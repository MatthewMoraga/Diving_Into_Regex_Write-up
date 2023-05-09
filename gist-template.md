# Diving Into Regex: A Tutorial 
## Written By: Matthew Moraga

## Intro
```
This is a write up and a tutorial of sorts about Regex which is short for Regular Expression, and is a way of describing a pattern of characters.
It is a powerful language used to perform complex text searches and string manipulations. 
It is also used in many programming languages, text editors, and command line tools.
``` 
## Summary
```
In this tutorial I will be going over this example Regex which is matching a URL. 
`/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/`
This involves using Regex to define a search pattern that will match a URL string. 
This pattern can include any combination of letters, numbers, and special characters.
Allowing you to match URLs of any length and complexity, and Once the pattern is defined. 
The Regex engine will use it to search for the URL string within a text document and return any matches.
```

# Table of Contents

- [Anchors](#anchors)
- [Quantifiers](#quantifiers)
- [Grouping Constructs](#grouping-constructs)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [The OR Operator](#the-or-operator)
- [Flags](#flags)
- [Character Escapes](#character-escapes)
- [Sources](#sources)
- [Author](#author)

# Regex Components
### Overview
```
Regex components are the individual elements that make up a regular expression.
These components can include literal characters, character classes, special characters, anchor characters and quantifiers.
- Literal characters are the indvidual characters that are used to match specific sequences of text.
- Character classes are sets of characters that match anything within the set.
- Special characters are used to match certain types of characters such as digits or whitespace.
- Anchor characters are used to match the beginning or end of a string.
- Quantifiers are used to specify the number of times a character or group of characters may appear in a string.
```

### Regex Example Pattern Using Literal Characters
```
If you wanted to match the word "cat" in a string. You could use the regex pattern "[cC][aA][tT]".
This pattern contains literal characters - c, a, and t.
Each one is written twice in order to match both lowercase and uppercase versions.
The literal characters are the components of the regex pattern.
They are used to match the exact sequence of characters that make up the word "cat".
```
# Anchors
### Overview
```
Regex anchors are special characters used to specify the start or end of a string.
They are used to ensure that the regular expression matches only the exact string you are looking for.
The two most common anchors are the caret(^) and dollar sign ($).
The caret is used to specify the beginning of a string and the dollar sign is used to specify the end of a string.
```
### Anchor Example
```
An example of anchors would look something like this "^cat$", but it will only match the string "cat".
Any other strings that contain the literal characters "c", "a", and "t" will not be matched.
Since the caret and dollar sign anchors are used it will ensure that the Regex engine only matches the exact
sequence of characters that make up the word "cat".
```
### Other Anchor Characters
```
While caret(^) and dollar sign($) are the most commonly used ones. 
There are other types such as:

- The word boundary anchors (\b and \B).
The word boundary anchors are used to match the beginning or end of a word.

- The lookahead and lookbehind anchors (?= and ?!).
The lookahead and lookbehind anchors are used to define condtions for a match.

- The assertion anchors(?<= and ?>).
The assertion anchors are use to match text that is preceded or followed by a given pattern.

- The conditional anchors(?( and )).
The conditional anchors are use to create branches in a Regex pattern.
```
### Word Boundary Anchor Example
```
If you wanted to search the word "cat" in a string, but only if it is preceded by the word "dog".
You could use the Regex pattern "dog\b\scat$"
This pattern consists of two anchor characters - the word boundary anchor (\b) and the dollar sign($).
The word boundary anchor ensures that the Regex engine only matches the "cat" if it is preceded by the word "dog".
The dollar sign($) ensures that the Regex engine only matches the exact sequence of characters that make up the word "cat".
- Note:
The s in the pattern stands for a whitespace character. It is used to make sure that the Regex engine only matches the word
"cat" if it is preceded by the word "dog" and a whitespace character.
This helps to ensure that the Regex engine is only matching the exact sequence of characters that make up the word "cat".
```
### Lookahead/Lookbehind Example
```
To match a string that is preceded by the word "cat" you could use a lookbehind anchor /(?<=cat)string/
To match a string that is followed by the word "dog" you could use a lookahead anchor /string(?=dog)/ 
```
### Assertion Anchor Example
```
Assertion anchors are special characters that are used to check if a certain condition is true before or after the current position in a string.
This pattern shows how an assertion anchor can check if the current position is preceded by the word "cat".
/(?<=cat)string/
The anchor will only match the string if preceded by the word "cat", otherwise it will not match.
```
### Conditional Anchor Example
```
Conditional expressions are used to specify a certain condition in orderfor the expression to be matched. 
To match a the string "hello" only if it is preceded by the word "cat":
/(?(?<=cat)hello|world)/
If the string is preceded by the word "cat", it will match "hello", otherwise it will match "world".
------
- Note:
The | character is a conditional opertor. It is used to specify that the expression wll mtach either string "hello" if it is preceded by the word "cat"
or the string "world" if it is not preceded by the word "cat".
```
### A full Anchor Example
```
^(https?:\/\/)(\b\w+(\.\w+)+)(\/\w+)*(\/\?[a-zA-Z0-9\-\=]+)?$
- the caret (^) matches the beginning of the string
- the dollar sign ($) matches the end of the string
- the word boundary anchor (\b) is used to match the start and end of words, while the non-word boundary anchor (\B) is used to match the middle of words.
- the ? anchors are used for optional matching. They are used to specify that the preceding group of characters can be matched zero or one times. 
The ? anchors in this example are used to specify that the (/) and the query string (\/?[a-zA-Z0-9\-\=]+)? can be matched zero or one times.
------------------------------------------------------------------------------------
- Note: the slashes (/)(\) are called character escapes and will be covered later on
- Note: the w+ is a character class and will be covered later on.
- Note: the + and * are quantifiers and will be covered later on.
I wanted to show what anchors do in a full Regex pattern.
```
# Quantifiers
```
Quantifiers are special characters or symbols used to specify the number of times a character, group of characters, should be matched in a string.
They allow the Regex engine to match a character, or a group of chracters, a certain number of times or within a certain range.
Common quantifiers include the asterisk(*), the plus sign(+), the question mark(?), and the curly brackets({}). 
```
### The Asterisk Quantifier
```
The asterisk(*) quantifier is used to indicate that the preceding character or group of characters should be matched zero or more times.
If you have the regular expression "a", it will match the strings "a", "aa", "aaa", etc.
------------------------------------------------------------------
- Note: The asterisk quantifier is also known as the "Kleen star".
- Some History: The name "Kleene star" for the asterisk quantifier comes from the mathmetician Stephen Kleene who developed a notation for regular expression.
He used the asterisk to represent a wildcard character that could match any character, or no character at all.
This notation is still used today, and the asterisk is often referred to as the "Kleene star" in honor of his work.
```
### Asterisk Quantifier Example
```
You can have a regular expression written like this "a*b". This expression would match strings such as "b", "ab", "aab", "aaab", etc.
```
### The Plus Sign Quantifier
```
The plus sign quantifier is used to indicate that the preceding character or group of characters should be matched one or more times.
A regular expression written like this "a+" will match strings such "a" it will match strings such as "a", "aa", "aaaa", etc.
```
### Plus Sign Quantifier Example
```
You can have a regular expression written like this "a+b". It would match strings such as "ab", "aab", "aaab", etc.
```
### The Question Mark Quantifier
```
The question mark quantifier is used to indicate that the preceding character or group of characters should be matched zero or one times.
If you have the regular expression "a?", it will match the strings "a" and “”.
----------------------------------------------------------------------------
- Note: “” is an empty string which represents the absence of any character.
The regular expression "a?" will match either the single character "a" or nothing at all.
```
### Question Mark Quantifier example
```
You can have a regular expression written like this "a?b" and it would match strings such as "b" and "ab".
```
### The Curly Brackets Quantifier
```
The curly brackets quantifier is used to indicate how many times a character, or group of characters, should be matched n a string.
If you have the regular expression "a{2}", it will match the string "aa".
The numbers inside the curly brackets can also be replaced with a range. If you have "a{2,4}"
the expression will match strings "aa", "aaa", "aaaa".
```
### Curly Brackets Quantifier Example
```
You can have a regular expression written like this "a{2,4}b" "aabb", "aaabb", "aaaabb", and "aaaaabb".
```
### Quantifiers Full Expression Example
```
^(\w*\+{2,4}?{2,4})$
Here the expression is looking for strings that begin with the word character (\w*) followed by two to four plus signs
followed by two to four optional characters.
- the caret(^) anchor marks the beginning of the expression
- \w is a word bounday anchor looking for any strings that begin with the w character in them
- the asterisk(*) quantifier is checking to see if w in the string should be matched zero or more times
- the plus sign(+) quantifier checks to see if w is in the preceding string one or more times
- the curly brackets({}) quantifier is checking for a range of times w matches in a string
- the question mark(?) quantifier is checing for optional characters at the end of the string
with  curly brackets checking for optional chracters that shouldbe matched up to a range of two to four times
- the dollar sign($) anchor marks the end of the expression
```
# Grouping Constructs
```
Grouping constructs are used to create "groups" within a regular expression.
The groups can then be used for backreferences or for further processing.
For example, in a URL regex, your grouping construct might be used to capture the protocol, host name, and path seperately,
so that you can use each part separately. 
This can be useful for further processing, such as validating only the hose name
or path, or for replacing tthe protocl in a URL.
The grouping construct in a regular expression would be parentheses: ().
```
### Example Grouping Contstruct
```
In a URL regex, the parentheses could be used to capture the protocol, host name, and path seperatley.
(https?)://([^/]+)(/.*)
```
# Bracket Expressions
```
Bracket expressions are a type of grouping construct used in regular expressions. 
They are used to match any character within a set of characters.
The syntax to enclose the set of characters in square brackets [].
If you have an expression like [abc] would match any of the characters a, b, or c.
Bracket expressions can also be used for character ranges, such as [a-z] which matches any lowercase letter from a to z. 
```
### Example Bracket Expression
```
A bracket expression written like this [0-9] matches any digit from 0-9.
Another expression [A-Za-z] matches any letter from A to Z both lower case and upper case.
```
# Character Classes
```
Character classes are a type of grouping construct used in regular expressions.
They are used to match any character within a predefined set of characters.
Character classes can be used to match characters based on their type (such as digits, letters, punctuation, etc.)
or based on their position in the alphabet of unicode table.
If you have the expression \d it would match any digit (0-9), while the expression \w 
would match any word character (A-z,a-z,0-9,and_).
```
### Character Classes Example
```
If you have an expression written like this \d{4}\s[A-Z]{2}, would match a four digit number followed by a space
and two uppercase letterss
```
# The OR Operator
```
Thr or operator (|) is used in regular expressions to match one of two or more patterns.
The or operator will match whatever pattern is on its left or tight side.
If you have an expression "cat|dog" it will match the word cat or dog.
```
### Or Operator Example
```
If you have an expression \d{3}|\d{4} it will match either a three digit number or a four digit number.
```
# Flags
```
Flags are used to modify the behavior of the expression.
Flags can be used to make expressions case-insensitive, or to make them match across multiple lines.
Flags can also be used to turn on and off certain features such as backreferences or lookahead and lookbehind assertions.
```
### Flag Example
If you have an expression written like (?i)cat it would match the word "cat" regardless of the case (uppercase or lowercase).
The flag (?i) makes the expression case-insensitive.

# Character Escapes
```
Character escapes are used to match special characters, such as newline, tab, and carraige return.
Character espcapes are used in the form of a backslash followed by the character.
The escape of a newline is \n and the escape for a tab is \t.
Character espcapes can also be used to match characters with special meaning in regular expressions,
such as the asterisk(*) or the dot(..)
```
### Character Escape Example
```
If you have an expression written like this \d{2}\s\n it wouldm match a two digit number followed by a space"\s", and a newline character(\n).
```

# In Conclusion
```
Using regex can be really handy to make searching for particular characters and digits to match with a URL.
You can even find sites that have the word "regex" or the number "17".
Regex can also be used for more than just URLs and are used to make sure a user is writing the thing in their HTTP request.
```

# Sources
```
I feel that it's important to source where you got your information from for writeups like these.
That way people can see where you got your info from and you can refer back to the links later.
Shoutout to www.regular-expressions.info since they explained things really well.

Intro
https://www.digitalocean.com/community/tutorials/an-introduction-to-regular-expressions

Summary
https://www.regular-expressions.info/url.html

Regex Components
https://www.regular-expressions.info/refquick.html
https://www.regular-expressions.info/tutorial.html

Anchors/Example
https://www.regular-expressions.info/anchors.html
https://www.regular-expressions.info/refanchors.html
https://www.regular-expressions.info/refcharacters.html
https://www.regular-expressions.info/lookaround.html

Quantifiers
https://www.regular-expressions.info/quantifiers.html
https://www.regular-expressions.info/asterisk.html
https://www.regular-expressions.info/history.html
https://www.regular-expressions.info/plus.html
https://www.regular-expressions.info/questionmark.html
https://www.regular-expressions.info/curlybrackets.html

Grouping Constructs

Bracket Expressions
https://www.regular-expressions.info/brackets.html

Character Classes
https://www.regular-expressions.info/charclass.html

The OR Operator
https://www.regular-expressions.info/alternation.html

Flags
https://www.regular-expressions.info/flags.html

Character Escapes
https://www.regular-expressions.info/characters.html

```

# Author

I am coding bootcamp student and really excited to be here.

GitHub Profile: https://github.com/MatthewMoraga