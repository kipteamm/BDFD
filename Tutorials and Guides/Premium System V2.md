Important notes:
- `<PREFIX>` should be replaced with your prefix of choice.
- `()` round brackets represent OPTIONAL arguments. 
- `[]` square brackets represent REQUIRED arguments.
- Time is formatted like this:
  - `1y` is 1 year
  - `1w` is 1 week
  - `1d` is 1 day
  - `1h` is 1 hour
  - `1m` is 1 minute

Lets start of with the `<PREFIX>givecode` command.
Important things to know. 
When sending a premium code to yourself the usage of the command is as following `<PREFIX>givecode (time)`.
Example usage would be:
```php
+givecode 1y
```
[give yourself with time](https://github.com/ToroEen/BDFD/blob/1dc5bff78c2fc0a98c1b474baecebcb7f0b46d40/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/give_yourself_with_time.png)
When sending a premium code to someone else the usage of the command is as following `<PREFIX>givecode [user] (time)`.
```php
+givecode @ToroEen 1y
```
[give someone else with time](https://github.com/ToroEen/BDFD/blob/1dc5bff78c2fc0a98c1b474baecebcb7f0b46d40/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/gife_random_with_time.png)
If you want to send a never expiring code you can leave the `(time)` argument empty. 
```php
$nomention
$allowMention

$enableDecimals[yes]

$onlyIf[$authorID==675316333780533268;You are missing permissions to use this command!]
$onlyIf[$userExists[$findUser[$message[1]]]==true;The mentioned user does not exist!]
$onlyIf[$isBot[$findUser[$message[1]]]==false;You can't give premium to a bot!]
$onlyIf[$isUserDMEnabled[$findUser[$message[1]]]==true;This user has their DM disabled and therefore cannot get their code delivered!]

$var[is_author;$replaceText[$replaceText[$checkCondition[$authorID==$findUser[$message[1]]];true;_0;1];false;_1;1]]

$var[user;$replaceText[$replaceText[$var[is_author];_0;$authorID;1];_1;$findUser[$message[1]];1]]
$var[date;$replaceText[$message[$sum[$replaceText[$var[is_author];_;;-1];1]]; ;;-1]]

$if[$var[date]!=]
  $var[time;$calculate[$replaceText[$replaceText[$replaceText[$replaceText[$replaceText[$var[date];y;*31536000;-1];w;*604800;-1];d;*86400;-1];h;*3600;-1];m;*60;-1]]]
$else
  $var[time;0]
$endif

$var[code;$replaceText[$replaceText[$randomString[10]$replaceText[$calculate[$date];2;T;-1];+;K;-1];-;k;-1]]

$setVar[premiumcodes;$getVar[premiumcodes;$var[user]]$var[code]-$var[time]+;$var[user]]

$sendMessage[Successfully send **$username[$var[user]]#$discriminator[$var[user]]** a premiumcode `($var[code])` $replaceText[$replaceText[$checkCondition[$var[date]==];true;;-1];false;worthy of `$replaceText[$replaceText[$replaceText[$replaceText[$replaceText[$var[date];y; year(s);-1];w; week(s);-1];d; day(s);-1];h; houra(s);-1];m; minute(s);-1]`;-1]]

You got a premiumcode `($var[code])` $replaceText[$replaceText[$checkCondition[$var[date]==];true;;-1];false;of `$replaceText[$replaceText[$replaceText[$replaceText[$replaceText[$var[date];y; year(s);-1];w; week(s);-1];d; day(s);-1];h; houra(s);-1];m; minute(s);-1]`;-1]

$dm[$var[user]]
```

NOT DONE, MORE COMING SOON
