# Regular Expressions 1

### Task
Complete the function in the editor below by returning a RegExp object, , that matches any string  that begins and ends with the same vowel. Recall that the English vowels are a, e, i, o, and u.

### Constraints

The length of string  is  .
String  consists of lowercase letters only (i.e., [a-z]).

### Output Format

The function must return a RegExp object that matches any string  beginning with and ending in the same vowel.

### Sample Input 0
```js
bcd
```
### Sample Output 0

```js
false
```

# Dev
```js
'use strict';

process.stdin.resume();
process.stdin.setEncoding('utf-8');

let inputString = '';
let currentLine = 0;

process.stdin.on('data', inputStdin => {
    inputString += inputStdin;
});

process.stdin.on('end', _ => {
    inputString = inputString.trim().split('\n').map(string => {
        return string.trim();
    });

    main();    
});

function readLine() {
    return inputString[currentLine++];
}

function regexVar() {
    /*
     * Declare a RegExp object variable named 're'
     * It must match a string that starts and ends with the same vowel (i.e., {a, e, i, o, u})
     */
    const re = new RegExp('^([aeiou]).*\\1$');

    /*
     * Do not remove the return statement
     */
    return re;
}

```

# Regular Expressions in JavaScript
A Regular Expression, or RegEx, is a pattern used to match character combinations in a string. In JavaScript, regular expressions are also objects. We'll start by giving some basic examples, and then explain the syntax needed to construct and understand RegExes in further detail.

### Creating a Regular Expression
A regular expression consists of a pattern string and, potentially, a flag specifying further detail on how the pattern should be matched. We construct regular expressions by using regular expression literals or RegExp class objects.


### Regular Expression Patterns
We generally construct RegEx patterns using the basic characters we wish to match (e.g., abc), or a combination of basic and special characters (e.g., `ab\*c or (\d+)\.\d\*`).

##### Regular Expression Literal
A regular expression literal is a RegEx pattern encosed within forward slashes:
```js
const re = /ab + c/;
```
> This RegEx above matches the character a, followed by one or more instances of the character b, followed by the character c.

##### RegExp Objects
We can write a regular expression string and pass it as an argument toi the RegExp construct:
```js
const re = new RegExp('ab+c');

// result same
const reg = /(.).*\1/;
const reg = new RegExp('(.).*\1' );
asdlp;fjlask;dkfjkxptmxm xptmxm vka vmfptmx dkasdflkjsdaflkjasdflklsdjflkasjdf
```

### Flags
To create a RegExp object, we use this syntax:
```js
new RegExp(pattern[, flags])
```

To create a regular expression literal, we use this syntax:
```js
/pattern/flags
```

If specified, flags can have any combination of the following values:
* $g$: global match.
* $i$: ignore case.
* $m$: multiline. Trates beginning(^) and end ($) characters as working over multiple lines.
* $u$: unicode. Treat pattern as a sequence of unicode code points.
* $y$: sticky. Matches only from the idex indicated by the lastIndex porperty of this regular expression in the target string.

### Special Characters in Regular Expressions
* Character Classes
* Character Sets
* Alteration
* Boundaries
* Grouping and back references
* Quantifiers
* Assertions

### Character Classes
This is not a class in the traditional sense, but rather a term that refers to a set of one or more characters that can be used to match a single character from some input string. Here are the basic forms:

* Enclosed within square brackets. Specify the what you'd like your expression to match within square brackets; for example, [a-f] will match any lowercase a through f character.
* Predefined: These consist of a backslash character (\) followed by a letter. The table below shows some predefined character classes and the characters they match.

|Character | Matches |
|:--:|:--|
| ^ |	Matches beginning of input. If the multiline flag is set to true, also matches immediately after a line break character. |
| $	|Matches end of input. If the multiline flag is set to true, also matches immediately before a line break character. |
| \b |	A zero-width word boundary, such as between a letter and a space. |
| \B |	Matches a zero-width non-word boundary, such as between two letters or between two spaces. |


##### Grouping and back references
* (a): Matches a and remembers the match. These are called capturing groups.

* (?:a): Matches a but does not remember the match. These are called non-capturing groups.

* \n: Here n is a positive integer. A back reference to the last substring matching the n parenthetical in the regular expression.

##### Quantifiers
* a*: Matches the preceding item a, 0 or more times.

* a+: Matches the preceding item a, 1 or more times.

* a?: Matches the preceding item a, 0 or 1 time.

* a{n}: Here n is a positive integer. Matches exactly n occurrences of the preceding item a.

* a{n, }: Here n is a positive integer. Matches at least n occurrences of the preceding item a.

* a{n, m}: Here n and m are positive integers. Matches at least n and at most m occurrences of the preceding item a.

##### Assertions
* a(?=b): Matches a only if a is followed by b.

* a(?!b): Matches a only if a is not followed by b.

##### Working with Regular Expressions
Regular expressions are used with the RegExp methods:

* test: The test() method executes a search for a match between a regular expression and a specified string. Returns true or false
* exec: The exec() method executes a search for a match in a specified string. Returns a result array or null.

and with the String methods:

* match: The match() method retrieves the matches when matching a string against a regular expression.
* search: The search() method executes a search for a match between a regular expression and this String object. If successful, search() returns the index of the first match of the regular expression inside the string. Otherwise, it returns -1
* split: The split() method splits a String object into an array of strings by separating the string into substrings. Separator specifies the character(s) to use for separating the string. The separator is treated as a string or a regular expression. If separator is omitted, the array returned contains one element consisting of the entire string. If separator is an empty string, str is converted to an array of characters.
* replace:The replace(pattern, replacement) method returns a new string where some (or all) occurrences of a matched  have been replaced with a  substring.
  + pattern: This value can be a string or a RegExp object to match against the calling string.
  + replacement: This value can be a substring to replace the match with, or it can be a function to invoke that generates the replacement substring.
