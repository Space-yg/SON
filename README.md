# SON
Simple Object Notation (SON) is an easier and more strict way of storing data

# Structure
## Key-value Pairs
The structure of SON is simple. You write the key = value. That's it.
```
key = "value"
```
You can have spaces in between the varaible name.
```
this is all one variable = "A value"
```
Variable names can be anything. Literally...
```
😁 = "This a an emoji as variable"
" = "This a quataion as varaible"
?!@#$%^&*:;"'`-+_()[]{} = "These are spacial characters as varaible"
123 = "Numbers can be variables too :D"
```
If you want to add an escape character, you can write the variable as if it is a string. See [String](#string).
```
"" = "This is an empty variable"
"\n" = "This is a variable with a new line"
b"bytes" = "This is a bytes variable"
r"\n" = "This is a variable named "\n". Not a new line"
c"a" = "This is a variable whose key is one character"
```

## Indentaion
The beginning indentation is very important. All variables must have the same indentation unless it is a [Dictionary](#dictionary).

You can indent with a space or a tab. They are both equal.

For example, the following structure is **invalid** because they do not have the same indentation:
```
key 1 = "This is OK" // ✅
  key 2 = "This is not OK" // ❌
```
the following structure is **valid** because they have the same indentation:
```
  key 1 = "This is OK" // ✅
  key 2 = "This is also OK" // ✅
```
the following structure is **valid**, since key 2's spacing is part of the variable name:
```
key 1 = "This is OK" // ✅
"  key 2" = "This is also OK" // ✅
```

## Comments
You can add comments with a double forward slash.
```
// This is a comment
string = "and this is a string" // This is also another comment
```

# Data types
Here is the list of the data types:
- [String](#string)
- [Boolean](#boolean)
- [Number](#number)
- [Array](#array)
- [Dictionary](#dictionary)
- [Regex](#regex)
- [Timestamp](#timestamp)
- [Other](#other)

## String
There are 4 types of strings: [string](!string-1), [raw](!row), [byte](!byte), and [char](!char)

### String
String is formatted as the following:


<picture>
    <source alt="String Flowchart" srcset="./images/string-flowchart-dark.drawio.png"  media="(prefers-color-scheme: dark)">
    <img alt="String Flowchart" src="./images/string-flowchart-light.drawio.svg">
</picture>


You can use double " or single ' quotation. There is no difference.

You can add a backslash \ by just typing it. If you don't want to escape a character but add a backslash, add \\

If you want to add double " or single ' quotation in a double " or single ' quotated string, respectively, just write it :D. The parser will just check if the beginning and end of the string have the same quotations.


Examples:
```
string 1 = "this is a string"
string 2 = "here is a new line \n"
string 3 = "here is the characters \ then n \\n"
string 4 = "here is a quataion " inside the string"
string 5 = 'here is a quataion ' inside the string'
```

### Raw
Raw strings are like normal strings, but you cannot use escape characters.

To write a raw string, use double " or single ' quotations at the start and the end of the string. Then add an `r` before the string

Example:
```
raw 1 = r"this is a raw string"
raw 2 = r"this is a literal \n, not a new line"
```

### Byte
Byte strings have the same structure as normal strings, except before the first quotation, there is a `b`.
```
byte 1 = b"this is a byte string"
byte 2 = b"you can escape characters here \n <- this is a new line"
```
Byte strings will be converted to bytes upon parsing the file.

### Char
Char strings are just one-character strings. That's it...

To make a char string, add a `c` before the string.
```
empty char = c""
char = c"a"
```
The following is an invalid char because it is more than 1 character:
```
invalid char = c"ab" // ❌
```

### Combine String Types
You can combine raw string with byte string or char string with byte string. You do that by just adding both letters that correspond to each.
```
raw byte = rb"This is a raw byte string. No escape characters \n. The string will be converted to bytes"
byte row = br"This is also a raw byte string."
char byte = cb"a"
byte char = bc"a" // This is the same as char byte
```

# Boolean
Just true or false...
```
bool 1 = true
bool 2 = false
```

# Number
<!-- @TODO Add a graph here to show the number structure -->
Numbers can be 2 things, an integer or a float.
```
num 1 = 123 // integer
num 2 = 123.456 // float
num 3 = .123 // float
num 3 = 123.0 // float
```
They can be positive or negative.
```
positive = 123
negative = -123
```

## Hex, Octal, and Binary
You can write a hexadecimal, octal decimal, or a binary number by adding a prefix of `0x`, `0o`, or `0b`, respectively.
```
hex = 0x123
oct = 0o123
binary = 0b101
```
These numbers will be converted to normal integers upon parsing.

You can even remove the `0` and just write `x`, `o`, or `b`.
```
hex = x123
oct = o123
binary = b101
```
They can be capital too.
```
hex 1 = 0X123
oct 1 = 0O123
binary 1 = 0B101
hex 2 = X123
oct 2 = O123
binary 2 = B101
```

## Scientific Notation
You can add scientific notation by adding `e` and then an integer.
```
num 1 = 12e3 // This will be evaluated as 12000
num 2 = 1.2e3 // This will be evaluated as 1200
num 3 = .12e3 // This will be evaluated as 120
```
You can add + or - after the `e`.
```
num 1 = 12e+3 // This will be evaluated as 12000
num 2 = 1.2e-3 // This will be evaluated as 0.0012
num 3 = .12e-3 // This will be evaluated as 0.00012
```
You **cannot** combine hex, octal, or binary with `e`.
```
num = 0x123e3 // This is invalid ❌
```

## Integers
You can specify if a number is an integer by adding a suffix `i`
```
int = 123i
```

### Specify Bits
You can also specify how many bits should this integer take up.
```
int8 = 123i8
int16 = 123i16
```
If no amount of bits is specified, the integer can be as big or small as possible.

The number of bits **must** be a factor of 8.
```
int = 123i5 // This is invalid ❌
```

### Integers with Scientific Notation
You can combine integers with scientific notation.
```
int 1 = 12e3i
int 1 = 1.2e3i8 // This is valid ✅ since it will be computed to be 1200
```

### Integers with Hex, Octal, or binary
You can combine integers with hex, octal, and binary.
```
int hex = 0x123i
```

### Unsigned Integers
You can make integers unsigned by using the suffix `ui`.
```
unsigned int = 123ui
```
You can add the number of bits, use scientific notation, and combine with hex, octal, or binary.

## Floats
You can also specify if a number is a float using the suffix `f`.
```
float 1 = 123f
float 2 = .123f
```

### Specify Bits
Just like integer, you can specify the number of bits by writing it after the `f`. It **must** be a factor of 16.
```
float16 = 123f16
float32 = 123f32
float48 = 123f48
float64 = 123f64
```
If the amount of bits is not specified, the parser will use the smallest amount of bits that can fit the number.

### Floats with Scientific Notation
You can combine floats with scientific notation.
```
float 1 = 12e3f
float 1 = 1.2e-3f16
```

### Floats with Hex, Octal, or binary
You can combine floats with hex, octal, and binary. For hex, You **must** specify the number of bits. It will be computed as the IEEE 754 standard.
```
float hex 1 = 0x123f16 // This is 4.07778e-43
float hex 2 = 0x7F800000f16 // This is inf
float hex 3 = 0xff800000f16 // This is -inf
```

### No Unsigned Float
There is **no** unsigned float.
```
unsigned float = 123uf // This is invalid ❌
```

## Special Values
You can add infinity and NaN.
```
infinity 1 = inf
infinity 2 = -inf
infinity 3 = infinity
infinity 4 = -infinity
not a number 1 = nan
not a number 2 = NaN
```

# Array
