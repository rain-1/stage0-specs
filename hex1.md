# hex1

## High level perspective

Hex1 is at its core an extension of hex0 and its input files inherit all of the properties of hex0, save where they are explicity overridded in this specification.

The primary advantage of hex1 over hex0 is the addition of labels and relative pointers which output the offset to the label based on the architecture specific requirements.

## Labels

Labels in hex1 are prefixed by the character : (0x3A) and the single character that follows, is its unique name.
This effectively allows 252 unique labels, but it is generally advised to limits ones label names to 0-9, a-z and A-Z.

## Pointers

Pointers are prefixed by the symbol that represents the size of the pointer.
Eg % (0x25),@ (0x40), or ! (0x21) depending on if the pointer is 32bits, 16bits or 8bits in length.

hex1 is only required to support 1 pointer size and per this specification that size should be the largest that can be reliably used for jumps and relative load/stores.

In the event the architecture does not support the standard size immediates (32, 16 or 8bits). The character ? (0x3F) is reserved for architecture specific immediates.
However support for such immediates are not required per the specification but exist as a tool to be leveraged by those dealing with badly engineered instruction sets.

## Architecture standards for Pointers

### x86

All pointers are 32bits long with little endian byte orientation but big endian nybble and bit orientation.
Therefore are prefixed with % (0x25).
The calculation for the relative displacement is the number of bytes from the end of the immediate to the destination.

### AMD64 (x86_64)

All pointers are 32bits long with little endian byte orientation but big endian nybble and bit orientation.
Therefore are prefixed with % (0x25).
The calculation for the relative displacement is the number of bytes from the end of the immediate to the destination.

### Knight

All pointers are 16bits long with big endian byte, nybble and bit orientation.
Therefor are prefixed with @ (0x40).
The calculation for the relative displacement is the number of bytes from the start of the instruction to the destination.

## Big and little endianness

Endianness refers to the sequential order in which bytes are arranged into larger numerical values.
More specificly are the bits or nybbles or bytes are ordered from the big end (most significant bit) or the little end (least significant bit).

### Examples

`%-2` would be converted to `FE FF FF FF` for x86 because x86 orders their bytes in little endian order but their bits/nybbles in big endian order.
`%-2` would be converted to `FF FF FF FE` for knight because knight orders their bits/nybbles/bytes in big endian order.

the number `%0x12345678` would convert to `78 56 34 12` for x86
the number `%0x12345678` would convert to `12 34 56 78` for knight.
