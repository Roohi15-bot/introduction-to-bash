# what is bash

Bash scripting involves writing a series of commands, normally executed one by one in a command-line interface, into a single text file. This file, known as a Bash script, can then be executed to run all those commands automatically in sequence.

# Basic Shell Concepts:-

>Terminal
   
The terminal is where you enter commands. Bash is the program interpreting these commands.

You can access the terminal via:

macOS: Terminal app

Linux: Ctrl+Alt+T

Windows: WSL (Windows Subsystem for Linux), Git Bash, or Ubuntu via terminal

 >Command Structure
   
command [options] [arguments]

Example:

ls -l /home/user

ls: command

-l: option (long format)

/home/user: argument (directory to list)

# Try It Yourself

>Open your terminal and try these:

echo "Hello, World!"

pwd

whoami

What They Do:

echo: prints a message

pwd: prints the current working directory

whoami: shows your username

#  What is a Bash Script?

A Bash script is a plain text file containing a series of Bash commands that the shell can execute sequentially.

Example:

#!/bin/bash

echo "Hello, this is my first Bash script!"

# Writing Your First Script

Open a terminal

>Create a file

touch myscript.sh

>Edit the file

nano myscript.sh

>Paste this into the file:

#!/bin/bash

echo "Script is running..."

date

>Save and exit (Ctrl + O, Enter, then Ctrl + X in nano)

 # Making a Script Executable
 
>To allow your system to run your script as a program, make it executable:

chmod +x myscript.sh

>Running a Bash Script

Now that it’s executable, run it with:

./myscript.sh

>Alternate Method:

You can also run the script without making it executable:

bash myscript.sh

> Shebang (#!)

The shebang at the top of the script:

#!/bin/bash

# Variables and Data Types in Bash

> What is a Variable?

A variable is like a container in memory. You can store data in it and use it later.

> How to Create a Variable

name="Alice"

✅ Rules:

No spaces around =

Variable names are case-sensitive (Name and name are different)

# How to Use (Access) a Variable

Use $ before the variable name:

echo "Hello, $name"

Output:

Hello, Alice

Tells the system to use the Bash interpreter to run the script. Without it, the system may not know how to execute your script.

> Reading User Input
> 
Let the user enter a value at runtime:

echo "What is your name?"

read user_name

echo "Welcome, $user_name!"

# Special Variables

>Variable	Description

$0	Name of the script

$1, $2, …	Arguments passed to the script

$#	Number of arguments

$@	All arguments

$$	Process ID of the script

$?	Exit status of last command (0 = success)

>Example:

#!/bin/bash

echo "Script name: $0"

echo "First argument: $1"

Run it like this:

bash script.sh hello

> Output:

Script name: script.sh

First argument: hello

# Data Types in Bash

Bash treats everything as strings unless you do something special.

> String
   
greeting="Hello"

> Number

x=5
 
y=3

sum=$((x + y))

echo "Sum is: $sum"

> (( )) is used for arithmetic.

>Use double quotes when printing variables: "Hello, $name"

>Use single quotes when you don’t want variables to be replaced: 'Hello, $name' (will print literally)

>Concept	Example:-

Declare variable	name="Ramya"

Use variable	echo $name

User input	read variable_name

Arithmetic	sum=$((x + y))

Special variable	$0, $1, $?, etc.

# Conditional Statements in Bash
 
> What Are Conditional Statements?

Conditional statements let your script make decisions.

Example: If it's raining, take an umbrella. If it's sunny, wear sunglasses.

In Bash, we use if, else, elif, and case for conditions.

 # Basic if Statement
 
#!/bin/bash

if [ condition ]; then

 code to run if condition is true
  
fi

>Example 1: Check if a number is positive

#!/bin/bash

number=5

if [ $number -gt 0 ]; then

    echo "The number is positive."
  
fi

# comparison Operators

Operator	Meaning

-eq	equal to

-ne	not equal to

-gt	greater than

-lt	less than

-ge	greater or equal

-le	less or equal

For strings: = (equal), != (not equal), -z (empty), -n (not empty)

# if...else Statement

#!/bin/bash

echo "Enter a number:"

read num

if [ $num -gt 10 ]; then

    echo "Greater than 10"
  
else

    echo "10 or less"
  
fi

#  if...elif...else

#!/bin/bash

echo "Enter your age:"

read age

if [ $age -lt 13 ]; then

      echo "You're a child."
   
elif [ $age -lt 20 ]; then

      echo "You're a teenager."
   
else

     echo "You're an adult."
  
fi

# String Comparison Example

#!/bin/bash

echo "Enter username:"

read username

if [ "$username" = "admin" ]; then

    echo "Welcome, admin!"
    
else

     echo "Access denied."
     
fi

Always quote variables like "$username" to avoid errors if the variable is empty or has spaces.

# The case Statement

Good for multiple fixed choices.

#!/bin/bash

echo "Choose a fruit: apple, banana, orange"

read fruit

case $fruit in

  apple)
  
       echo "Apples are red or green.";;
       
  banana)
  
       echo "Bananas are yellow.";;
  orange)
  
       echo "Oranges are orange.";;
       
  *)
  
       echo "Unknown fruit.";;
       
esac

#loops

Loops are used to repeat a set of commands multiple times, making your scripts powerful and efficient.

> types of loops

Loop type     Description

for	        Repeat over a list or range

while       	Repeat while a condition is true

until	        Repeat until a condition becomes true

> for loop

A for loop is best when you know how many times you want to repeat something or have a list to go through.

 > Syntax:

for variable in list

do

    commands
  
done

> Example:

for fruit in apple banana cherry

do

    echo "I like $fruit"
  
done

Output: I like apple I like banana I like cherry

> while loop

 Theory:
 
A while loop is used when the condition needs to be checked before each iteration.

>  Syntax:

while [ condition ]

do

    commands
  
done

>  Example:

count=1

while [ $count -le 3 ]

do

      echo "Count is $count"
  
      ((count++))
  
done

> until loop

Theory:

An until loop runs until the condition becomes true — almost like the opposite of while.

>  Syntax:

until [ condition ]

do

    commands
  
done

> Example:

count=1

until [ $count -gt 3 ]

do

    echo "Count is $count"
  
    ((count++))
  
done 

# controlling loops

 > break – Exit the loop early

for i in {1..5}

do

     if [ $i -eq 3 ]; then
  
        break
    
     fi
  
     echo "i is $i"
  
done

Stops when i becomes 3

> continue-Skip current iteration

for i in {1..5}

do

     if [ $i -eq 3 ]; then
  
       continue
    
   fi
  
   echo "i is $i"
  
done

Skips printing 3

> Concept	Explanation

for -	Repeats over a list or range

while	 - Runs while condition is true

until  -	Runs until condition becomes true

break  -	Exits the loop early

continue - 	Skips one iteration and continues











