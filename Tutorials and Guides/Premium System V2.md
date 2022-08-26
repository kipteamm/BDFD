# Summary
A set of codes that allow you to limit codes for servers with your premium subscription activated.
You can gift codes that can expire, activate a server with a code of choice. 
Log everything that happens and even deactivate a server if needed!


# Important notes
- Make sure to put all codes in `BDScript 2`
- `<PREFIX>` should be replaced with your prefix of choice.
- `()` round brackets represent OPTIONAL arguments. 
- `[]` square brackets represent REQUIRED arguments.
- Time is formatted like this:
  - `1y` is 1 year
  - `1w` is 1 week
  - `1d` is 1 day
  - `1h` is 1 hour
  - `1m` is 1 minute


# Variables
All these work with 2 variables only. 
The first variables is called `premium` with a default value of `false`.
The second variable is `premiumcodes` with a default value of nothing.
![premium variables](https://github.com/ToroEen/BDFD/blob/7e09ceb3c613cd246a208d2f7784d2d33fd0cecc/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/premium_variables.png)


# Command 1
Lets start of with the `<PREFIX>givecode` command.
Important things to know. 
When sending a premium code to yourself the usage of the command is as following `<PREFIX>givecode (time)`.
Example usage would be:
```php
+givecode 1y
```
![give yourself with time](https://github.com/ToroEen/BDFD/blob/1dc5bff78c2fc0a98c1b474baecebcb7f0b46d40/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/give_yourself_with_time.png)

When sending a premium code to someone else the usage of the command is as following `<PREFIX>givecode [user] (time)`.
```php
+givecode @ToroEen 1y
```
![give someone else with time](https://github.com/ToroEen/BDFD/blob/1dc5bff78c2fc0a98c1b474baecebcb7f0b46d40/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/gife_random_with_time.png)

If you want to send a never expiring code you can leave the `(time)` argument empty.  
The following line is the one that says who can send premium codes. Make sure to replace `your_user_id` with your userID.
```php
$onlyIf[$authorID==your_user_id;You are missing permissions to use this command!]
```
If you want to allow multiple users replace it with the following [function](https://nilpointer-software.github.io/bdfd-wiki/bdscript/onlyForIDs.html). Don't forget to fill in actual userIDs.
```php
$onlyForIDs[user_id_1;user_id_1;...;You are missing permissions to use this command!]
```
This is the full code:
```php
$nomention
$allowMention

$enableDecimals[yes]

$onlyIf[$authorID==your_user_id;You are missing permissions to use this command!]
$onlyIf[$userExists[$findUser[$message[1]]]==true;The mentioned user does not exist!]
$onlyIf[$isBot[$findUser[$message[1]]]==false;You can't give premium to a bot!]
$onlyIf[$isUserDMEnabled[$findUser[$message[1]]]==true;This user has their DM disabled and therefore cannot get their code delivered!]

$var[is_author;$replaceText[$checkContains[$message[1];y;w;d;h;m];false;$checkCondition[$findUser[$message[1]]==$authorID];1]]
$var[user;$replaceText[$replaceText[$checkCondition[$var[is_author]==true];true;$authorID;1];false;$findUser[$message[1]];1]]
$var[date;$replaceText[$replaceText[$checkContains[$message[1];y;w;d;h;m];true;$message[1];1];false;$message[2];1]]

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


# Command 2
Second of all is a user's inventory where all gifted premium codes get stored.  
The trigger for this code is as following `<PREFIX>inventory (@user)`.  
So the usage would be:

![Inventory with user](https://github.com/ToroEen/BDFD/blob/504ced6f75414b20c5c8bb693a8ec7f3e041d12c/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/inventory_with_user.png)
```php
$nomention

$textSplit[$getVar[premiumcodes;$mentioned[1;yes]];+]

$var[n;1]

$title[$username[$mentioned[1;yes]]'s inventory]
$description[**1.** $replaceText[$eval[$replaceText[`$replaceText[$replaceText[$getVar[premiumcodes;$mentioned[1;yes]];+;\]:F>
**%{DOL}%var[n\;%{DOL}%sum[%{DOL}%var[n\]\;1\]\]%{DOL}%var[n\].** `;-1];-;` if activated now, active till <t:%{DOL}%sum[%{DOL}%getTimestamp\;;-1];if activated now, active till <t:%{DOL}%sum[%{DOL}%getTimestamp\;0\]:F>;active forever;-1]];**$var[n].** `;;-1]]
$footer[+activate (number)]
```


# Command 3
Now the most important code, activating a premium-code.
This command has the following trigger `<PREFIX>activate (number)`. When `(number)` is left emtpy, the first code from the user's inventory will be used.
The number represents the one shown in the `<PREFIX>inventory (@user)` command.  
So the complete usage would be:

![activated number 1](https://github.com/ToroEen/BDFD/blob/bbea7d851c813b7ff4a22f3d63c2c66b863f5411/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/activated_number_one.png)

This command comes with an extra channel that allows you to log all activated premium codes.  
The last line of this code is as following:
```php
$c[Replace this with the log code if you want to use it, otherwise just remove it.]
```
So if you want this logging feature, replace the line mentioned earlier with the following piece of code.
Make sure to replace `your_log_channel_id_here` with your log channel's channel ID.
```php
$channelSendMessage[your_log_channel_id_here;**$username#$discriminator[]** `($authorID)` activated premium $replaceText[$replaceText[$checkCondition[$var[time]==0];true;;-1];false;till <t:$var[time]:F> ;-1]in **$serverName[$guildID]** `($guildID)`]
```
The logging code in use would look like this:
![activation logged](https://github.com/ToroEen/BDFD/blob/8a344d671ef3927904db514778a2262e984113cd/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/activation_logged.png)
This is the whole code:
```php
$nomention

$onlyIf[$getServerVar[premium]==false;This server already has premium activated!]
$onlyIf[$getVar[premiumcodes;$authorID]!=;You don't have any premium codes!]

$textSplit[$getVar[premiumcodes;$authorID];+]

$if[$message!=]
  $onlyIf[$isNumber[$message]==true;That is an invalid number!]
  $onlyIf[$message<=$sub[$getTextSplitLength;1];That is an invalid number!]
  
  $var[number;$message]
$else
  $var[number;1]
$endif

$var[premiumcode;$splitText[$var[number]]]

$textSplit[$var[premiumcode];-]

$var[time;$replaceText[$replaceText[$checkCondition[$optOff[$splitText[2]]==0];true;0;-1];false;$sum[$getTimestamp;$optOff[$splitText[2]]];-1]]

$setServerVar[premium;$var[time]]
$setVar[premiumcodes;$replaceText[$getVar[premiumcodes;$authorID];$var[premiumcode]+;;-1];$authorID]

<@$authorID> activated premium in this server$replaceText[$replaceText[$checkCondition[$var[time]==0];true;!;-1];false; till <t:$var[time]:F>!;-1] Don't forget to thank them!

$c[Replace this with the log code if you want to use it, otherwise just remove it.]
```


# Command 4
Check your server's premium status.  
Trigger is as following, `<PREFIX>status`.  
It would give a response as shown below.

![status](https://github.com/ToroEen/BDFD/blob/b9b86bca307b208a140503ecd9051e8d1e34c5d9/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/status.png)
```php
$nomention

$if[$getServerVar[premium]!=false]
  This server has an active premium subscription$replaceText[$replaceText[$checkCondition[$getServerVar[premium]==0];true;!;-1];false; till <t:$getServerVar[premium]:F>;-1]
$else
  This server currently has no premium subscription.
$endif
```


# Command 5
You can also as an owner deactivate the premium in a server.
The trigger of that command would be `<PREFIX>deactivate (server)`. When left blank the current server will get deactivated.
The command would something like this.
![deactivate guild](https://github.com/ToroEen/BDFD/blob/9902a67501ec816ac4c9491392642b43191c4e6c/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/deactivate_guild.png)

Also this code comes with an optional logging feature.
The last line of this code is as following:
```php
$c[Replace this with the log code if you want to use it, otherwise just remove it.]
```
So if you want this logging feature, replace the line mentioned earlier with the following piece of code.
Make sure to replace `your_log_channel_id_here` with your log channel's channel ID.
```php
$channelSendMessage[920020324806963230;Premium got deactivated in **$serverName[$var[guild]]**!]
```
The logging code in use would look like this:

![logged deactivation](https://github.com/ToroEen/BDFD/blob/4bba1ab9f2f80d54f747881a3aa0749de9f73e4f/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/logged_deactivation.png)

This is the whole code:
```php
$nomention

$var[guild;$replaceText[$replaceText[$checkCondition[$message[1]==];true;$guildID;1];false;$message[1];1]]

$onlyIf[$guildExists[$var[guild]]==true;Invalid guild ID provided!]
$onlyIf[$authorID==675316333780533268;You are missing permissions to use this command!]
$onlyIf[$getServerVar[premium;$var[guild]]!=false;This server has no active premium subscription running!]

$setServerVar[premium;false]

Successfully deactivated premium in **$serverName[$var[guild]]**!

$c[Replace this with the log code if you want to use it, otherwise just remove it.]
```


# Make a code premium only (no embed error)
If you want a command to be premium only and the error message to not be an embed add this at the top of your code just underneath `$nomention`.
An example of a premium limited code error:

![no command error](https://github.com/ToroEen/BDFD/blob/fd7d5f991585a62c6f69147fb261654b5416d64e/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/no_embed_error.png)
```php
$setServerVar[premium;$replaceText[$replaceText[$checkCondition[$getServerVar[premium]==0];false;$checkCondition[$replaceText[$getServerVar[premium];false;0;1]>$getTimestamp];1];true;$getServerVar[premium];1]]

$onlyIf[$getServerVar[premium]!=false;This server does not have an active premium subscription!]
```

# Make a code premium only (embed erorr)
If you want a command to be premium only and the error message to be an embed set your code up as following.
Replace the following bit with your premium limited code.
```php
$c[Your premium code here]
```
An example of a premium limited code error:

![no embed error](https://github.com/ToroEen/BDFD/blob/fd7d5f991585a62c6f69147fb261654b5416d64e/Tutorials%20and%20Guides/Tutorials%20and%20Guides%20Assets/no_command_error.png)
```php
$nomention

$setServerVar[premium;$replaceText[$replaceText[$checkCondition[$getServerVar[premium]==0];false;$checkCondition[$replaceText[$getServerVar[premium];false;0;1]>$getTimestamp];1];true;$getServerVar[premium];1]]

$if[$getServerVar[premium]!=false]
  $c[Your premium code here]
$else
  $description[This server does not have an active premium subscription!]
$endif
```
