# Regex Tutorial

This tutorial will be walking through a regular expression, or Regex, and breaking down what each code snippet means. 

## Summary

I'm going to explain a regex that is used to match the format of an email address:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

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
Anchors: ^ and $ - characters in a regex that indicate the qualifying match of any string that starts with or ends with ^ and $, respectively.

Examples: 

`^For any$` - this is looking for an exact match of any string that starts with `For any`

`^For` - looks for a string that starts with `For`

`any$` - tries to find a string that ends with `any`

`thing` - finds a match for any string that has the text `thing` in it somewhere

### Quantifiers


### OR Operator

### Character Classes

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
