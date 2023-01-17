# **So You Want to Learn REGEX?**

AS A web development student
<br>
I WANT a tutorial explaining a specific regex
<br>
SO THAT I can understand the search pattern the regex defines

## **Summary**

A regular expression, or "regex," is a pattern that is used to match against a string. They can be used for tasks such as replacing text within a string, validating forms, and extracting substrings based on a pattern match. For example, when creating an application, a regular expression can be used to set rules for a user's chosen username. The regex could be used to ensure that the username only contains letters, numbers, underscores, and hyphens and that it has a limited number of characters for a clean interface. An example of such a regular expression for validating a username or email is: 
<br>
/^([a-z0-9_.-]+)@([\da-z.-]+).([a-z.]{2,6})$/.

## **Table of Contents**

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

# **Regex Components**


### **Anchors**

Anchors have special meaning in regular expressions. They do not match any character. Instead, they match a position before or after characters:

 * ^ – The caret anchor matches the beginning of the text.
 * $ – The dollar anchor matches the end of the text.
### **Quantifiers**

Quantifiers indicate that the preceding token must be matched a certain number of times. A quantifire can be greedy or lazy that is explained below.

* a*a+a? -0 or more, 1 or more, 0 or 1

* "+" Matches 1 or more of the preceding token.
* "*" Matches 0 or more of the preceding token.
* "?" Matches 0 or 1 of the preceding token, effectively making it optional.
*"?" Makes the preceding quantifier lazy, causing it to match as few characters as possible. By default, quantifiers are greedy, and will match as many characters as possible.
* a{5}a{2,} -Looks for exactly five, two or more

* {2,6} -forces the input of characters between two & six characters long.

* a+?a{2,}? -match as few as possible

* ab|cd -match ab or cd

### **OR Operator**

* | Acts as a boolean OR. Matches the expression before or after the |. It can operate on a whole expression, or within a group. The patterns will be tested in order.
### **Character Classes**

* The square brackets [] are used to match any character inside the brackets. For example, if you use [ABC], it will match any character that is A, B, or C.
* The caret symbol [^] is used to match any character that is not inside the brackets. For example, if you use [^ABC], it will match any character that is not A, B, or C.
* The dash [-] is used to match a range of characters. For example, if you use [A-Z], it will match any uppercase letter from A to Z.
* The dot (.) is used as a wildcard to match any character except for line breaks.
* The combination of \s and \S can be used to match whitespace and non-whitespace characters respectively.
* The \w  is used to match any word character, which includes alphanumeric characters and the underscore.
* The \W is used to match any character that is not a word character.
* The \d is used to match any digit character (0-9).
* The \p is used to match a character in a specified Unicode category.
### **Flags**

Expression flags are used to modify the way a regular expression is interpreted. They are added after the closing forward slash of the expression and can change how the expression is matched. Some of the most common flags include:

* The "i" flag, which stands for "ignore case", tells the expression to ignore the case of the characters it is matching. This means that it will match both uppercase and lowercase letters.
* The "g" flag, which stands for "global", tells the expression to perform a global search, which means that it will find all matches in the string, rather than just the first one. It also allows subsequent searches to start from the end of the previous match.
* The "m" flag, which stands for "multiline", allows the expression to match the start and end of a line, instead of the start and end of the whole string. This flag is particularly useful when working with multi-line text.
* The "u" flag, which stands for "unicode", enables full Unicode support for the regular expression.
* The "y" flag, which stands for "sticky", tells the expression to match from its lastIndex position and ignores the global (g) flag if set.
* The "s" flag, which stands for "dotall", tells the expression that the dot (.) will match any character, including newline.
### **Grouping and Capturing**

Parentheses () are used to group multiple characters or expressions together and create a "capture group". This means that the characters or expressions inside the parentheses can be accessed separately from the rest of the expression, and can be used to extract a specific substring from the match or to use a backreference.
* The syntax (?<name>ABC) creates a "named capture group" which allows you to refer to the specific group by name, instead of by its position.
* The syntax \1 is a "numeric reference" to a previously captured group. It refers to the first capture group, \2 refers to the second, etc.
* The syntax (?:ABC) is used to group multiple characters or expressions together without creating a capture group. 
### **Bracket Expressions**

A bracket expression enclosed in square brackets is a regular expression that matches a single character, or collating element. If the initial character is a circumflex ^, then this bracket expression is complemented.

### **Greedy and Lazy Match**

In regular expressions, "greedy" quantifiers will match the longest possible string. This means that the engine will try to match as many instances of the quantified token or subpattern as it can. For example, a greedy quantifier like '*' will match as many characters as possible.
<br>
In contrast, "lazy" quantifiers will match the shortest possible string. A lazy quantifier tells the engine to match as few of the quantified tokens as needed. For example, a lazy quantifier like '*?' will match as few characters as possible.
<br>
To make a regular quantifier "lazy" you can append a "?" (question mark) to it. This tells the engine to match as few instances of the quantified token or subpattern as possible.

###  **Boundaries**

The \b is an anchor like the caret and the dollar sign. It matches at a position that is called a “word boundary”. This match is zero-length.

Characters that are matched by the short-hand character class \w are the characters that are treated as word characters by word boundaries.

Since digits are considered to be word characters, \b4\b can be used to match a 4 that is not part of a larger number. So saying \b matches before and after an alphanumeric sequence is more exact than saying “before and after a word”.

\B is the negated version of \b. \B matches at every position where \b does not. Effectively, \B matches at any position between two word characters as well as at any position between two non-word characters.

There are more boundries with the Regex Engine. Some examples include Tcl, GNU, and POSIX.
### **Back-references**
Backreferences match the same text as previously matched by a capturing group. Suppose you want to match a pair of opening and closing HTML tags, and the text in between. By putting the opening tag into a backreference, we can reuse the name of the tag for the closing tag.

For Example: <([A-Z][0-9]*)\b[^>]*>.*?</\1> This regex contains only one pair of parentheses, which capture the string matched by [A-Z][0-9]*. This is the opening HTML tag. The backreference \1 references the first capturing group. \1 matches the exact same text that was matched by the first capturing group. The / before it is a literal character. It is simply the forward slash in the closing HTML tag that we are trying to match.
### **Look-ahead and Look-behind**
(?=ABC) is a postive lookahead and it matches a group after the main expression without including it in the result.

(?!ABC) is a negitive lookahead and it specifies a group that can not match after the main expression (if it matches, the result is discarded)

(?<=ABC>) is a postive lookbehind and matches a group before the main expression without including it in the result.

(?<!ABC) is a negitive lookbehind and Specifies a group that can not match before the main expression (if it matches, the result is discarded).

Lookaheads and lookbehinds forces the main expressions to be what you have defined it as. Without it being exactly what it is it will not be accepted as a valid input.
## **Author**

Andrew Simmons
<br>
github: https://github.com/asimmons03
<br>
University of Minnesota Web Development Bootcamp


## **Sources**

* https://coding-boot-camp.github.io/full-stack/computer-science/regex-tutorial
