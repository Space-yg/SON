<!-- Hello there whoever is seeing this! -->
<!--
TODO
- Generics:
```
Snowflake = string | integer
id 1 = <Snowflake> 1
id 2 = <Snowflake> "123"

collection<T> = array<T> | set<T>
array of integers = <arr<integer>> [1, 2, 3]
```
- Make a file for each data type.
- Make a valid.son and invalid.son files for each data type. This will include the valid and invalid values for each data type.
-
-->

# SON
Simple Object Notation (SON) is an easier and more strict way of storing data.

What's the purpose of SON? What makes it unique?
1. Allocate the right amount of memory. No more, no less. ✅
2. Type-check your data before using it. ✅
3. Process the right type for each key. ✅
4. A variety of data types. ✅

Table of contents
- [Structure](#structure)
  - [Key-value Pairs](#key-value-pairs)
  - [Indentaion](#indentaion)
  - [Comments](#comments)
- [Data Types](#data-types)
  - [String](#string)
  - [Boolean](#boolean)
  - [Number](#number)
  - [Array](#array)
  - [Set](#set)
  - [Dictionary](#dictionary)
  - [Regex](#regex)
  - [URL](#url)
  - [Timestamp](#timestamp)
  - [Other](#other)

# Structure
## Key-value Pairs
The structure of SON is simple. You write `key = value`. That's it.
```
key = "value"
```

You can have spaces in between the variable names.
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
The beginning indentation is very important. All variables must have the same indentation unless it is a [Array](#array) or [Set](#set).

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

# Data Types
Here is the list of the data types:
- [String](#string)
  - [Normal String](#normal-string)
  - [Escape Characters](#escape-characters)
  - [Raw](#raw)
  - [Byte](#byte)
  - [Character](#character)
  - [Combine String Types](#combine-string-types)
- [Boolean](#boolean)
- [Number](#number)
  - [Hex, Octal, and Binary](#hex-octal-and-binary)
  - [Scientific Notation](#scientific-notation)
  - [Integers](#integers)
    - [Specify Integer Bits](#specify-integer-bits)
    - [Integers with Scientific Notation](#integers-with-scientific-notation)
    - [Integers with Hex, Octal, or Binary](#integers-with-hex-octal-or-binary)
    - [Unsigned Integers](#unsigned-integers)
  - [Floats](#floats)
    - [Specify Float Bits](#specify-float-bits)
    - [Floats with Scientific Notation](#floats-with-scientific-notation)
    - [Floats with Hex, Octal, or Binary](#floats-with-hex-octal-or-binary)
    - [No Unsigned Float](#no-unsigned-float)
  - [Special Values](#special-values)
- [Array](#array)
- [Set](#set)
- [Dictionary](#dictionary)
- [Regex](#regex)
- [URL](#url)
- [Timestamp](#timestamp)
- [Other](#other)

# String
- [Normal String](#normal-string)
- [Escape Characters](#escape-characters)
- [Raw](#raw)
- [Byte](#byte)
- [Character](#character)
- [Combine String Types](#combine-string-types)

There are 4 types of strings: [normal string](!normal-string), [raw](!row), [byte](!byte), and [char](!char)

## Normal String
A normal string is structured as follows:


<picture>
    <source alt="String Flowchart" srcset="./images/string-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="String Flowchart" src="./images/string-flowchart-light.drawio.svg">
</picture>


You can use a double `"` or single `'` quotation. There is no difference.
```
string 1 = "this is a string"
string 2 = 'this is also a string'
```

## Escape Characters
Here is the structure of the escape characters:


<picture>
    <source alt="Escape Characters Flowchart" srcset="./images/escape-characters-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="Escape Characters Flowchart" src="./images/escape-characters-flowchart-light.drawio.svg">
</picture>


If you want to add a double `"` or single `'` quotation in a double `"` or single `'` quoted string, respectively, just write it :D. The parser will just check if the beginning and end of the string have the same quotations.
```
string 1 = "here is a newline \n"
string 2 = "here is NOT a newline \\n but just the characters \ and n"
string 3 = "here is a quotaion " inside the string"
string 4 = 'here is a quotaion ' inside the string'
```

## Raw
Raw strings are like normal strings, but you cannot use escape characters.

To write a raw string, add an `r` before the string
```
raw 1 = r"this is a raw string"
raw 2 = r"this is a literal \n, not a new line"
```

## Byte
Byte strings have the same structure as normal strings, except before the first quotation, there is a `b`.
```
byte 1 = b"this is a byte string"
byte 2 = b"you can escape characters here \n <- this is a new line"
```
Byte strings will be converted to bytes upon parsing.

## Character
Character strings are just one-character strings. That's it...

To make a char string, add a `c` before the string.
```
empty char = c""
char = c"a"
```

The following is an invalid character because it is more than 1 character:
```
invalid char = c"ab" // ❌
```

You can have escape characters inside a character string.
```
escape character = c"\n" // This is valid ✅
```

## Combine String Types
You can combine raw string with byte string or char string with byte string. You do that by just adding both letters that correspond to each other.
```
raw byte = rb"This is a raw byte string. No escape characters \n. The string will be converted to bytes"
byte raw = br"This is also a raw byte string."
char byte = cb"a"
byte char = bc"a" // This is the same as char byte
raw char = rc"\" // This is valid because raw strings do not have escape characters
char raw = cr"\" // This is the same as raw char
```

# Boolean
Just true or false...
```
bool 1 = true
bool 2 = false
```

# Number
- [Hex, Octal, and Binary](#hex-octal-and-binary)
- [Scientific Notation](#scientific-notation)
- [Integers](#integers)
  - [Specify Integer Bits](#specify-integer-bits)
  - [Integers with Scientific Notation](#integers-with-scientific-notation)
  - [Integers with Hex, Octal, or Binary](#integers-with-hex-octal-or-binary)
  - [Unsigned Integers](#unsigned-integers)
- [Floats](#floats)
  - [Specify Float Bits](#specify-float-bits)
  - [Floats with Scientific Notation](#floats-with-scientific-notation)
  - [Floats with Hex, Octal, or Binary](#floats-with-hex-octal-or-binary)
  - [No Unsigned Float](#no-unsigned-float)
- [Special Values](#special-values)

A number is structured as follows:


<picture>
    <source alt="Number Flowchart" srcset="./images/number-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="Number Flowchart" src="./images/number-flowchart-light.drawio.svg">
</picture>


**Note: `number` is not a type. `integer` and `float` are the types.**

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
You can use an uppercase `E`.
```
num 1 = 12E3
num 2 = 1.2E3
num 3 = .12E3
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
You **cannot** use float after the scientific notation.
```
num = 12e3.4 // This is invalid ❌
```

## Integers
- [Specify Integer Bits](#specify-integer-bits)
- [Integers with Scientific Notation](#integers-with-scientific-notation)
- [Integers with Hex, Octal, or Binary](#integers-with-hex-octal-or-binary)
- [Unsigned Integers](#unsigned-integers)

You can specify if a number is an integer by adding a suffix `i`.
```
int = 123i
```

### Specify Integer Bits
You can also specify how many bits should this integer take up.
```
int8 = 123i8
int16 = 123i16
```
If no amount of bits is specified, the integer can be as big or small as possible.

The number of bits **must** be a multiple of 8.
```
int = 123i5 // This is invalid ❌
```

### Integers with Scientific Notation
You can combine integers with scientific notation.
```
int 1 = 12e3i
int 1 = 1.2e3i16 // This is valid ✅ since it will be computed to be 1200
```

### Integers with Hex, Octal, or Binary
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
- [Specify Float Bits](#specify-float-bits)
- [Floats with Scientific Notation](#floats-with-scientific-notation)
- [Floats with Hex, Octal, or Binary](#floats-with-hex-octal-or-binary)
- [No Unsigned Float](#no-unsigned-float)

You can also specify if a number is a float using the suffix `f`.
```
float 1 = 123f
float 2 = .123f
```

### Specify Float Bits
Just like an integer, you can specify the number of bits by writing it after the `f`. It **must** be a multiple of 16.
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

### Floats with Hex, Octal, or Binary
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
An array is structured as follows:


<picture>
    <source alt="Array Flowchart" srcset="./images/array-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="Array Flowchart" src="./images/array-flowchart-light.drawio.svg">
</picture>


You make an array using `= []`.
```
array 1 = [1, 2, 3]
array 2 = ["value 1", "value 2", "value 3"]
```

You can write the array on multiple lines.
```
array = [
  1,
  2,
  3
]
```

If the elements are on multiple lines, you do not need to have a `,` at the end of each element.
```
array = [
  1
  2
  3
]
```

You can make a mix of new lines and `,`.
```
array = [
  1, 2
  3
  4,
  5, 6, 7,
  8
]
```

Elements can have different indentations.
```
array = [
  1
    2
3
]
```

Arrays can contain different types.
```
array = [
  "string"
  123
  true
]
```

You can have arrays in arrays.
```
array = [
  [
    "This is another array"
  ]
]
```

You can have dictionaries in arrays.
```
array = [
  :
    key = "this is a dictionary"
]
```

## Array of a Type
You can specify the type of the elements in an array.
```
array = <array<string>> [
  "Hi"
  "This"
  "is"
  "an"
  "array"
  "of"
  "type"
  "string"
]
```
The above will be computed as follows:
```cpp
// This is an example in C++. It can be made with any programming language.
string arr[8] = {
  "Hi",
  "This",
  "is",
  "an",
  "array",
  "of",
  "type",
  "string"
};
```

For more information, see [Collection of a Type](#collection-of-a-type).

# Set
A set is structured as follows:


<picture>
    <source alt="Set Flowchart" srcset="./images/set-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="Set Flowchart" src="./images/set-flowchart-light.drawio.svg">
</picture>


You can make a set using `= {}`
```
set 1 = {1, 2, 3}
set 2 = {
  1,
  2,
  3
}
set 3 = {
  1
  2
  3
}
set 4 = {
  1
2
    3
}
set 5 = {
  1, 2
  3
}
```
All sets are valid set syntaxes and all of them are the same.

A set cannot contain duplicates:
```
set duplicates = {1, 2, 3, 1} // This is invalid ❌
```

A set can be empty.
```
empty set = {}
```

A set can have any type inside it.
```
set string = {"value 1", "value 2", "value 3"}
set directory = {
  directory 1:
    key = "value"
  directory 2:
    key 1 = "value"
    key 2 = "value"
}
set set = {{}, {1}, {2}, {1, 2}}
```

A set can have multiple types inside of it.
```
set multiple types = {
  "string", 1
  directory:
    key = "value"
  {2, 5}
}
```

You can specify the type of the set by doing the following:
```
set string = string{"value 1", "value 2", "value 3"}
set array = array{["value 1", "value 2"], [1, 2], [[3, 4], "value 6"]}
set set = set{{1}, {2}, {{3}, 4}}
```

You can specify one or more types for a set in a set.
```
set of set of integer = set<integer>{{1}, {2}, {1, 2}, {}} // Empty sets are valid for any set of any type
set of set of string = set<string>{{"value 1", "value 2"}, {"value 3"}}
set of array of integer = array<integer>{[1, 2], [3], [1], [2, 1]}
```

# Dictionary
A dictionary is structured as follows:


<picture>
    <source alt="Dictionary Flowchart" srcset="./images/dictionary-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="Dictionary Flowchart" src="./images/dictionary-flowchart-light.drawio.svg">
</picture>


You make a dictionary using a `:`
```
dictionary:
  key = "value"
```

You **must** indent all the key-value pairs inside the dictionary.

You can nest dictionaries inside of each other.
```
nested dictionary:
  key 1 = "value"
  key 2 = "value"
  dictionary:
    another key = "value"
  key 3 = "value"
```

You can make an empty dictionary as follows:
```
empty dictionary:
another empty dictionary:
```

# Regex
Regular Expressions can be written in the following pattern: `flavors/pattern/flags`.
```
regex 1 = /abc/ // Normal pattern
regex 2 = /abc/i // Case insensitive flag
regex 3 = py/abc/i // Only for python
regex 4 = py|js/abc/i // Only for python and javascript
```
`regex 1` and `regex 2` have a flavor of any. This means that it can be used in any programming language, but not all programming languages support the same patterns and flags.

## Different Regex Flavor
If the programming language you are using is a different one from the flavor of a regex, you **must** add a class to manage that regex. Here is an example in Python:
```py
class OtherRegexFlavor:
    """A class for a regex that is not a python regex."""
    def __init__(self, full: str, flavors: list[str], pattern: str, flags: str) -> None:
        self.full = full
        self.regex = f"/{pattern}/{flags}"
        self.flavors = flavors
        self.pattern = pattern
        self.flags = flags
```
Whenever the parser finds a regex with a flavor that is not `py`, `python`, or no flavor, a new `OtherRegexFlavor` object gets created and passed as the value.

# URL
You can represent a URL with just the link.
```
full url = https://www.google.com
url = www.google.com
url path = www.google.com/path
url params = www.google.com?search=cats
relative path = ./path
```
When parsing a URL, you **must** use the programming language's standard library for parsing URLs.

Relative paths **must** start with `./`.
```
relative path = path/another_path // This is invalid ❌
```

You **can** put a URL in a string. This will prevent the program from making the URLs into objects which could make the program faster.

# Timestamp
There are many different ways to write timestamps. The format follows some of the [ISO 8601](https://en.m.wikipedia.org/wiki/ISO_8601) standards.

All numbers must be zero-padded. For example, the month of March should not be written as `3` but as `03` instead.

All values must be valid date or time. For example, you cannot have day 31 in February.

## Timestamp as Number
**Disclaimer: This format is not part of ISO 8601.** It is just a format to make things easier.

You can write an integer or float number and add the suffix `t`. This will indicate that this number is a timestamp.
```
timestamp = 123t
```
`t` **must** be at the very end, even after the integer and float identifiers `i` and `f`, respectively.

## Date
Here are the formats for the date:
```
DYYYY
YYYY-DDD
DYYYYDDD
YYYY-Wwww
YYYYWwww
YYYY-Wwww-D
YYYYWwwwD
YYYY-MM // No YYYYMM ❌
YYYY-MM-DD
DYYYYMMDD
```
The prefix `D` is **not** in the ISO 8601 standard, but it is used here to differentiate between normal numbers and dates. You can add the prefix `D` to any date.

### Terms
#### YYYY
The year from `0000` to `9999`.

#### MM
The month from `01` to `12`.

#### Www
The week from `W01` to `W53`.

#### DDD
The day from `001` to `365` or `366` if it is a leap year.

#### DD
The day from `01` to `31` depending on the month.

#### D (not the prefix)
The day from `1` to `7`. Monday is day `1`. Yeah, it's annoying...

## Time
You can write time in multiple formats.
```
Thh
Thhmm
Thhmmss
Thhmmss.ssss
hh:mm
hh:mm:ss
hh:mm:ss.ssss
```
You can add a `T` at the beginning of each one, but `T` is a **must** for the ones that have it.

### Terms
#### T
Time.

#### hh
The hour from `00` to `24`.

#### mm
The minute from `00` to `60`.

#### ss
The second from `00` to `60`.

#### .ssss
The milliseconds. A dot `.` or a comma `,` is allowed for the seconds.

## Time Zone
Here are the following formats to specify the timezone:
```
<time>Z
<time>±hh
<time>±hhmm
<time>±hh:mm
```

### Terms
#### \<time>
A time from [Time](#time)

#### Z
The time is UTC.

#### ±hh, ±hhmm, and ±hh:mm
The time plus or minus UTC. Minus sign `−` (U+2212) and hyphen-minus sign `-` (U+002D) can be used to indicate negativity.

## Date and Time
You can combine the date with the time in the format `<date>T<time>`.
```
date and time = 2006-1-28T12:05:30.1234
```

## Duration
The following can be used to format a duration time:
```
PnY
PnM
PnW
PnD
PTnH
PTnM
PTnS
PnYnMnDTnHnMnS // Can use some of the durations but must be in this order
P<date>T<Ttime>
```
You can combine the date and the time however you want, but it **must** follow the format `P<date>T<Ttime>`.

### Terms
#### P
Period. It is used to specify that this date is a duration.

#### Y, M, W, D, T, H, M, and S
These are constant characters.
##### Y
Year.
##### M
Month.
##### W
Week.
##### T
Time.
##### D
Day.
##### H (after T)
Hour.
##### M (after T)
Minutes.
##### S
Seconds.

#### n
Any number.

#### \<date>
A [Date](#date).

#### \<time>
A [Time](#time).

## Time Intervals
The following formats can be used to represent time intervals:
```
<start>/<end>
<start>/<duration>
<duration>/<end>
<duration>
```

### Terms
#### \<start> and \<end>
These are [Time](#time), [Date](#date), or [Date and Time](#date-and-time).

#### \<duration>
This is a [Duration](#duartion).

## Repeating Intervals
The following formats can be used to represent repeating intervals:
```
Rn/<interval>
R/<interval>
```

### Terms
#### R
Repeating.

#### n
Any number.

#### \<interval>
A [Time Interval](#time-interval).

# Other
## Null
nothing...
```
key = null
```

# Type Checking
You can specify the types that are valid inside for any value.
```
number = <integer> 2
string = <string> "hi"
array of anything = <array> [1, "hi", true]
array of strings = <array<string>> ["value 1", "value 2", "value 3"]
set of integers = <set<integer>> {1, 2, 3}
```

You can nest types with other types as follows:
```
array of arrays of integers = <array<set<integer>>> [{1, 2}, {2, 1}, {1}, {1}, {}] // Empty set is a valid set of integers
set of array of regex = <set<array<regex>>> {/regex 1/, /regex 2/i, py/regex 3/m}
```

You can use `|` to specify more than one type.
```
array of strings or integers = <array<string | integer>> [1, "value 2", 3, "value 4"]
```

You can use `&` to specify both types at the same time. This can be used on some of the types.
```
raw byte string = <string<raw & byte>> rb"This is a raw byte string"
```

## String Types
You can specify what type of string you want to check for.

### Any String Type
Denoted as `<string>`.
```
string = <string> "This is a string"
byte string = <string> b"This is a byte string"
```

### String Raw Type
Denoted as `<string<raw>>` or `<string<r>>`.
```
raw string = <string<raw>> r"This \is a \raw \string" // This is valid ✅
normal string = <string<r>> "This is a normal string" // This is valid ✅
not a raw string = <string<raw>> "This is not \n a raw string" // This will give an error because there is an escape character ❌
```

### String Character Type
Denoted as `<string<character>>`, `<string<char>>`, or `<string<c>>`.
```
character string = <string<character>> c"a"
empty string = <string<char>> "" // This is valid ✅
normal string = <string<c>> "b" // This is valid ✅
escape string = <string<c>> "\n" // This is valid ✅
invalid string = <string<character>> "ab" // This is not valid ❌
```

### String Byte Type
Denoted as `<string<byte>>` or `<string<b>>`.
```
byte string = <string<byte>> b"This is a byte string"
byte string = <string<byte>> "This is a normal string" //  This is not valid ❌
```

### Mix String Types
You can mix string types by using `&`.
```
byte raw string = <string<byte & raw>> br"This is a byte raw string"
char raw string = <string<char & r>> rc"\"
char byte string = <string<c & b>> cb"a"
```

## Integer Types
You can specify what type of integer you want to check for.

### Integer Type
Denoted as `<integer>` or `<int>`.
```
integer = <integer> 2
int = <int> 5
```

The rest of the examples will use `<integer>`, but `<int>` works for all of them.

### Integer Bits Type
Denoted as `<integer<8>>`, `<integer<16>>`, `<integer<24>>`, etc.
```
int 1 = <integer<16>> 123
int 2 = <integer<16>> 123i16
int 3 = <integer<16>> 123i8 // This is invalid ❌
int 3 = <integer<16>> 123.0 // This is invalid ❌
int 3 = <integer<8 & 16>> 123 // This is invalid ❌
```

What is the difference between `<integer<16>>` and `i16`?
There is no difference. Both of them will check the value of the integer and will give an error based on it. `<integer<16>>` is mainly used when you want to nest it in other types such as [arrays](#array-types) or [sets](#set-types).

*To be continued*
