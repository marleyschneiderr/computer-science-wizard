# Regular Expressions (Regex) Tutorial: Matching an Email

Today I will be diving into a concise summary of regular expressions. A regex, or regular expression, is a string of text that allows a user to create patterns that aid in matching, locating, and handling text. Regular expressions define a search pattern that is intended to be used in pattern matching with strings or string matching, such as "find and replace" operations. Regular expressions can save you hundreds of hours if you work with text or need to parse massive volumes of data into a computer. These expressions can also be used from the command line or in text editors to find text within a file.

## Summary

I will be analyzing the below regex related to matching an email. 

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

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

The first anchor used in this regular expression is the `^` (caret) character. The `^` character signifies the start of the entire email string. It ensures that the pattern must match the beginning of the string, and nothing that comes before it. 

The second anchor used in this regular expression is the `$` character. The $ character signifies the end of the entire email string. It makes sure that the pattern must match the end of the string, and nothing that comes after it.

Together, the `^` and `$` characters symbolize the start and end of the email string. Both characters guarantee that the whole string matches the email pattern, and nothing else. 

### Quantifiers

Quantifiers are special characters that allow the user to specify how many times a character or group of characters must appear in the input in order for a match to be detected. Individual characters, character classes, groupings, and even other quantifiers can use these characters. 

Throughout the matching an email regex, there are three quantifiers used:

1) The `+` character. This quantifier means "one or more times". In this regex, the + character is found directly after the `[a-z0-9_\.-]` and `[\da-z\.-]` character classes, meaning that the characters within those classes can appear one or more times in the matched email string input. 

2) The `{2,6}` quantifier. This is set up in the `{x,y}` format, where x is the minimum and y is the maximum value. This quantifier means "between 2 and 6 times". In this regex, the `{2,6}` quantifier is found directly after the `[a-z\.]` character class, meaning that the characters within that character class MUST appear between 2 and 6 times in the matched email string input. 

3) The `$` anchor. NOTE: Although this is not techincally a quantifier, the `$` anchor is used to ensure that the regex input matches only email strings that end with the pattern specified in the regular expression. Therefore, it is an honorary quantifier!

### Grouping Constructs

In regular expressions, grouping constructs are used to group together a series of characters or expressions, and they are ALWAYS wrapped in parenthesis. When using grouping constructs, a user can apply operators to the entire group rather than just one character or expression within the group.

Example: Alteration - Within a group, you can specify alternative matching options by using the pipe symbol `|`. `(cat|dog)` would, for example, match either `"cat"` or `"dog"`.

In the email sequence, there are 3 examples of grouping constructs:

1) `([a-z0-9_\.-]+)`: This grouping construct creates a 'capturing group' that matches one or more lowercase letters, numbers, dots, or hyphens. This group represents the matching for the username section of an email address.

2) `([\da-z\.-]+)`: This grouping construct creates a 'capturing group' that matches one or more lowercase letters, numbers, dots, hyphens, or underscores. This group represents the domain name portion of an email address.

3) `([a-z\.]{2,6})`: This grouping construct creates a 'capturing group' that matches 2 - 6 lowercase letters or dots. This group represents the top-level domain (TLD) section of an email address (example: .com, .edu, .org, etc.)

### Bracket Expressions

There are three bracket expressions throughout the matching an email regex.

Example: `[0-9]` is a strong example of a bracket expression. This character type corresponds to any single digit from 0 to 9. For example, the regular expression `/[0-9]+/` would match any sequence or input of one or more numbers, such as 456 or 9, but not 1a2e4r. 

1) `[a-z0-9_\.-]+`: This character class matches one or more lowercase letters, numerals, underscores, dots (periods), or dashes in the email address before the @ sign. The + sign after the bracket expression means that there must be at least one character in this character class. 

2) `[\da-z\.-]+`: This character class matches one or more numerals, lowercase letters, dots (periods), or dashes in the email address after the @ symbol and before the domain name. The \d shorthand character class matches any digit, and the backlash before the .- character indicates that they should be considered as literal characters, NOT as special regex characters. The + sign after the bracket expression means that there MUST be at LEAST one character in this character class. 

3) `[a-z\.]{2,6}`: This character class matches the domain name extension (example: org, edu, etc.) in the email address. The {2,6} quantifier after the bracket expression means that there must be between 2 and 6 characters in this character class. The . character in this character class is included to match domain names like .com.au or .co.uk. 

### Character Classes

Character classes are a set of characters surrounded by square brackets that describe the characters that will properly match a single character from a specified input string, in this case, within an email address. 

Example: The character class `[abc]` matches any single character that is either `a`, `b`, or `c`.

In the regex email example, there are 4 character classes:

1) `[a-z0-9_\.-]`: This character class matches any lowercase letter (a-z), digit (0-9), underscore `_`, dot `.`, or dash `-`. The brackets mean that any one of these characters can be matched.

2) `\d`: This shorthand character class matches any digit from 0 to 9.

3) `[a-z\.]`: This character class matches any lowercase letter (a-z) or dot `.`.

4) `{2,6}`: As said previously, this quantifier specifies the minimum and maximum number of characters that can be matched by the preceding character class. For this specific example, it says the preceding character class, `[a-z\.]`, can match between 2 and 6 characters.

### The OR Operator

In the regular expression `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, the OR Operator is not used. This expression uses character classes to match certain types of characters for each email input.

In regular expressions, the OR operator is signified by the `|` variable. 

Example: `/Marley|Mark|Miryka` - This regex pairs with any of the strings `Marley` `Mark` or `Miryka`. The vertical bar variable spaces out the three options, so if each individual name was found in the target text, it would still be a match.

### Flags

In the regular expression `/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`, flags are not used. 

Flags are optional parameters in regular expressions that change the behavior of the target text matching. 

Example: `s` - Known as dot-all, this expression allows the `.` character to match any character in the input, including newlines. Newlines are special characters used to represent the end of a line of text, indicating a link break in a file.

### Character Escapes

Character escapes are a way of indicating that a particular character should be treated as a literal character rather than a special character with its regular expression meaning.

Character escapes can be used in regular expressions to represent other characters that have specific meanings. For example, curly braces `({ hi })`, plus sign `(+)`, square brackets `([ hi ])`, question mark `(?)`, vertical bar `(|)`, and MORE.

Example: The dot character `.` has a specific significance in a regular expression in that it matches any single character. If a user wants to match a literal dot character, they should use the character escape `\.`. The escape character (the backslash) instructs the regular expression engine to consider the following character (in this case, the dot) as a literal character rather than its regular expression meaning.

In the email sequence, there are four character escapes used:

1) `\d`: This character escape matches any number character (those that are equivalent to `[0-9]`).

2) `\.`: This character escape matches a period character `.`. The backslash escapes the period due to the fact that the period is a special character in regular expressions that matches any character.

3) `\-`: This character escape matches a hyphen character `-`. The hyphen is used as a literal character is escaped with a backslash as well. 

4) `\[ and \]`: This character escape matches a square bracket character. The square brackets are used as literal characters and are also escaped with a backslash.

Note: Some of these character escapes are used within character classes (i.e., inside square brackets), where they have slightly different meanings than outside of character classes. For example, the dot `.` matches a literal dot (period) within a character class, but it matches any character except a newline outside of a character class.

## Author

If you have questions, please send them [here](mailto:marleysue@gmail.com?subject=[GitHub]%20Dev%20Connect) or visit [github/marleyschneiderr](https://github.com/marleyschneiderr). My name is Marley Schneider, and I am a 23-year-old full-stack web developer in practice. I graduated from Washington State University in May 2022 with a double major in Advertising and Web Development and am now pursuing a certificate in Web Development through this course. I aspire to be a UX/UI designer who designs websites that are both useful and visually appealing. 