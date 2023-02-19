# Bash Scripting
Basic tutorial about bash scripting

1. [Introduction](#introduction)
2. [Basic Syntax](#basic-syntax)
3. [Variables](#variables)
4. [Arithemetic Operations](#arithemetic-operations)
5. [If Conditions](#if-conditions)

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

## Arithemetic Operations

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

## If Conditions

Basic syntax for if statement is

```
if (( *comparison condition* ))
then 
# Your code
fi
```

And you can put `then` on the same line and separate it with `;`. You can type multiple commands in the same line and separate them by `;` 


```
if (( *comparison condition* )); then 
# Your code
fi
```

Some basic relational operators are

`==` - is equal

`>` - is greater than

`<` - is less than 

`!=` - is not equal

`>=` - is greater than or equal

`<=` - is less than or equal

For other conditions (non comparison), you should use `[ *condition* ]` instead of `(( condition ))`. You should add space before and after the condition

For example to test if a file named new_script exists

```
if [ -e new_script ]; then 
echo "Exists"
fi
```
To test if it's a file you can use the `-f` flag and if it's a directory use `-d`.

You can use else if statement as follows 

```
if [ -f script.sh ]; then
echo "File Exists"
elif [ -d directory/ ]; then
echo "Directory Exists"
fi
```

You can also add an else statement without a condition that will be executed as a last option.

Furthermore, you can combine multiple conditions together

Some important operators

`-a` - AND for `[]` operator

`-o` - OR for `[]` operator

`&&` - AND for `(())` operator

`||` - OR for `(())` operator

Consider the following code

```
if [ -f script.sh -o -d directory/ ]; then
 echo "Exists"
fi
```

This code prints *Exists* if there's a file called script.sh or there's a directory called *directory*.

Consider the following code to make a program that creates a new file with the `touch` command and if that file already exists we create a new file with `1` after the name

```
#!/bin/bash

read -p "Enter name of the file " name 

if [ -f $name ]; then
	printf "The file already exists\n"
	printf "File %s1 is created instead\n" "$name"
else
	touch $name
	printf "File %s created\n" "$name"
fi
```
