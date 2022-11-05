# Line Splitter
This code splits an input into lines witch individually get run through the parser.  
It makes use of `$repeatMessage` which is is set to repeat `$getTextSplitLength` times (this functions returns the amount of lines).  
Using a variable `$var[c]` to which 1 gets added every time we ""loop"" we get an `$splitText[$var[c]]` and than add 1 to `$var[c]`.  
The following code will run every line separately through the old parser (which is bad and getting a revamp). 

**Code**
```php
$nomention

$var[t;$replaceText[$message;
;@;-1]]

$textSplit[$var[t];@]

$var[c;1]

$eval[$repeatMessage[$getTextSplitLength;%{DOL}%textSplit[%{DOL}%var[t\]\;@\]

%{DOL}%var[dec\;false\]
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
%{DOL}%var[final_code\;%{DOL}%var[final_code\] %{DOL}%replaceText[%{DOL}%replaceText[%{DOL}%var[a\]\;0\;%{DOL}%var[output\]\;1\]\;1\;%{DOL}%replaceText[%{DOL}%var[output\]\;\\]\;\;-1\]\;-1\]\]]]

$var[final_code]
```
