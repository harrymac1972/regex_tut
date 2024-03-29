
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
- [Bonus Content](#bonus-content)

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

A flag alters the default search behavior of a regular expression, causing it to execute searches in a modified manner.

`i`	- Ignore Casing <br>
`g`	- Global <br>
`s`	- Dot All <br>
`m`	- Multiline <br>
`y`	- Sticky <br>
`u`	- Unicode <br>

Syntax: `/pattern/flags`

Example: `/hello/i` makes the casing inconsequential.

### Grouping and Capturing

Grouping within regular expressions is a tool that streamlines patterns. For instance, it allows you to identify recurring sequences of characters, like phone numbers or email addresses, making pattern matching more efficient.

eg: `(\d{3})-(\d{3})-(\d{4})`<br>
would capture a typical North American phone number: `555-867-5309`


### Bracket Expressions

A bracket expression comprises characters enclosed within `[` and `]`. It matches any single character from that specified list. If the list begins with the caret '^', it matches any character not present in the list, and it's unspecified whether it matches an encoding error. For instance, the regex `[0123456789]` matches any single digit, while `[^()]` matches any character except an opening or closing parenthesis, potentially encountering an encoding error.

### Greedy and Lazy Match

Greedy means your expression will match as large a group as possible, lazy means it will match the smallest group possible. <br>
Addding a question mark at the end of quantifier will enable lazy match.
<br>
For this string: `abcdefghijklmc`, and this expression: `a.*c`
A greedy match will match the whole string, and a lazy match will match just the first `abc`.

### Boundaries

Simply put: `\b` allows you to perform a “whole words only” search using a regular expression in the form of `\bword\b`. A “word character” is a character that can be used to form words. All characters that are not “word characters” are “non-word characters”.<br>
<br>
eg: apply the regex `\bis\b` to the string `This island is beautiful`<br>
This returns the word in the middle `is` but not the 'is' in 'this' or 'island'.

### Back-references

Backreferences enable you to refer to and reuse the text captured by a capturing group within the same regular expression pattern.<br>
eg: `(a|b|cd)\1` matches `aa`, `bb` or `cdcd`<br>
Capturing groups and backreferences is very useful in various situations, including addressing the "finding duplicated words" problem.

### Look-ahead and Look-behind

 At the end of a lookahead or a lookbehind, the regex engine hasn't moved on the string.  Therefore "lookarounds stand their ground". They look immediately to the left or right of the engine's current position on the string—but do not alter that position.<br>
`(?=world)`	Lookahead	Asserts that what immediately follows the current position in the string is "world"<br>
`(?<=hello)`	Lookbehind	Asserts that what immediately precedes the current position in the string is "hello"<br>
`(?!world)`	Negative Lookahead	Asserts that what immediately follows the current position in the string is not "world"<br>
`(?<!hello)`	Negative Lookbehind	Asserts that what immediately precedes the current position in the string is not "hello"

## Bonus Content

While not using complicated regex expressions, finding all the purmutations of dates can become quite involved!<br>
The following is an SQLite table from an application I made at work to extract data from documents.<br>
There is just too many ways to write dates.  One has to wonder why this has not been made into a more uniform standard.<br><br>
![Screenshot_1](./imgs/dates_regex_format_table.png)

## Author

This feature presentation has been brought to you by Harry.<br>
Years ago I rode skateboards and BMX, now I ride motorcycles, in the future I will ride mobility scooters.<br>
<a href="https://github.com/harrymac1972">Harry on Github</a>
