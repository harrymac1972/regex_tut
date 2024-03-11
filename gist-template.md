
# REGEX: Regular Expressions - Pattern matching to get your data

Regular expressions are extremely valuable for extracting information from various types of text.  Examples include invoices, spreadsheets, long log files, etc.. The following lessons and examples will demonstrate practical applications of regular expressions, to facilite fast and accuract data extractions for your workflow.

An essential point about regular expressions is that each element within text is a character. Therefore, our objective is to devise patterns that precisely correspond to specific sequences of characters, ie: strings. These patterns are combinations of letters, digits, punctuation marks, and various keyboard symbols.

## Summary

While this guide should be fairly comprehensive, I will add extra focus on a challenge I have personally had in my business.  Matching patterns for dates.  The combinations of Regex Exprissions needed for dates from Canada, UK, and the US is truly surprising once one realizes how many need to be used.

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

Regex Anchors do not match any characters, they actually confirm that the current position of the regex search within the string aligns with specific locations. These locations may include the start of the string, or the end of a line.

In most cases, the caret anchor `^` asserts that the search is the beginning of the string. Therefore, `^a` matches an a at the beginning of the string.

To match at the very end of the string, the `$` anchor corresponds to the position immediately after the final character.  Example string = `the apple`, the `$` anchor matches the position after the e, and `e$` matches the final e, but not the first one.

### Quantifiers

Quantifiers determine the frequency of repetition for a specific segment of your regular expression. Whenever there's a need to repeat a component within a regex, a quantifier can be appended to indicate the desired repetition count.<br>

`{MAX,MIN}` - missing parameter == 'any'

eg: 'Range Quantifier' `enrol{1,2}` you'll be able to match both enrol AND enroll.
Note that other Quantifiers can be translated into ranges for comprehension.

`?` is `{0,1}`<br>
`*` is `{0,}`<br>
`+` is `{1,}`

### OR Operator

Parameters are separated by a 'pipe' character. <br>
eg: `hi|hello` == A string that contains either `hi` or `hello`

### Character Classes

Simply place the characters you want to match between square brackets. If you want to match an a or an e, use `[ae]`. You could use this in `gr[ae]y` to match either `gray` or `grey`.

A very common use is to search for only digits: `[0-9]`.  Note the hyphen represents a range.

Another common use case is to find a hexadecimal digit: `[0-9a-fA-F]`

Placing a caret immediately after the opening square bracket negates the character class.  ie: `q[^u]` means “a `q` followed by a character that is not a `u`”.

### Flags

### Grouping and Capturing

### Bracket Expressions

### Greedy and Lazy Match

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)
