# Regex Tutorial

This tutorial will be walking through a regular expression, or Regex, and breaking down what each code snippet means. 

## Summary

I'm going to explain a regex that is used to match the format of an email address:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

(insert explanation here)

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

boundar

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
