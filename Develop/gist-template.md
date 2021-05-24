# Regex Tutorial

This tutorial will be walking through a regular expression, or Regex, and breaking down what each code snippet means. 

## Summary

following is an explaination of a regex that is used to match the format of an email address:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

* the `^` anchor denotes the beginning of the string and the `$` denotes the end of the string

* the 2 `+` are [quantifiers](#quantifiers) that connect the email address 'name', email services and the domain 

* `\d`is a [character class](#character-classes) looing for charcters that are a digit from 0-9.

* there are 3 [capture groups](#grouping-and-capturing).

  * `([a-z0-9_\.-]+)` corresponding to the email user name

  * `([\da-z\.-]+)` corresponding to the email service

  * `([a-z\.]{2,6})` corresponding to the domain

* the bracketed expressions include:

  * the character set `a-z0-9_\.-` which is looking for any letter from 'a' to 'z' and is case sensitive, a character from '0-9' and any of the characters '_', '-', and '.'.

  * `\da-z\.-` matches a single digit from '0-9', any character from 'a-z'(case sensitive) and the characters '.' and '-'.

  * `a-z\.` matches any character from 'a-z'(case sensitive) and the character '.'.

* greedy and lazy matching

because the regex contains the `+` [quantifier](#quantifiers) matches as many times as it can, returning all matches. the `{}` looks for the domain group to be at least 3 characters and up to 6.



## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Flags](#flags)
- [Grouping and Capturing](#grouping-and-capturing)
- [Bracket Expressions](#bracket-expressions)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
`^ $ -` characters in a regex that indicate the qualifying match of any string that starts with or ends with ^ and $, respectively.

Examples: 

`^For any$` - this is looking for an exact match of any string that starts with `For any`

`^For` - looks for a string that starts with `For`

`any$` - tries to find a string that ends with `any`

`thing` - finds a match for any string that has the text `thing` in it somewhere

### Quantifiers
`* + ? {}` - these regex characters look for matching patterns of the character immediately preceding the regex character and how many times it follows the string immediately before it

Examples: 

`ghi*` - finds a matching string that has >=0 `i`'s after the string `gh`

`ghi+` - finds a matching string that has >0 `i`'s after the string `gh`

`ghi?` - finds a matching string that has <=1 `i`'s after the string `gh`

`ghi{3}` - finds a matching string that has exactly 3 `i`'s after the string `gh`

`ghi{3,}` - finds a matching string that has >=3 `i`'s after the string `gh`

`ghi{3,6}` - finds a matching string that has at least 3 `i`'s and 6 after the string `gh`. the first number has to be less than the second

### OR Operator
`(|) or [|]` - the 'pipe' character inclosed in parenthesis or brackets matches either of two strings on either side of the 'pipe' immedatiely following the string previous to the left `(` or `[`

Examples:

`ball(boy|girl)` - looks for a string that `ball` followed by `boy` or `girl`. when you use `()`, you have the ability to capture the match you're looking for

`ball[boy|girl]` - same as above with the ability to capture the match

### Character Classes
`\d \w \s .` - these look for exact matches. `d` is for 'digit', `w` is for 'word', `s` is for 'space'. If you use an uppercase letter instead, like `\D`, it means the inverse. 

Examples:

`2\d` - matches any digit that is a '2'

`m\w` - matches any word character that is an 'm'. you can look for any character in the following range: 'a-zA-Z0-9_'

`\s` - matches any space, or whitespace, character

### Flags
`g m i` - these flags can be specified at the end of the  `/ /` regex to have the search pattern return as follows:

Examples:

`/baseball/g` - the g stands for 'global' and returns the first match. if you restart this search, it returns the rest of the matches

`baseball/m` - the m stands for 'multi-line' and when you use `^` or `$` it searches the entire line of text, not only the string.

`bAsEBaLl/i` - the i stands for 'insensitive'. run the example to the left would match the word 'baseball' or 'BASEBALL' or 'BasEBaLL', for example.

### Grouping and Capturing

`()` - used to extract information from strings or data and put in an array to allow for accessing via their index in said array.

Examples:

`x(yz)` - looks for the first occurrence of the string `yz` following `x`

`x(2)` - looks for the first occurrence of the string `2` following `x`

`x(?:)` - including `?:` disables the capture group

`x(?<>)` - including `?<>` gives a name to the group

### Bracket Expressions

`[]` - matches characters enclosed by `[]`
`^` - using a `^` looks for any character *not* in the list
`%` - including a `%` matches the string inside the brackets before the `%`

Examples:

`[abc]` - matches a string that has `x`, `xy`, or `xz`
`[^h-m]` - matches a string that does not have a character from h to m, inclusive
`[0-9]%` - matches a string that has a charater from 0-9 before a `%`

### Greedy and Lazy Match

`Greedy` means to match the longest possible string

`Lazy` means to match the shortest possible string

Examples:

`ba?` - matches a `b` character(case sensitive) and an `a` character or nothing. For example `abc` returns a match. `ac` does not. `acb` returns a match. `a83d` does not.

`ba*` - matches a `b` character(case sensitive) and an `a` character as many times as possible. For example, `abc` returns a match. `ac` does not.  

### Boundaries

boundaries are the places between characters. the two types of boundaries are 'Word' and 'Non-word'.

Examples:

`\babc\b` matches whole words only for the string `abc`

`\Bb\B` matches `abc`

`B\c\B` does not match `abc`

### Back-references

when using Grouping, you can capture the group and save it for using later. When you use this saved group, it's called Back-referencing.

Examples:

if you're trying to match a string that has a digit from 0-9 and a lowercase character you could search with `[0-9][a-z]`. This matches `2-n-9` and `2 a-4`. the backreferencing looks at the match that was found in the capture group and matches the location exactly. the previous example would become `[0-9]\1[a-z]` where the `\1` signifies the first capture group. this now matches `2-n-9` or `2 n 9` but not `2 a-9` or `2-a/9`

### Look-ahead and Look-behind

you can have the following variations:

* positive lookahead: `(?=pattern)` - looks for a match of the pattern without including the pattern in the match. For example, if your data is `abcdef`, then `abc(?=def)` matches `abc`

* negative lookahead: `(?!pattern)` - if your data is `abcdef`, then `abc(?!def)` does not match

* positive lookbehind: `(?<=pattern)` - if your data is `abcdef`, then `?<=abc(def)` matches `def`

* negative lookbehind: `(?<!pattern)` - if your data is `abcdef`, then `(?<!abc)def` does not match


## Author

[Tim Weyel](https://github.com/timweyel) is currently (5/24/2021) a UC Berkeley bootcamp student studying Full Stack JavaScript.


