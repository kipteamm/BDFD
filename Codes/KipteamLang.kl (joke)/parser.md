The following code can only parse one line and a few functions. For more info check `readme.md`.
```php
$nomention

$onlyIf[$message!=;ahum?]

$var[dec;false]
$var[input;$message]

$c[low level replacing]
$var[dec;$checkContains[$var[input]; = "]]
$var[output;$replaceText[$replaceText[$replaceText[$var[input]; = ";\;;-1];";;-1];);;1]] 

$var[a;$replaceText[$replaceText[$checkContains[$var[output];storage];true;storage;1];false;;1]]
$var[a;$replaceText[$replaceText[$var[dec];true;set;1];false;get;1]]

$c[function replacing]
$var[output;$replaceText[$replaceText[$replaceText[$var[output];var ;%{DOL}%var[;-1];storage(;%{DOL}%$var[a];-1];tlocal, ;tUserVar[;-1]\]] 

$var[a;$replaceText[$replaceText[$checkContains[$var[output];.];true;get_attribute;1];false;no_attribute;1]]

$c[Attributes]
$var[output;$replaceText[$replaceText[$replaceText[$replaceText[$var[a];get_attribute;$textSplit[$var[output];.]$splitText[2]$splitText[1]\];-1];value\];%{DOL}%var[;-1];name\];;-1];no_attribute;$var[output];-1]]

$c[Replace unnecessary brackets]
$var[a;$replaceText[$replaceText[$checkContains[$var[output];[];true;0;1];false;1;1]]
$var[output;$replaceText[$replaceText[$var[a];0;$var[output];1];1;$replaceText[$var[output];\];;-1];-1]]
```
So the input would be as following:

**Input:**
```js
$var[input]
``` 
The parsed code that later would be evaluated using `$eval` would be like this:

**Evaluated Code**
```php
$var[output]
```
And evaluating the parsed code would be the this:

**Output**
```php
$replaceText[$replaceText[$var[dec];true;[!\] DEBUG >> Declared Variable;1];false;$eval[$var[output]];1]
```
