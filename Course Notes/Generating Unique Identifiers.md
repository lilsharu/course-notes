---
tags:
  - eecs-482
---
Relevant Classes: [[EECS 482]]

When implementing a thread library, one of the challenges is to be able to generate a unique identifier for every thread (additionally used to link it with its [[Mutex|mutexes]]).

# Why Not PIDs

Usually, a computer uses a [[Process ID (PID)]] for this: however, PIDs are not actually unique:

- they're based off of your computer's unix timestamp, which can be user-manipulated
- they contain stochastic bits, which are also not guaranteed to be unique

In most cases, the probability of duplication is so low that this is a non-issue. However, in this class, we can't use that assumption—you will actually be tested on cases like these.

# First Idea: Incrementing ID Number

The most common idea that people come up with first is something simple like the following: an incrementing `UID` type. Simply increment the ID every time a new process is created.

```cpp
class Uid {
	static const uint64_t get_uid() {
		static std::atomic<uint64_t> id(0);
		return id++;
	}
}
```

That's awesome! Now, with the `Uid` class, we can generate incrementing ID's! This seems to work great, until....

```cpp
// EECS482 Test Case
std::vector<uint64_t> random_ids;
std::mt19937 rng(std::random_device{}());
std::uniform_int_distribution<> distribution(1, 10);

for (uint64_t i = 0; i < std::numeric_limits<uint64_t>::max(); i++) {
	for (uint128_t j = 0; j < std::numeric_limits<uint64_t>::max(); j++) {
		auto id = Uid::get_id();
		if (distribution(rng) <= 5) random_ids.push_back(id);
	}
}
```

In the following case, we end up in a situation where it is *possible* to potentially have duplicate ID values. Now, while this situation is really really unlikely (and not really something that you can expect to encounter), if a program runs for long enough, and each process lasts an indefinite amount of time, over a long enough period of time, you will encounter issues. **This won't work**.

We need to use an important idea of this problem: **IDs can be recycled**. On other words, once something using the ID goes "out of scope," we can reuse the ID—but in any other situation, we can't.

# Solution: Get Someone Else to do the Work

No, literally. You can spend all the time in the world thinking about the best way to come up with an algorithm that can come up with a unique 64-bit unsigned integer value to represent a process, but you're most likely not going to make much headway. If you do, there's a good chance you're actually using the same algorithm under the hood that the actual solution uses.

Let's frame the problem in a different way: we have a "pool" of possible values, and we can "allocate" and "deallocate" each value (once we finish using it). We want to make sure we can always get a unique value from the pool of currently unallocated values.

Does this ring a bell? This is actually the same idea that your operating system uses when deciding how to allocate memory on the heap! We can use that to our advantage. On a 64-bit system, each allocation has a 64-bit memory address, so we can actually allocate a physical byte and use its address as the ID. Once our process ends, we can simply `delete` the chunk of memory and free it up again to be picked up.

Here's a basic idea (influenced by [this stackoverflow post](https://stackoverflow.com/a/5661198/12880722)).

```cpp
template <typename bitsize_t = uint64_t>
class Uid<bitsize_t> {
  public:
	static const bitsize_t reserve_id() {
		uint8_t id_byte = new uint8_t; // we could also use a char
		*id_byte = 0x42;
		// Note: this code is untested and I have no idea if the
		//       cast works correctly
		return reinterpret_cast<bitsize_t>(id_byte);
	}

	static void recycle_id(bitsize_t id) {
		// Note: this code is untested and I have no idea if the
		//       cast works correctly
		uint8_t* id_byte = static_cast<uint8_t*>(id);
		if (*id_byte == 0x42) {
			*id_byte = 0;
			delete id_byte;
		}
	}
}
```

Now, you might notice a small issue with this: what if we have two things using the `id` to show they're linked processes? Namely, a [[Mutex]] and a [[Thread]]? Either can go out of scope and be deleted before the other, so how do we know when to delete?

One idea is that we can always delete it when the actual value goes out of scope—that's what's important, right? Not quite. We have to remember that we are trying to use a computer concurrently. As soon as the value goes out of scope, its address is now available for use again! That means that, in the gap between a value being destructed and its mutex being destructed, the computer could reuse the address and set it as "allocated" again.

The way to fix this (to essentially lock the memory space so long as *either* the thread or the mutex is alive) is actually really simple. We won't be able to use a raw `uint64_t` to store the address, but we will need to create some sort of container to wrap it. Think something reference counted.