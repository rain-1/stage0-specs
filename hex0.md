# hex0

## High level perspective

hex0 is the most minimal assembler that is reasonable for a given architecture.

It primarily assembles bytes out of nybbles in the form of hex characters [0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F,a,b,c,d,e,f] hence the name.
For architectures where nybble alignment is either impossible or complicates basic work, 2 alternative forms also exist as compatibles: oct0 and bit0.

oct0 assembles bytes out of octets in the form of octal characters [0,1,2,3,4,5,6,7] and requires a triplet eg 077 to create a byte.

bit0 assembles bytes out of individual bits and is only used on the most insane and hostile bootstrapping environments. Limiting to only binary characters [0,1] and requiring sequences 8 long.

## User friendliness extensions

In order to simplify the task of keeping track of what you are doing and giving the programmer the flexibility required hex0 supports both # (0x23) and ; (0x3B) line comments which terminates when a line feed character (0x0A) is read.

To avoid the eternal platform specific end of line character question, all implementations are to convert the carriage return character (0x0D) to the line feed character (0x0A) prior to processing.
Should your platform use some character other than line feed or carriage return when the keyboard return/enter key is pressed, the implementation is required to convert said character to line feed and stored form is to utilize the line feed character (0x0A).

To avoid any confusion or complication, hex0 treats upper case and lower case letters identically, eg F == f, E == e, etc.

Any character that doesn't match the allowed input character are simply ignored, save for EOT (0x04) and EOF (-1) which simply drop any outstanding nybbles and terminate the processing of the input.
