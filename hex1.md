# hex1

Extension of hex0.

* Adds single letter labels.
* Adds pointer references of one fixed size.

# labels

```
:l
```

# pointers

Pointers are relative addresses.

* On x86 `%l` is used, the size is 32 bit.
* On x64 `%l` is used, the size is 32 bit.
* On KNIGHT `@l` is used, the size is 16 bit.

knight calculates the displacement as the number of bytes from the start of the instruction to the destination.

x86 calculates the displacement as the number of bytes from the end of the immediate to the destination (which could be in the middle of the instruction in the event of a double immediate instruction, but usually it means from the end of the instruction for x86 and x86_64).


