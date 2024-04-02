---
tags:
  - eecs-370
---
Related Courses: [[EECS 370]]

Object files are an intermediary between assembly and machine code that allows you to split up code into multiple files. It essentially allows you to declare a label in one file and use it in another, and have the assembler and linker handle the rest of the process of connecting these defragmented pieces.

## What's in an Object File

Since an object file contains everything we'll need to be able to turn it into machine code, there are a few required sections that are able to describe everything in the program.

We'll describe these using [[LC2K]], but the concept is the same regardless.

### Header

The header is a very simple part of the object file that describes the size each section within the rest of the file.

LC2K Example
```
5 4 3 2
```

The above header section is saying that theres five lines of text (instructions) in our object file, four lines of data, three items in the symbol table, and two items in the relocation table. 
### Text 

This includes all the machine code you were able to generate—with some defaults for undefined labels.

### Data

This includes all globals, static locals, and all the data that `.fill` directive is used to describe. Usually, this does not include uninitialized data values, but for LC2K we use the simplifying assumption that all data will go here.

### Symbol Table

This is going to list all the labels (and all of the function names and variable names) that are visible outside this file. All globals will be listed here, and depending on who you ask, `static` variables would also go here.

### Relocation Table

This is the list of all instructions and data declarations that are going to have to be updated at during [[Linking]] (because things will move around in memory). 