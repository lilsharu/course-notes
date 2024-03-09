---
tags:
  - eecs-370
---
Related Classes: [[EECS 370]]

When linking [[LC2K]] [[Object Files]], there are a few situations you can encounter.

# What to Link

Linking simply involves a) checking global labels and b) making any modifications necessary as marked by the [[Object Files#Relocation Table|Relocation Table]].

There are four types of values that your relocation table can link: Text -> Text, Data -> Text, Text -> Data, and Data -> Data.

## Linking to Text

When you're linking to something in the Text Section, the process followed is simple:

- Since all text is grouped together, calculate how many lines from the beginning were added before the file that you're linking too. Then, add the value from the symbol table to this calculation (if relevant)
- Add this calculated value to the "immediate" value of the instruction.

## Linking to Data

When you're linking from to something in Data, the process is also fairly simple, but has a few caveats.

- Since data comes after all text, take the total number of lines from the beginning that were added before the data section that you were referring to.
- Here is the caveat: if the label is a global label, add the symbol table offset to this line number and **set** the "immediate" to this newly calculated value.
- If it is local, we can simply add the additional lines offset to our `sw/lw` functions (and the offset from the data section should already be accounted for). 
	- **You just need to subtract the number of lines in the text section of the relevant file to avoid double counting**.