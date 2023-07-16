# SON
Simple Object Notation (SON) is an easier and more strict way of storing data.

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
- [URL](#url)
- [Timestamp](#timestamp)
- [Other](#other)

# String
There are 4 types of strings: [normal string](!normal-string), [raw](!row), [byte](!byte), and [char](!char)

## Normal String
A normal string is structured as the following:


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

## Char
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

## Combine String Types
You can combine raw string with byte string or char string with byte string. You do that by just adding both letters that correspond to each.
```
raw byte = rb"This is a raw byte string. No escape characters \n. The string will be converted to bytes"
byte raw = br"This is also a raw byte string."
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
Here is the structure of a number:


<picture>
    <source alt="Number Flowchart" srcset="./images/number-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="Number Flowchart" src="./images/number-flowchart-light.drawio.svg">
</picture>


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
Here is how arrays are structured:


<picture>
    <source alt="Array Flowchart" srcset="./images/array-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="Array Flowchart" src="./images/array-flowchart-light.drawio.svg">
</picture>


Arrays are simple to write. There are 2 ways to write arrays.

## Single Element Araay
If an array has one element, you can write it like this `[value]`
```
array 1 = ["value"]
array 2 = [123]
```

## Multi-Element Array
If an array has more than one element, you will write the following syntax:
```
array = [
  value 1
  value 2
  value 3
  ...
]
```
You **must** have each value on a separate line. You **must** have all values have the same indentation.

The following is an **invalid** array because one of the elements has a different indentation than the others.
```
array = [
  "value" // This is OK ✅
  "value" // This is OK ✅
"value" // This is not OK ❌
]
```

The following array is **valid** because all elements have the same indentation.
```
array = [
"value"
"value"
"value"
]
```

## Same Element Type Array
If all of the elements in an array have the same type, then compute this array to be only this type with the same length.
```
array = [
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
The above will be computed as the following.
```cpp
// This is an example in C++. It can be made with any programming language.
string array[8] = {
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

## Different Element Type Array
Arrays can contain different values.
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
    "this is another array"
  ]
]
```

You can have dictionaries in arrays.
```
array = [
  {
    key = "this is another dictionary"
  }
]
```

# Dictionary
Here is the structure of a dictionary:


<picture>
    <source alt="Dictionary Flowchart" srcset="./images/dictionary-flowchart-dark.drawio.svg"  media="(prefers-color-scheme: dark)">
    <img alt="Dictionary Flowchart" src="./images/dictionary-flowchart-light.drawio.svg">
</picture>


There are 2 ways to make a dictionary: using a `:` or `= {}`
```
dictionary 1:
  key = "value"
dictionary 2 = {
  key = "value"
}
```
In the example, `dictionary 1` and `dictionary 2` are the same dictionary.

When using `:` to make a dictionary, you **must** indent all the key-value pairs inside.

You can stack dictionaries inside of each other.
```
dictionary:
  key 1 = "value"
  key 2 = "value"
  dictionary:
    another key = "value"
  key 3 = "value"
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
The minutes from `00` to `60`.

#### ss
The seconds from `00` to `60`.

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
