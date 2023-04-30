# Regular Expressions (Regex) Tutorial: Matching an Email

Today I will be diving into a concise summary of regular expressions. A regex, or regular expression, is a string of text that allows a user to create patterns that aid in matching, locating, and handling text. Regular expressions define a search pattern that is intended to be used in pattern matching with strings or string matching, such as "find and replace" operations. Regular expressions can save you hundreds of hours if you work with text or need to parse massive volumes of data into a computer. These expressions can also be used from the command line or in text editors to find text within a file.

## Summary

I will be analyzing the below regex related to matching an email. 

/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/

Email addresses are validated using this regular expression. The email address is segmented into three parts: the username, the domain name, and the top-level domain (or TLD). Each of these parts are enclosed in parentheses, indicating each separate group. All three of these components work together to ensure that the email address being validated is well-built and correct when inputed into the computer software. 

## Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)

## Regex Components

### Anchors

The first anchor used in this regular expression is the ^ (caret) character. The ^ character signifies the start of the entire email string. It ensures that the pattern must match the beginning of the string, and nothing that comes before it. 

The second anchor used in this regular expression is the $ (dollar sign) character. The $ character signifies the end of the entire email string. It makes sure that the pattern must match the end of the string, and nothing that comes after it.

Together, the ^ and $ characters symbolize the start and end of the email string. Both characters guarantee that the whole string matches the email pattern, and nothing else. 

### Quantifiers

Quantifiers are special characters that allow the user to specify how many times a character or group of characters must appear in the input in order for a match to be detected. Individual characters, character classes, groupings, and even other quantifiers can use these characters. 

Throughout the matching an email regex, there are three quantifiers used:

1) The + character. This quantifier means "one or more times". In this regex, the + character is found directly after the `[a-z0-9_\.-]` and `[\da-z\.-]` character classes, meaning that the characters within those classes can appear one or more times in the matched email string input. 

2) The {2,6} quantifier. This is set up in the {x,y} format, where x is the minimum and y is the maximum value. This quantifier means "between 2 and 6 times". In this regex, the {2,6} quantifier is found directly after the `[a-z\.]` character class, meaning that the characters within that character class MUST appear between 2 and 6 times in the matched email string input. 

3) The '$' anchor. NOTE: Although this is not techincally a quantifier, the $ anchor is used to ensure that the regex input matches only email strings that end with the pattern specified in the regular expression. Therefore, it is an honorary quantifier!

### Grouping Constructs


### Bracket Expressions

There are three bracket expressions throughout the matching an email regex.

1) `[a-z0-9_\.-]+`: This character class matches one or more lowercase letters, numerals, underscores, dots (periods), or dashes in the email address before the @ sign. The + sign after the bracket expression means that there must be at least one character in this character class. 

2) `[\da-z\.-]+`: This character class matches one or more numerals, lowercase letters, dots (periods), or dashes in the email address after the @ symbol and before the domain name. The \d shorthand character class matches any digit, and the backlash before the .- character indicates that they should be considered as literal characters, NOT as special regex characters. The + sign after the bracket expression means that there MUST be at LEAST one character in this character class. 

3) `[a-z\.]{2,6}`: This character class matches the domain name extension (example: org, edu, etc.) in the email address. The {2,6} quantifier after the bracket expression means that there must be between 2 and 6 characters in this character class. The . character in this character class is included to match domain names like .com.au or .co.uk. 

### Character Classes

### The OR Operator

### Flags

### Character Escapes

## Author

If you have questions, please send them [here](mailto:marleysue@gmail.com?subject=[GitHub]%20Dev%20Connect) or visit [github/marleyschneiderr](https://github.com/marleyschneiderr). My name is Marley Schneider, and I am a 23-year-old full-stack web developer in practice. I graduated from Washington State University in May 2022 with a double major in Advertising and Web Development and am now pursuing a certificate in Web Development through this course. I aspire to be a UX/UI designer who designs websites that are both useful and visually appealing. 