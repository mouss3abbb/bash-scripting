# Bash Scripting
Basic tutorial about bash scripting

## Introduction

Shell is a command language interpreter that is available on many operating systems.

Shell has many variants. One of them is Bourne Again Shell (aka Bash).

To get started make sure you have a shell variant (Bash and Zsh are used in this tutorial), then make a file with `.sh` extension

## Basic syntax

For making a comment in Bash you simply add `#` and type your comment (similar to Python)

```
# Hello, this is a comment in bash

# This is also a comment
```

However, there's a special line that starts with `#` but is not a comment and that is `#!`

These two symbols together are (Sharp sign and Bang sign) pronounced *Shebang*
 
This line tells which Shell variant are you using 

For Bash users you would type `#!/bin/bash`

For ZSH users you would type `#!/bin/zsh`

You can always find the path to your shell using this command `echo $SHELL`

Your script should look like this now

```
#!/bin/bash

# The rest of the script
...
```

## Variables

To declare a variable in bash, you simply type its name and assign it a value (Do never add space before or after the equal sign)

`VAR="Abdullah"`

Variable names can be combination of upper and lower case letter or numbers and underscores but should start with a letter or underscore

Another way if you want to declare the variable without assigning a value to it, you can use `declare`

```
declare VAR
```

You can also assign a value

```
declare VAR="Hello World"
```

By default all variables are strings, but you can declare integers by adding the flag `-i`

```
declare -i INT_VAR=5
```

## I/O
To print anything to the console screen you can use the `echo` command 

```
echo "Anything to the screen"
```
You can access any predefined variables using the `$` symbol inside double quotation and also without them

```
echo "Variable value = $VAR" # correct
echo $VAR # correct
echo "$VAR" # correct
echo '$VAR' # Will print $VAR not the value in the variable
```

There are some variables predefined and found in any Bash script. These variables are called environment variables

Some of them are `$HOME`, `$SHELL` and `$PATH`. You can use these variables anywhere from a shell
