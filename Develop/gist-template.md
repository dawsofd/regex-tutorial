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

/  ^([a-z0-9_```\.```-]+)@([```\d```a-z```\.````-]+)```\.````([a-z```\.```]{2,6}) ```$``` /<br>

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

```{2,6}``` - **Designates a match of at least 2 characters, at most 6 times

The final capture group contains a more specific quantifier, which requires a match with at least 2 characters defined in the capture group brackets, but no more than 6 times. 


## Other Regex Components 
For reference, here are some definitions of other regex components not found in our "Matching an Email" example: 

### OR Operator

```|``` - **Designates a logical OR in a match

Example: ```abc|xyz``` matches ```abc``` or ```xyz```

### Greedy and Lazy Match

```*``` - **Designates a "greedy" match.

Example: ```ab*c``` matches ```abc```, ```abbcc```, or ```abcdc```

```?``` - **Designates a "lazy" match.

Example:

Example: 

### Flags

### Boundaries

### Back-references

### Look-ahead and Look-behind

## Author

Dawson Dohlen
![Link to Github Profile](https://www.github.com/dawsofd)

