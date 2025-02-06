---
{"dg-publish":true,"permalink":"/🖥/📜/🍊C/🖨stdio/format specifications/","tags":["c"]}
---


>[!definition] format (specifier)
>beginning with the `%` character, indicated the location & method of conversion applies to a data piece (e.g., a number) into characters to be displayed in screen. 
>see [[🖥/📜/🍊C/🖨stdio/🖨 printf\|🖨 printf]]

it has the following form:
![Pasted image 20241226194030.png](/img/user/Pasted%20image%2020241226194030.png)
- *flags* 
	justification of output and printing of signs, blanks, decimal points, octal & hexadecimal prefixes, and the semantics for `wchar_t` precision unit.
- *width*
	minimum number of bytes output
- *precision*
	👀[[🖥/📜/🍊C/🖨stdio/🖌formatting/format precision\|format precision]]
- *h, l, ll, L, H, D, DD*
	size of the expected arg (..)

## alternative format specification
has the following form:
![Pasted image 20241226194158.png](/img/user/Pasted%20image%2020241226194158.png)
as an alternative, specific entries in the arg-list can be assigned by using the format specification outlined up here^

>[!danger] the 2 format specifications **cannot** be mixed in the same call to [[🖥/📜/🍊C/🖨stdio/🖨 printf\|🖨 printf]]
>otherwise, unpredictable results...

- `arg-number` - a positive integer ct. s.t.
	- 1 - the first entry in the *argument-list*
	- ⚠ cannot be greater than the number of entries in the *argument-list*
	- ⚠ cannot be greater than `NL_ARGMAX
	- ...

## type characters

you indicate the way you want to display a piece of data by indicating what goes after the `%` char:

| character | argument         | output format                                                                             |
| --------- | ---------------- | ----------------------------------------------------------------------------------------- |
| `%`       |                  | `%` char                                                                                  |
| `i`       | integer          | signed decimal integer                                                                    |
| `d`       | integer          | signed decimal integer                                                                    |
| `u`       | integer          | unsigned decimal integer                                                                  |
| `x`       | integer          | an **unsigned** hexadecimal integer, using *abcdef*                                       |
| `X`       | integer          | an **unsigned** hexadecimal integer, using *ABCDEF*                                       |
| `c`       | character (byte) | a single character (char)                                                                 |
| `s`       | string           | characters (bytes) printed up to the first null char (\0) or until *precision* is reached |
| `p`       | pointer          | pointer converted to a sequence of printable chars, displayed in base 16.                 |

## flags

| flag        | meaning                                                                                                                                                                                                | default                                                 |
| ----------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ | ------------------------------------------------------- |
| `-`         | left-justify the result within the field width                                                                                                                                                         | right-justify                                           |
| `+`         | prefix output value with a sign ($+$ or $-$) if the output value is of a signed type                                                                                                                   | sign appears only for negative signed values ($-$)      |
| blank `" "` | prefix the output value with a blank if the output value is signed & positive. The `+` flag overrides the *blank* flag if they both appear, and a positive signed value will be output **with** a sign | no blank                                                |
| `#`*        | when used with `o`, `x`, `X` formats => prefixes any nonzero output value with `0`, `0x` or `0X`, resp.                                                                                                | no prefix                                               |
|             | when used with the `p` format => converts the pointer to hex digits. these hex digits cannot be converted back into a pointer, unless in a *teraspace* environment                                     | pointer converted to a sequence of printable characters |
| `0`         | when used with `d`, `i`, `u`, `x`, `X`... => causes leading $0$s to pad the output to the field *width*. this flag is ignored if *precision* is specified for an integer or if the `-` is specified.   | space padding                                           |

>[!warning] (\*) for `#`
>the `#` flag should not be used with the `c`, `d`, `i`, `u` or `s` types.

# width
>[!definition] width ($\omega$)
>a non-negative decimal integer controlling the minimum number of characters printed

- if $\# \{ \text{chars (bytes) in output value}\} < \omega$ => blanks are added on the left or right (depending on whether the `-` flag is specified) until minimum *width* is reached
- never causes a value to be truncated
  if $\# \{ \text{chars (bytes) in output value}\} > \omega$ **or** no specified *width* => all chars of the value are printed (subject to the *precision* specification)
- *width* specification can be an asterisk (\*), i.e. an argument from the argument list supplies the value. 
  - [!] the *width* argument **must** precede the value being formatted in the argument list
# precision
>[!definition] precision
>a non-negative decimal integer preceded by a period `.`, specifying the number of chars to be printed or the number of decimal places.
>unlike *width* specification, the *precision* **can** cause **truncation** of the output value or rounding of a floating-point or packed decimal value

- *precision* specification can be an asterisk (\*), i.e. an argument from the argument list supplies the value.
  - [!] the *precision* argument **must** precede the value being formatted in the argument list

>[!info] the interpretation of *precision* & default behaviour w not passed is determined by format type:


| type                         | meaning                                                                                                                                                                                                                                                       | default                                                                                                                    |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- |
| `i`, `d`, `u`, `o`, `x`, `X` | specifies the **minimum** number of digits to be printed. <br>if $\#\{\text{digits in argument}\} < \text{precision}$ => output value is padded on the left with zeroes.<br>❗value is not truncated when $\#\{\text{digits in argument}\} > \text{precision}$ | if precision is $0$ or omitted entirely, or if the period appears without a number following it => precision is set to $1$ |
| `c`                          | no effect                                                                                                                                                                                                                                                     | the `wchar_t` character is converted and resulting multi-byte character is printed                                         |
| `s`                          | *precision* specifies the maximum number of characters (bytes) to be printed. chars (bytes) in excess of *precision* are not printed                                                                                                                          | characters are printed until a *null* char is encountered                                                                  |


