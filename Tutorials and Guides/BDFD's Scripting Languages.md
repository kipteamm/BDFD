Scripting or coding languages.
Bot Designer For Discord has 3, oh well, 4 of then.
Quick explenation, if I say "parsing" I refer to the way that your code gets interpretated so that the bot can execute it.
So let's get started. 

BDScript 1 or Bot Designer Script 1 was the very first language ever added to the app.
However, the way that it would parse your could would quickly result in a new langauge.
This becuase BDScript 1 makes use of a "priority-list". 
Let's say that list would be structured as following:
```php
$function_1[]
$function_2[]
$function_3[]
```
It will read your code and firstly parse
```php
$function_1[]
```
Before getting to the next function on the list. 
This method will work in some cases where to code doesn't get to complicated. 
Like this one:
```php
$function_1[]
$function_3[]
$function_2[]
```
It would just follow the order of it's list and no issues would occur. 
But what if we have the following code
```php
$function_1[$function_2[]]
$function_3[]
```
It would first parse $funcion_1[] which would result in an error as there is an unparsed function inside of it. 
So the developers came with a solution.

Introducing BDScript Unstable.
A language that wouldn't make use of this "priority-list".
Instead it would read your code as a human would.
From bottom to top and right to left. 
However this isn't always suiting and still, just less common, it had it's own issues. 

So there, on the 16th of June, 2021 the developers gave us BDScript 2. 
A language that would read and interpretate your code from left to right and bottom to top. 
That concludes all the Bot Designer For Discord scripting languages. 

Oh yeah! I forgot one...
There also is ES5 an old version of JavaScript dating from around the 18 hundreds. 
A language that no one uses, no one should use and no one ever will use.