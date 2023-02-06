# David Mancini's Regex Tutorial 


Regex stands for Regular Expression, and despite it's rather odd look, is a term for a type of quite useful sequences of characters that defines a specific search pattern. They can be used to find certain patterns of characters within a string, or to find and replace a character or sequence of characters within a string. This tutorial will explain the componats of a Regex sequence.


## Summary


We will  be exploring how to use Regex to match a URL. we'll be looking at Anchors, Quantifiers, Groups, OR Operators, Classes, and Greedy/Lazy Matching.

````
/^(https?:\/\/)?([\da-z\.-]+)\.([a-z\.]{2,6})([\/\w \.-]*)*\/?$/
````

## Table of Contents

- [Anchors](#anchors)
- [Grouping and Capturing](#grouping-and-capturing)
- [Quantifiers](#quantifiers)
- [OR Operator](#or-operator)
- [Character Classes](#character-classes)
- [Greedy and Lazy Match](#greedy-and-lazy-match)


## Regex Components
This sequence seems like nonsense, but if we break it down into it's components, we can get a better understanding of how it works.
### Anchors
The anchors are the first part we'll look at. the sequence begins and ends with the anchors, `^` at the begining, and `$` at the end. using these, you are calling for an exact string match with whats between them. used alone, `^` matches just the starting characters, and conversely, `$` alone matches the end. using them together, we are asking for exactly what's in between, no more and no less.

### Grouping and Capturing
inside the anchors is where the real fun begins. inside paretheses `()` are groups of regex, each one meaning something diffrent;
`(https?:\/\/)` is the initail `https` component.
`([\da-z\.-]+0\`is the domain name, such as www.github
`([a-z\.]{2,6}` is the top level domain, such as .com
`([\/\w \.-]*)*` is the file path

### Quantifiers
now we'll talk about the Quantifiers! you maay have seen some of the groups end with a `*` or with a `?`, which are known as quantifiers. these are used to define how many times optionaly the expression can be matched, with `?` being once and `*` being multiple times. lets break that down. take a look at this;
`https?:\/\/)?`
there are two `?` here. we are using this to look for either `http://` OR `https://`, so we can have only one `s`, which is optional. in fact, it is entirely valid that the URL beigns with `www.`, so it could be nither. so both `?` are saying look for those exact instances only once. now lets look at this;
`([\/\w \.-]*)*`
what this is saying any number of the characters there will be found in this part.
theres one more quantifier, the `{}` whice defines a range of how many matches can be found. so in 
`([a-z\.]{2,6})`, its sayin the domian consists of 2 to six characters.

### OR Operator\Bracket Expressions
an OR Operator we use above is `[]`. what this does is match for any classes or characters inside the brackets. in our sequence, you can see the use of brackets in `[\da-z\.-]`, so it will match digits from `\d`, and\or and character between a and z thanks to `a-z`, and/or any period, as seen in `\.` and /or any use of a dash, from `-`.

### Character Classes
the important Character Classes here are `\d` and `\w`. `\d` looks for any digit, and `\w` looks for any alphanumeric character. in the above expresion, you can see `\d` in the domain section, `([\da-z\.-]+)\`, its asking to look for any digit, (as well any letter a-z). `\w` is used in the file path, `([\/\w \.-]*)*`, to look for any type of alphanumeric character at all.


### Greedy and Lazy Match
Greedy Matches will make as many matches as they possibly can. for example, in `([\da-z\.-]+)`, the `+` means look for as many things that match as can be, making it greedy. Lazy matches mean match as few times as possible, so stop after thr first one. as stated above, `?` will look for matches only once, making it lazy.

## Author
This guide was made by David Mancini. find my github at https://github.com/Dmancini87
