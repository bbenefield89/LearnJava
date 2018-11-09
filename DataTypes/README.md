#Java Data Types

##Type
Boolean

###Summary
boolean data types reprsent one of two values which can be either
true or false. Boolean types only take up 1bit of memory each.
Boolean types can also be represented as a 1 (true) or 0 (false)


##Type
Byte

###Summary
The "byte" data type is an "8bit signed twos complement integer" that can hold
a range of integer values from (-2^7) to (2^7 - 1) or (-128 to 127). If the
byte data type were unsigned it would then hold (0) to (2^8 - 1) or (0) to
(255).  
That's a lot of technical words so lets break it down.

- "8bit": The integer can only be made up of eight bits (the numbers
representing each slot in binary), e.g. 0000 0000 which would return 0.

- "signed": When an integer is "signed" that means it can hold negative values
while an "unsigned" integer can only hold positive values. Signed and unsigned
integers will still hold the same RANGE of values but the range has been
adjusted to fit the MIN and MAX value of that data type.

- "twos complement": The concept of two's complement can be difficult to
explain so I'll just leave a helpful link from stack overflow
https://stackoverflow.com/questions/1049722/what-is-2s-complement
https://stackoverflow.com/questions/1125304/why-prefer-twos-complement-over-sign-and-magnitude-for-signed-numbers


##Type
Short

###Summary
The short data type is a 16bit signed twos complement integer that is able to
hold a range of values from "-32,768 to 32,767". Use short type when it's
critical you save as much memory as possible


##Type
Int

###Summary
The int data type is a 32bit signed twos complementary integer which is capable
of holding (-2^31) to (2^31 - 1). Since Java 8 we can also use the int data
type to hold unsigned integers which have a range from (0) to (2^32 - 1).


##Type
Long

###Summary
The long data type is a 64bit signed twos complement integer which is capable 
of holding (-2^63) to (2^63 - 1) and since Java 8 the long type can also be
used to store unsigned integers which can hold (0) to (2^64 - 1) and must use
an "L" as a suffix


##Type
Float/Double

###Summary
floats and doubles are pretty similar. Floats are a single-precision 32bit IEEE
754 floating point and should use an "f" as a suffix while doubles are
double-precision 32bit IEEE 754 floating point. Use floats when you need to
save data but doubles are what you will typically come accross in "the wild".
https://en.wikipedia.org/wiki/IEEE_754