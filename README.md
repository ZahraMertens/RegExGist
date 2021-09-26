# Regex - Matching an Email

A "Regex" stands for regular expression and is a string of specific characters which allows us to search for specific patterns of text within string. This patterns are a universal powerful tool as they are used to validate text and/or search through text and can be used in more than one language such as Python and JavsScript.
When you first look at a regular expression it can look extremely complicated, this is because there are endless possible combinations to describe a string and it takes practice to fully understand the syntax.

a sequence of characters a search pattern for text

This specific tutorial will explain the Regex of matching an email.

## Summary

A possible Regular Expression to describe whether a text or input matches the email format is:

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

This specifc sequence of characters is used to validate if the email fulfills the email format requirements. Here is how the string breaks down: 

* The string can contain any lower case letters
* Can contain and number from 0 to 9
* Can contain a . a -
* Must contain a @
* Followed by 
* Followed by a .
* followed by any lower case letters with the max amount of 6 and the min of 2

each character of the regex string is a literl charactr
meta characters allow us to create a generic regex string 
. any character 	A period (special character: needs to be escaped by a \) \. (escapes the dot) excaoe character
* zero or more
".*" matches everyting

Shorthand characters \d Since certain character classes are used often, a series of shorthand character classes are available. \d is short for [0-9]. In most flavors that support Unicode, \d includes all digits from all scripts. Notable exceptions are Java, JavaScript, and PCRE. These Unicode flavors match only ASCII digits with \d.

. ca be anything in a regex





Briefly summarize the regex you will be describing and what you will explain. Include a code snippet of the regex. Replace this text with your summary.

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

As Regex is a literal, to match the regex structure requirements the string characters/ meta characters must be wrapped in forward slashes ' "/" characters "/" '.

### Metacharacter

### The Dot

To understand the "Matching an email" regex there are some things which are mendatory to understand. The dot in a regex has a special meaning as it can be used as a wildcard. By default, the dot is a metacharacter and can match any single character, so it can be used as a letter, digit, whitespace or special character (except line breaks). So for example if we use "...\." this could match many different strings such as: "cat.", "891.", "?=+." because the dot (.) can be anything. 

What what if we want to specificly find a dot insetad of any character? We then use a syntax called "escaping a character" which is basicall using a backslash before the special character: \. . This syntax means that the dot is not defined as any character anymore, in fact it is now "just" a dot (.).

Example:

 * alert("5.1".match(/\d\.\d/)) = MATCH, because \d is any digit and \. is a dot, so \d\.\d is the same as 5.1
 * alert("51".match(/\d\.\d/)) = NO MATCH, because expression is looking for a real dot but the string does not contain one.

** Note: To "escape" other characters the backslash is also used for [ \ ^ $ . | ? * + ( ). The syntax is the same as the dot. So: to use the $-sign we must use "\.".


### Anchors

In the email regex, there are two different anchors in order to signify the beginning and end of the regex. 
In order to validate when the email regex starts and ends we use anchors. To indicte the beginning of regular expression we use ^ so every character that follows is considered as being part of the pattern we are looking for. In order to indicate the end of the regex we use $

In a regular expression line anchors do not match any characters in the text. In fact they are used to match the position before and after characters. In the email regex we can find two characters which are considrered anchors: A caret (^) and the dollar sign ($). The caret matches the position before the first character in the string and the $-sign machtes right after the last character in the string.

In general there are two possible options the string could start or end with:

 1. The beginning or end could match an exact string. E.g. If the regex would be ^user this means that the next needs to start with "user". If the text starts with "User", it would not match as a regular expression is case sensitive.
 2. The start or end of the string can have multiple possible matches, if we use a bracket expression. (See bracket expressions below)

If we use this concept on our "Match an email" regex, the string must start with characters which match this pattern: [a-z0-9_\.-]. This means that it could start with a lower case letter, a number from 0 to 9 or a special character.
As we also use a bracket expression at the end of the string we text must end with a combination of charaters which match this pattern: [a-z\.]{2,6}.

To understand the patterns described above, the next section will explain the xact meaning of it.

The caret (^) is used to signify a string with the characters that follow it. As we use a bracket a bracket expression right after the caret, there i a range of possible matches.
The $ anchor in the email i also perceded by a bracket expression which means there is a variety of options the string could end with.

`/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/`

If we take out email regex we can see the anchors at the beginning and end of the regex. This defines that the beginning of the regex can start with any lower case letter, any number from 0 to 9 or the special characters. If the would start the email with ?test@user.com it would not match the regex and thorw an error.

### Bracket Expressions

A bracket expression is a subexpression of the regex string and can match the expression or not match the expression. In the email regex it is used to match a specific set of mulyiple characters such as any letter from a to z or any number from 0-9. The characters inside of the brackets ([]) represent the scope of characters which we want to match. The content of the so called "Bracket Expression" describe the characters we want to include in our text in order to match the regex. 
It is very common to use a hyphen (-) between letters or numbers to describe the range of characters which we are looking for. It is sort of a shortcut of writing the exprssion. E.g. [abcde] is the same as [a-e] or [12345] is the same as [1-5].

In our specific case of the "Match an email" Regex we have multiple bracket expression: 

1. [a-z0-9_\.-] The string can contain any lower case letter, any number from 0 to 9 or can contain special characters such as the hyphen (-), an underscore (_), ... 
As this bracket expression follows the ^ anchor, it measn that the beginning of the string we want to match can start with any of the above named characters. It is aso important to understand that it is not mendatory that all characters are present at the same time. So possible options would be: "test-12", "user_test", "user", "12user_". Also note that for example "User_12" would not match our pattern as only lower case letters are valid in the string so in order to make this valid we would need to change the bracket expression to: [a-zA-Z0-9_\.-] 
In our example we use a quantifier after the bracket expression. To learn about quantifiers read below.
2. [\da-z\.-]
3. [a-z\.]


### Quantifiers

In a regex there are multiple options of quantifiers and specify how many instances of a charcter, group or charcter class must be present in the text for the match to be found. Following are the most common ones:

* "*" This quantifier describes that the character must be present zero or more times and is considered a greedy quntifier. This expression is equivalent to {0,}
* "+" This greedy qunatifier describes that the instance
? match zero or one time
{n, m} match from n to m: this is integer consistant as a greedy quantifier such as * or + can match endless characters, this expression specifies  





### Grouping Constructs

To describe a grouping in a regex the characters are placed within parentheses and is used to restrict alternations.





### Character Classes

Character Classes are used to tell the regex engine to match only one out of several characters and are indicated by characters wrapper in square brakets such as: [a-z0-9_\.-]. Usually a character class macthes only a sinle character and the order in the text is not relevant. 
To specify a range of characters we can use the hyphen ("-") [a-z]. As for example in the email regex we are looking for more than just one letter or number before the at sign, we can use a ?, * or + to repeat the character class in order to be able to validate the part in an email before the @ such as "test.user12". As we use the + sign after the character class we tell the regex engine that it is repeating the character class more than once.

### The OR Operator

### Flags

### Character Escapes

## Author

A short section about the author with a link to the author's GitHub profile (replace with your information and a link to your profile)