# KipteamLang, Kipteam-Lang or KPL for short
A custom language that is parsed by and to BDFD code.

# Variables
(Temporary) variables, basically, variables that don't get stored for long term use work as following.

**Setting:**
```js
var test = "temp"
```

**Getting**
```js
test.value 
// returns "temp" (as declared above)
```

**And name getting** _unique feature_
```js
test.name
// returns "test" (as a string)
```

Long term variables/stored variables have different versions, local, global and server. All have their own features.
This table shows their features.
|               | local | global-user | global | server |
|---------------|-------|-------------|--------|--------|
| user-unique   |✅     |✅          | ❌     | ❌    |
| server-unique |✅     | ❌         | ❌     | ✅    |

**Setting**
```js
storage(local, test) = "temp"
// set local variable 'test' to "temp"
```
You can replace the keyword `local` with one of the following
- local -> for local variables
- global_user -> for global-user variables
- global -> for global variables
- server -> for server variables

**[!] keep in mind that only `local` is functional yet!**

**Getting**
```js
storage(local, test)
// returns "temp" (as declared above)
```
