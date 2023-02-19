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

You can specifiy the variable as *readonly* (similar to constant) to prevent someone from overwriting it

```
declare -r NAME_CONST="Linux"
```

## Basic I/O

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

For more advanced printing you can use the `printf` command (similar to C).

You can add some format specifiers and they will be replaced by the corresponding variables

```
#!/bin/bash

declare -i age=21
declare name="Abdullah"

printf "%s is %d years old\n" "$name" "$age"
```

`%s` - denotes a string

`%d`, `%i` - denotes integer

`%f` - denotes float

`%e` - denotes scientific notation

You can also printf specific precision with floats

`printf "%.6f" 2.15214`

To read an input value from the user you can use the `read` command.

```
declare NAME

printf "Please enter your name: "

read NAME

printf "Hello Mr. %s\n" "$NAME"
```

You can even delete the `declare` statement as the variable will be automatically created with the `read` command.

Furthermore, you can add a flag `-p` for prompting the user with a message. That means we can delete the first printing statement as well

```
read -p "Please enter your name: " NAME

printf "Hello Mr. %s\n" "$NAME"
```

## Arithmetic Operations

You can't do many arithemetic operations directly.

Try these operations `VAR++`, `VAR-=4`. They won't work

To make arithemetic operations you can use the `let` command

```
let VAR++
let VAR-=2
let VAR=5+7
let VAR=VAR-1
```

Another way is to put your operation in ``(())``


```
((VAR++))
((VAR-=2))
((VAR=5+7))
((VAR=VAR-1))
```

Basic operators

`+` - Addition

`-` - Subtraction

`*` - Multiplication

`/` - Integer division

`%` - Remainder

`++` - Post/Pre increment

`--` - Post/Pre decrement
