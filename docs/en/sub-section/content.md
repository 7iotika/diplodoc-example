# Sub-Section with content 

This is an example page for demonstation how sub-sections can be organized. 
More details about subsections inclusion can be found [here](https://diplodoc.com/docs/en/project/toc)

Language:enum type cast
Status: Released

Contents
1,	Enum type cast
  1.	Explicit type cast
  1.	enum <-> str type cast
  1.	enum <-> int type cast
  1.	enum E1 -> enum E2
1.	Implicit type cast
Enum type cast
Explicit and implicit type casts are supported for enum with several restrictions. Explicit/implicit type cast may be allowed for read access and always forbidden for write access.

Explicit type cast
Explicit type cast is made with the help of operator as.

enum <-> str type cast
The result of enum to str type cast will be a str value of the variant.

{% cut "Example 1" %}

```
type Color = enum { Red [[str="G"]], Blue };       

var a = Color.Red as str;                      // The value of 'a' variable is the 'str' value 'G'.
var b = Color.Blue as str;                     // The value of 'b' variable is the 'str' value 'Blue'.
The result of str to enum type cast will be a variant with the str value equal to the operand's value. An enum type should have the variant with such str value, otherwise a runtime error E_TypeCastError.
```

{% endcut %}

Example:

type Color = enum { Red, Green = 2 [[str="G"]], Blue };

var x3 = "G" as Color;                                    // x3 == Color.Green.
var x4 = "Red" as Color;                                  // x4 == Color.Red – default 'str' value.
var x5 = "Green" as Color;                                // Runtime error – E_TypeCastError, the type 'Color' doesn't have a variant with a str value 'Green'.
enum <-> int type cast
