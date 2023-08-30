# Tutorial: Regex matching Hex value

Regular expressions are combinations of special character operators, which are symbols that control the search, that you can use to construct search strings for advanced find and/or replace searches.are patterns used to match character combinations in strings. In a regular expression the metacharacter ^ means "not". So, while "a" means "match lowercase a", "^a" means "do not match lowercase a".

## Summary
Today I will be covering and breaking down the components of a regular expression used to match Hex Values. Hexadecimal code is a numbering system, it can be used to represent large numbers with fewer digits, its ensuring a consistency and accuracy in an electronic display. A hexadecimal color value is a six-digit code preceded by a "#" sign; it defines a color that is used in a website 
/^#?([a-f0-9]{6}|[a-f0-9]{3})$/

## Table of Contents

- [Character Classes](#character-classes)
- [Anchors](#anchors)
- [OR Operator](#or-operator)
- [Quantifiers](#quantifiers)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Bracket Expressions](#bracket-expressions)



## Regex Components

### Character Classes

/^#?(`[a-f0-9]`{6}|`[a-f0-9]{3}`)$/  
Character classes are components within our regular expression that tells us what type of characters to expect. In our example our character classes are confined within brackets `[]`. For our example we have 2 character classes: `[a-f0-9]` and `[a-f0-9]` which searches for the same values. We will be breaking down what the characters are searching within these character classes. `a-f` searches for letters `a-f` and `0-9` searches for digits `0-9`.

### Anchors

/`^`#?([a-f0-9]{6}|[a-f0-9]{3})`$`/  
Anchors do not match any characters at all. Instead, they match a position that is before, after, or between characters. They can be used to “anchor” the regex match at a certain position. The caret `^` matches the position before the first character in the string. Applying `^a` to `abc` matches `a`. `^b` does not match `abc` at all, because the `b` cannot be matched right after the start of the string, matched by `^`. See below for the inside view of the regex engine.
Similarly, `$` matches right after the last character in the string. `c$` matches `c` in `abc`, while `a$` does not match at all.



### OR Operator

/^#?([a-f0-9]{6}`|`[a-f0-9]{3})$/  
The "or" operator within a regular expression is defined using the `|` element. The or operator indicates that it could either of the components that we are separating with the `|`. For our hex value regular expression we have `([a-f0-9]{6}``|``[a-f0-9]{3})`. Note the or operator separating these 2 components. This means that our hex value could either be 6 characters `[a-f0-9]{6}` or 3 characters `[a-f0-9]{3}`.

### Quantifiers

/^#`?`([a-f0-9]`{6}`|[a-f0-9]`{3}`)$/   
Quantifiers are used to communicate how many characters are to be expected. Quantifiers specify how many instances of a character, group, or character class must be present in the input for a match to be found. By default, quantifiers are greedy, and will match as many characters as possible. If the "`,+,?,{}`" characters are found within regular expressions, they are considered quantifiers. The `?` indicates the expression to match `0` or `1`time. As mentioned in the summary above because there are 2 types of formats we'll use the or operator to distinguish which format we are using. In our Hex Value regular expression we have `{6}` (Hex Triplet Format) and `{3}` (Shorthand Hex Format), this indicates that the length of the component preceding these quantifiers should be `6` for `{6}` and `3` for `{3}`.

### Greedy and Lazy Match

/^#`?`([a-f0-9]{6}|[a-f0-9]{3})$/  
A greedy match tries to match an element as many times as possible. Whereas, a lazy match tries to match an element as possible. In my example we have `?`, this is referred to a lazy quantifier because it causes the regular expression engine to match the least occurances as possible. We can turn this lazy match into a greedy one by adding `?`.


### Bracket Expressions

/^#?`([a-f0-9]{3}|[a-f0-9]{9})`$/  
Matches any character in the square brackets. For example 	`[hH]` `[iI]` matches `hi`, `hI`, `Hi`, and `HI`.
`gr[ae]y` matches both spellings of the word `'grey'`; that is, `gray` and `grey`.