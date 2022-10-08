# Line Splitter
The goal is to split an input into lines witch individually will be run through the parser.  
So I have the following code, which _partially_ works. It does what it needs to do, with the downside that it depends on `$repeatMessage[]` which with the character limit of 4000 is having a hard time processing 4764. Althus it only parses the first line.  
If you have an idea feel free to make a pr or DM me on discord (@kipteam#3048)

**Input**
```js
var test = "temp"
test.value
test.name
```

**Code**
```php
$nomention

$var[t;$replaceText[$message;
;@;-1]]

$textSplit[$var[t];@]

$var[c;1]

$eval[$repeatMessage[$getTextSplitLength;%{DOL}%var[dec\;false\]
%{DOL}%var[input\;%{DOL}%splitText[%{DOL}%var[c\]\]\]

%{DOL}%var[c\;%{DOL}%sum[%{DOL}%var[c\]\;1\]\]

%{DOL}%var[dec\;%{DOL}%checkContains[%{DOL}%var[input\]\; = "\]\]
%{DOL}%var[output\;%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%var[input\]\; = "\;%{DOL}%toLowercase[\;\]\;-1\]\;"\;\;-1\]\;)\;\;1\]\] 

%{DOL}%var[a\;%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%checkContains[%{DOL}%var[output\]\;storage\]\;true\;storage\;1\]\;false\;\;1\]\]
%{DOL}%var[a\;%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%var[dec\]\;true\;set\;1\]\;false\;get\;1\]\]

%{DOL}%var[output\;%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%var[output\]\;var \;%{DOL}%toLowercase[$\]var[\;-1\]\;storage(\;%{DOL}%toLowercase[$\]%{DOL}%var[a\]\;-1\]\;tlocal, \;tUserVar[\;-1\]\\]\] 

%{DOL}%var[a\;%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%checkContains[%{DOL}%var[output\]\;.\]\;true\;get_attribute\;1\]\;false\;no_attribute\;1\]\]

%{DOL}%var[output\;%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%var[a\]\;get_attribute\;%{DOL}%textSplit[%{DOL}%var[output\]\;.\]%{DOL}%splitText[2\]%{DOL}%splitText[1\]\\]\;-1\]\;value\\]\;%{DOL}%toLowercase[$\]var[\;-1\]\;name\\]\;\;-1\]\;no_attribute\;%{DOL}%var[output\]\;-1\]\]

%{DOL}%var[a\;%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%checkContains[%{DOL}%var[output\]\;[\]\;true\;0\;1\]\;false\;1\;1\]\]
%{DOL}%var[output\;%{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%var[a\]\;0\;%{DOL}%var[output\]\;1\]\;1\;%{DOL}%replaceText[%{DOL}%var[output\]\;\\]\;\;-1\]\;-1\]\]

%{DOL}%var[output\]]]
```
