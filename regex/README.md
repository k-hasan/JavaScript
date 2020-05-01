# Regular Expresion 
#### Rules
```regexp
1. '/' Start and end end symbol
2. It is Case Sensitive
3. 'i' flag for case insensitive exp: /babe/i
4. 'g' flag for gloval search exp: /baba/g
5. 'm' flag for multi line search exp: /.../m
6. | for or condition exp: /book|black/
7. () for group exp: /b(ook|lack)/
8. '\' for scape spasial character
9. [a-z] this is character class, '-' use for range
10. \w, \d, \s, \W, \D, \S thes 6 are character class
11. /[A-Za-z0-9_]/ alternative \w
12. \W every thing(Symbol, etc) without /[A-Za-z0-9_]/
13. \d for digit (0-9), \D every thing without (0-9)
14. \s for space ( ), \S every thing without Space
15. "abba" for /ab{2}a/
16. "abbbbba" for /ab{2,5}a/
17. "abbbbbbbbbbbbba" for /ab{2,}a/
18. "abbbbbbbbbbbbba" for /ab{0,}a/ instead of /ab*a/ একটা নাও থাকতে পারে থাকতেও পারে আবার একাদিক থাকতে পারে 
19. "abbbbbbbbbbbbba" for /ab{1,}a/ instead of /ab+a/ কম পক্ষে একটা থাকবে  আবার একাদিক থাকতে পারে 
20. "shahin" or "sahin" for /sh{0, 1}ahin/ instead of /sh?ahin/ একটা থাকবে আবার নাও থাকতে পারে 
21. "sem" for /se[^x]/ নির্দিষ্ট character ছাড়া other যেকোনো character হতে পারে 
22. ^শুরু  করা,  $ শেষ করা 
```
#### Use
```composer log
Two type Uses for regexp in javascript

1. Constractor
2. Literal


1. Constractor
var r = RegExp('^abc+$', 'i');

var s = "abccc";
console.log(r.test(s)); //true

2. Literal
var r = /abc+/i
var s = "abc"
console.log(r.exec(s)); //["abc"]

***Functions
`test` dile true or false return kore
`exec` dile matched array return kore
`replace` dile matched portion change hobe
```