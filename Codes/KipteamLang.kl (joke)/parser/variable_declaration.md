# Declaring variables
This is the code that declares variables, feel free to recommend changes/updates.
```php
$c[Variable declaration]
$if[$optOff[$getTextSplitLength]==2]
  $onlyIf[$checkContains[$splitText[1]; ;0;1;2;3;4;5;6;7;8;9]==false;:x: - Error `variableDeclarationError` invalid variable name (line 1)]
  $var[t1;$splitText[1]]
  $if[$checkContains[$splitText[2];"]$isNumber[$splitText[2]]==falsefalse]
    $onlyIf[$checkContains[$var[vars];$splitText[2]]==true;:x: - Error `variableDeclarationError` invalid value provided, looked for a variable with name **$splitText[2]** 0 found (line 1)]
    $var[t2;$var[$splitText[2]]]
  $else
    $if[$isNumber[$splitText[2]]]
      $var[t2;$splitText[2]]
    $else
      $textSplit[$splitText[2];"]
      $onlyIf[$optOff[$getTextSplitLength]==3;:x: - Error `typeError` invalid string provided (line 1)]
      $var[t2;$splitText[2]]
    $endif
  $endif
  $var[$var[t1];$var[t2]]
  $var[vars;$var[vars]+$var[t1]]
$endif
```
I wouldn't mind some suggestions to make this more compact.
