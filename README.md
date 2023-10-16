# Regex 101

Welcome to my regex 101. This is a summary of the basic components of Regex.

## Summary

Regex is a simple set of components that, when used together, can give us the ability to match complicated expressions.  Below, I'll try to explain each component, and then tie it all together by applying them to a more complicated expression:

 /^#?([a-f0-9]{6}|[a-f0-9]{3})$/

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
- [Use Case](#use-case)

## Regex Components

### Anchors
Anchors are denoted by the ^ and $ symbols, and will match if the searched characters exist at the beginning or end of an expression, respectively.

The below would match with the first and last words of the above:

/^Anchors/g

/respectively\\.$/g

### Quantifiers
Quantifiers can help you control how many of a characters you want to match with, and how strictly you are searching.

?  will match if the preceding character if it exists. The character preceding the ? is optional.

\* will match zero or more of the preceding character.

. will match anything except for a new line.

\+ will match one or more of the preceding character.

{min,max} will match anything with the preceding character repeating no less than the min number of times, but no more than the max number of times. Omit 'max' to set your max to infinty.

{n} will match when the preceding character repeat exactly n times. If an experession contains the character repeating more than n times, it will match on the first n characters in that expression. Examples of this: /s{2}/g  will find only the first 2 esses in the expression "sss"

### OR Operator

| is the 'or' operator.  This will match with either the preceding or the following character.

Example: /(1|2){2}/g  will match with each of the following:

11\
12\
21\
22

### Character Classes
[a-z] will match with all lower case letters.

[A-Z] will match with all upper case letters.

[0-9] will match with all numbers.

You can reduce the range by changing the either the left or right hand side(s) of the range.

You can string these ranges togethers, such as [A-Za-z0-9] which will match all letters and numbers.

Use ^ inside square braces for a negative match. [^A-Za-z0-9] will find all characters that are NOT letters or numbers. Useful for finding special characters.

### Flags

Flags can be used to specify how to search through a block of text. Highlighting, strange cases, and underlining used for explanation purposes in the example.

end your regex with: 

g to perform a global `search`\
i for a case insensitive seArch\
m for a multiline <ins>search</ins>

Example:

/search$/g   would match with the underlined "search" above.
/search$/gm  would match with both the underlined AND the highlighted "search" above.
/search$/gmi would match with all instances of "search" above.

### Grouping and Capturing

You can use parenthesis to search for a grouping of characters.

Example:

/(se){2}/g would match with "sese"

### Bracket Expressions

Entering a string of individual characters into square braces will look for individual instances of each of those characters. In other words,

/[abc]/g is equivalent to /[a-c]/g

and

/[12][12]/g is equivalent to /(1|2){2}/g

### Greedy and Lazy Match

<ins><span style="color:yellow">"Greedy"</span> will match the longest instance of the searched string, and <span style="color:yellow">"lazy"</span></ins> will match the shortest. 

Example:

/".+"/g will match with the underlined text above. This will look for a quote, then look for .+ (which is the rest of the paragraph). Then, it will look backward from the last character in the paragraph to find another quote.

/".+?"/g will match with the yellow text above. This will look for a quote, then look forward from the quote to find another character followed by a quote.

### Boundaries

\b can be used to match with words that begin with whatever follows.

b\ can be used to match with words that end with whatever precedes.

Examples:

/\bhap\g will match "hap" in "happiness"

/hap\b/g will match "mihap"

/\bhap\b/g will match neither "happiness" nor "mishap" but will match "hap"

### Back-references

\1 can be used after a group to look for it occuring twice.

Example text:

<div>This is a div</div>

Example regex expression:

/(<.?div>)\1*/g  would match <div> and </div>

### Look-ahead and Look-behind

?<= can be used to find whatever follows the regex expression, and then match characters in searched text that follow.

?= can be used to find whatever follows the regex expression, and then match characters in searched text that precede.

Examples:

(?<=the). will match single characters that have a "the" before it.

.(?=the) will match single characters that have a "the" after it.

### Use case

Let's now look at the following expression, and try to understand how it works:

 /^#?([a-f0-9]{6}|[a-f0-9]{3})$/

^ - this is looking for the expression at the beggining of a string or line.

$ - this is looking for the expression at the end of a string or line.

If we are looking for where an expression appears at the beggining of a string and that same instance appears at the end of a string, we're basically looking for where it's making up the entire content of the string.

\#? - If there is a hashtag in front of our text, we'll include it in our match.

[a-f0-9]{6}|[a-f0-9]{3}  - this is looking for exactly 6 characters that contain any lowercase letters a,b,c,d,e,f, or any numbers between 0 and 9 inclusive OR exactly 3 characters that contain any lowercase letters a,b,c,d,e,f, or any numbers between 0 and 9 inclusive.

### Author

Michael Lee is a student developer.
Github: https://github.com/leex3683
