- --
[the vidoe](https://www.youtube.com/watch?v=4ygaA_y1wvQ)

This is a reference material for the video i am watching.

First of all you'll need to start all you'r bash scripts with a shebang, Like this.
```bash
#!/usr/bin/env bash
```

Its recommended to use this shebang because, it may not run other machines with a different shebang.

# vars
you define a variable like this in bash.
```bash
name="assi-45"
```


Now on how to print.
```bash
echo "hello $name"
```

This will print `hello {name}`

Now if you wan't to pass a default value into the echo command (its just a linux command) You'll need to do this

```bash
echo "hello ${name:-"veronica"}"
```

But this a one time thing. If you wan't it to become a reusable value across your script it has to be writen like this.

```bash
echo "hello ${name:="veronica"}"
```

Now variable name is _veronica_.

# sub shells
A sub shell is a child process created by the shell to execute commands in an isolated environment. Variables, options, and the working directory inside a subshell do not affect the parent shell.

Here is an example
```bash
(cd ..; pwd)
```

But sub shell are most used for **command substitution**. -> `$()`

Here is an example
```bash
var=$(pwd)
```

it basicly just allows you to use the text/output of a command in a other command.

you also have **command substitution**.  -> `<()`
Its like the one above except its not treated as plain text but a file.

And the last one is arithmetic expansion. -> $(())
here you can do all kinds of math stuff.

# command line args
![[2025-12-10_10-05-07_3xDec.png]] **In the script**
![[2025-12-10_10-05-31_3xDec.png]] 
# conditional logic
They look like this.
```bash
if [[ condition ]]; then
	execution
elif [[ condition]]; then
	execution
else
	execution
fi
```
And that's how they look.

# exit code
Exit code or like **true** or **false** in other languages 
**1** -> succes
anything else -> failure

With this you can run commands as your conditonals.

# conditionals
![[2025-12-10_10-20-07_3xDec.png]]

**_Note!_**; Put spaces every like above or else you'll have an error

![[2025-12-10_10-23-54_3xDec.png]]
![[2025-12-10_10-23-45_3xDec.png]]

# strict mode
![[2025-12-10_11-19-26_3xDec.png]]
This will set strict mode in bash.
```bash 
set -euo pipefail
```

At this point you probably know 80 % of the stuff your gana use day to day.

# arrays
This works like in any other language but the syntax is a bit strange.
![[2025-12-10_11-24-32_3xDec.png]]

# for loops
basic for loop
```bash
array=(1,2,3,4)
for item in array do
	echo $item
do
```
![[2025-12-10_11-27-55_3xDec.png]]

# while loop
```bash
while [ contiition ] do
	execution
done
```

