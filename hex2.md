# hex2

## High level perspective

hex2 is the next logical extension of the hex1 programming language which by definition must support several additional features.

hex2 exists in 2 forms: Minimal self bootstrap or full standards compliant.

## Minimal self bootstrap requirements

### Long labels

The implementation of hex2 must support labels of atleast 42 characters in length.

The prefix character used : (0x3A) is not counted towards the length of the label.

The label is to be terminated by either a space (0x20), a tab (0x09), a line feed (0x0A) or carriage return (0x0D).

All other characters are to be considered part of the label.

### Multiple references

The implementation must support atleast 1 relative and 1 absolute reference to comply with the minimal self bootstrap requirements

## full standards compliant hex2

A full standards compliant hex2 must support everything required by the minimal self bootstrap requirements of hex2 along with several enhancements.

### Long labels

The implementation must now support labels of atleast 4,000 characters in length.

Labels gain the additional terminator: > (0x3E) which is now reserved for displacement calculations.

### Multiple references

The implementation must now support all absolute, relative and displacement references in this specification.
The sole exception is that of the architecture specific ? (0x3F) relative pointer and / (0x2F) absolute address references.

## Reference forms in this specification

### absolute

Absolute addresses are to be expressed in the architecture specific form required (as is specified in the hex1 specification).

They are the absolute address of the `:<label>` used and start at the base address specified by the architecture used or if so desired as specified by the user.

The prefixes formally specified are as follows:

* `$<label>` 2 byte address (0x24)
* `&<label>` 4 byte address (0x26)
* `/<label>` Architecture specific and not required to be supported (0x2F)

### relative

Absolute addresses are to be expressed in the architecture specific form required and calculated according to the architecture specific requirements (as is specified in the hex1 specification).

They are the relative number of byte (or words depending on architecture) from the reference to the label specified and of the size expressed by prefix.

The prefixes formally specified are as follows:

* `!<label>` 1 byte relative (0x21)
* `@<label>` 2 byte relative (0x40)
* `%<label>` 4 byte relative (0x25)
* `?<label>` Architecture specific and not required to be supported (0x3F)

## displacement

Displacements are the number of bytes between the addresses of the labels :foo and :bar and are to be expressed in the architecture specific form required (as is specified in the hex1 specification).

The prefixes formally specified are as follows:

* `!foo>bar` for 8 bit (0x21, 0x3E)
* `@foo>bar` for 16 bit (0x40, 0x3E)
* `%foo>bar` for 32 bit (0x25, 0x3E)
