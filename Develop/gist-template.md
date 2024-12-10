# Regex Tutorial (UCB-VIRT-FSF-PT-07-2024-U-LOLC Homework Assignment #17)

Hello! This is a tutorial explaining how a specific regular expression (regex) functions by breaking down each part of the expression and describing what it does.

## Summary

The regular expression covered in this tutorial will be "Matching an Email":

```/^([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6})$/```

Each component of this regex has a unique responsibility to make sure that a string of text matches the expected pattern of an email address (i.e. an unspecified number of characters preceding the @ symbol, followed by a domain.  The specific components of the expression are broken out and defined below.   

## Table of Contents
Components included in the matching an email expression: 
- [Anchors](#anchors)
- [Bracket Expressions](#bracket-expressions)
- [Character Classes](#character-classes)
- [Grouping and Capturing](#grouping-and-capturing)
- [Quantifiers](#quantifiers)


Other common components:
- [OR Operator](#or-operator)
- [Greedy and Lazy Match](#greedy-and-lazy-match)
- [Flags](#flags)
- [Boundaries](#boundaries)
- [Back-references](#back-references)
- [Look-ahead and Look-behind](#look-ahead-and-look-behind)

## Regex Components

### Anchors
/  ```^``` ([a-z0-9_\.-]+)@([\da-z\.-]+)\.([a-z\.]{2,6}) ```$``` /<br>
The highlighted ```^``` and ```$``` characters are both "anchors" - characters used to denote the beginning and end of the expression, respectively.  


### Bracket Expressions
```[]``` - **Anything inside a square bracket ```[]``` represents a range of characters to match**

/^( ```[a-z0-9_\.-]``` +)@( ```[\da-z\.-]``` +)\.( ```[a-z\.]``` {2,6})$/

In our expression, ```[a-z]``` looks to match any lowercase letter a-z, ```[0-9]``` looks to match any numbers 0-9.  The first bracket expression also includes```[_\.-]``` which broadens the match from a-z and 0-9 to also include the characters ```_``` , ```-```, and ```.```.  Similarly, the second bracket expression matches any digit (using the ```\d``` character class explained below), any lowercase letter a-z, and any either character ```.``` or ```-```. The third bracket expression matches a-z and just the ```.``` character.

### Character Classes
```\``` - **Anything that immediately follows a ```\``` indicates the character should be treated specially, or "escaped"**

```\d``` - **Digit character class escape**

/  ^([a-z0-9_```\.```-]+)@([```\d```a-z```\.````-]+)```\.```([a-z```\.```]{2,6}) ```$``` /<br>

In the bracket expressions above, the ```\``` character is used to escape the ```.``` character so that it is treated literally in the each of the matches.  

The ```\d``` is a special digit character class escape, which matches any digit.  This is equivalent to ```[0-9]```. For example, ```/\d/``` or ```/[0-9]/``` matches "2" in the string "B2 is the suite number."


### Grouping and Capturing
```()``` - **Designates a capturing group**

/^ ```([a-z0-9_\.-]+)``` @ ```([\da-z\.-]+)``` \. ```([a-z\.]{2,6})```   $/<br>

The matching logic inside of ```()``` is called a capturing group, which are used to define sections of matching.  In our example, the first capturing group looks for any sequence containing lowercase letters (a-z), numbers 0-9, ```_```, ```.```, or ```-```.  The second capture group looks for any sequence containing 

### Quantifiers
```+``` - **Designates a match of one or more.**

/^([a-z0-9_\.-] ```+``` )@([\da-z\.-] ```+``` )\.([a-z\.]{2,6})$/ <br>

The first two capture groups are preceeded by the quantifier ```+```, which stipulates that the matches defined in each are met one or more times. 

```{2,6}``` - **Designates a match of at least 2 characters, at most 6 times**

The final capture group contains a more specific quantifier, which requires a match with at least 2 characters defined in the capture group brackets, but no more than 6 times. 


## Other Regex Components 
For reference, here are some definitions of other regex components not found in our "Matching an Email" example: 

### OR Operator

```|``` - **Designates a logical OR in a match**

Example: ```abc|xyz``` matches ```abc``` or ```xyz```.

### Greedy and Lazy Match

```*``` - **Designates a "greedy" match**

With greedy matching, the regex engine will try to match the string as many times as possible.  For example: ```ab*c``` matches ```abc```, ```abbcc```, or ```abcdc```.

```?``` - **Designates a "lazy" match**

With lazy matches, the regex engine will stop matching once the condition is satisfied. For example: ```ab?c``` matches ```ac``` or ```abc```.

### Flags

```i``` - **Designates case insensitivity**
```g``` - **Designates global search**
```m``` - **Designates multi-line search**
```y``` - **Designates sticky search match starting at current position in target string**

Regex flags are used to modify the behavior of an expression. For example: ```/hello/i``` matches ```Hello``` in ```Hello World!```

### Boundaries

```\b``` - **Designates a word boundary** 

A word boundary matches positions where one side is a word character (usually a letter, digit, or underscore) and the other side is a non-word character (the beginning of a string or a space character). For example: ```\bcat\b``` would match ```cat``` in ```a black cat```, ```\bcat``` would match ```cat``` in ```catfish``` and ```cat\b``` would match ```cat``` in ```tomcat```.

### Back-references

```\n``` - **Designates a back-reference (where "n" is a positive integer)**

For example, ```/apple(,)\sorange\1/``` matches ```apple,orange``` in ```apple,orange,cherry,peach```.

Back-references are commands that refer to a previous part of the matched regular expression. 

### Look-ahead and Look-behind

```(?=foo)``` - **Designates a look-ahead
```(?<=foo)``` - **Designates a look-behind

The look-ahead asserts what immediately follows the current position in the string is ```foo```.
The look-behind asserts what immediately precedes the current position in the string is ```foo```.

## Author

Dawson Dohlen is a full-stack coding bootcamp student.
Link to my [GitHub](https://github.com/dawsofd) profile.

