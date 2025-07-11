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

# Functions in bash

A function is a reusable block of code that performs a specific task.

> function syntax in bash

function_name() {

    commands
    
}

Basic Example: A Simple Greeting

greet() {

    echo "Hello, welcome to Bash scripting!"
  
}

 #Call the function

  greet
  
Output: Hello, welcome to Bash scripting!

> Example:

print_name() {

    echo "Your name is $1"
  
}

print_name "Ramya"

Output: Your name is Ramya

> Use echo to return text

get_date() {

  echo "Today is $(date)"
  
}

result=$(get_date)

echo $result

> Check if a Number is Positive

#!/bin/bash

check_number() {

  if [ $1 -gt 0 ]; then
  
    echo "$1 is positive."
    
  else
  
    echo "$1 is not positive."
    
  fi
  
}

check_number 5

check_number -2

Output:

5 is positive.

-2 is not positive.

> Add Two Numbers

#!/bin/bash

add_numbers() {

  result=$(( $1 + $2 ))
  
  echo "The sum is: $result"
  
}

add_numbers 3 7

Output:

The sum is: 10

> Reusable Calculator Function

calculator() {

  if [ "$2" == "+" ]; then
  
    echo $(($1 + $3))
    
  elif [ "$2" == "-" ]; then
  
    echo $(($1 - $3))
    
  else
  
    echo "Unsupported operation"
    
  fi
  
}

calculator 10 + 5

calculator 20 - 7

> Summary

function_name() - Declares a function

$1, $2, etc. - 	Function arguments

return -          Sends back numeric result

echo -           	Returns any type of value

$(...) - 	      Captures output of a function

Use if inside - 	Check number, compare strings

# working with files in bash 

 > Why File Handling?

File handling lets your scripts:

Save output (e.g., logs or results)

Read input from a file

Combine tools to build powerful automations

 > 1. Writing to a File with>

 Use: Save output to a file (overwrite if it exists)
 
         echo "Hello, Ramya!" > greeting.txt

 This creates or overwrites greeting.txt with the line:

       Hello, Ramya!

> 2. Appending to a File with>>

 Use: Add text to the end of a file without deleting existing content
 
         echo "How are you?" >> greeting.txt
         
Now greeting.txt contains:

      Hello, Ramya!
      
      How are you?

> 3. Reading from a File with <

 Use: Take input from a file (not often used alone, but good to know)

         cat < greeting.txt
         
This tells cat to read the file using <.

> Reading a File Line-by-Line (Practical Example)

#!/bin/bash

while read line; do

    echo "Line: $line"
  
done < greeting.txt

Each line in greeting.txt will be printed like:

   Line: Hello, Ramya!

   Line: How are you?

5. Pipes | – Connecting Commands

 Use: Send output from one command into another
 
          echo "hello world" | tr a-z A-Z

Output:

HELLO WORLD

Here:

echo prints "hello world"

tr translates it to uppercase using a pipe

< 6. tee – Save Output AND Show It

 Use: Show output and also write it to a file
 
             echo "This is a test" | tee output.txt

Output:

This is a test

File output.txt contains:

   This is a test

> Example: Combine echo, tee, and>>

      echo "New log entry" | tee -a log.txt

This shows the message and also appends it to log.txt.

> Summary

Symbol	Use:-

>=Write (overwrite)

>>=Append

<=Read from file

`	`	`

tee = Show and save output	

# String and Array Operations in Bash

String Manipulation in Bash

> What is a String in Bash?

     In Bash, a string is simply text stored in a variable. It can be anything: words, sentences, file names, etc.

> a) Assigning Strings

name="Ramya"

The = sign assigns the value without any spaces around it.

"Ramya" is the string being stored.

Now, you can use $name to access the value.

     echo "Hello, $name"

Prints: Hello, Ramya

$name gets replaced by the value inside the variable.

> b) Getting String Length

text="hello"

echo ${#text}

   ${#text} gives the number of characters in the string.

   Output: 5 (Because "hello" has 5 letters)

> c) Extracting Substrings

    text="BashScripting"

    echo ${text:0:4}

${text:START:LENGTH} is the format.

This means: start at index 0 and take 4 characters.

Output: Bash

    echo ${text:4}

Starts from position 4 and takes everything till the end.

Output: Scripting

Bash starts counting from 0.

> d) Replacing Part of a String

         greeting="Hello World"

        echo ${greeting/World/Ramya}

${variable/old/new} replaces the first occurrence of old with new.

Replaces "World" with "Ramya" in the string.

Output: Hello Ramya

 You can use ${variable//old/new} to replace all occurrences.

 > e) Removing Part of a String

         filename="report.txt"

         echo ${filename%.txt}

% is used to remove a suffix from the string.

%.txt means "remove .txt if it appears at the end".

Output: report

You can also use # for removing prefixes.

# arrays in bash 

> What is an Array?

An array is a collection of values (like a list). You can store multiple items in one variable and access them using index numbers.

> a) Creating an Array

fruits=("apple" "banana" "cherry")

We use () to group items.

Each item is separated by a space, not commas.

The index starts at 0:

fruits[0] = "apple"

fruits[1] = "banana"

fruits[2] = "cherry"

> b) Accessing Items

       echo ${fruits[0]}   # apple

       echo ${fruits[2]}   # cherry

${fruits[index]} gets the item at the given position.

> c) Get All Items

         echo ${fruits[@]}

${fruits[@]} or ${fruits[*]} gives all items in the array.

Output: apple banana cherry

> d) Length of an Array

         echo ${#fruits[@]}

${#array[@]} gives the number of items in the array.

Output: 3 (since we added three fruits)

 > e) Add and Remove Items

          fruits+=("orange")     # Add orange to the array

           unset fruits[1]        # Remove banana (index 1)

+= appends new elements.

unset deletes the element at a specific index.

After this:

fruits[0] = "apple"

fruits[1] = (removed)

fruits[2] = "cherry"

fruits[3] = "orange"

Note: Bash arrays do not automatically reindex after deletion.

# Looping Through Arrays

 > Why loop?

To perform some action with each item in the array — like printing, checking, or modifying.

>  Loop Example

colors=("red" "green" "blue")

for color in "${colors[@]}"; do

     echo "Color: $color"
  
done

> How it works:

"${colors[@]}" gives all elements.

for color in ... means: go through each item one-by-one.

echo prints it.

Output:

Color: red

Color: green

Color: blue

> Summary Table:-

Concept                          syntax                                               Meaning

String assignment	              str="hello"	                               Store text in a variable

String length	                 ${#str}	                                  Number of characters

Substring	                    ${str:start:length}	                      Slice part of a string

Replace                         ${str/old/new}                            	 Replace part of a string

Array declare	                 arr=(a b c)                                 Create a list

Array item                      ${arr[1]}	                                  Get one item

All items                       ${arr[@]}	                                  Get all array values

Array length                    ${#arr[@]}                                  Get how many items

Add item	                       arr+=("new")	                               Add item to array

Remove item	                    unset arr[1]	                               Remove item at index

Loop	                          for x in "${arr[@]}"	                      Go through each item

#  Error Handling and Debugging in Bash

 > 1. Exit Status ($?)

>  What is an Exit Status?

Every time you run a command in Bash, it returns a hidden value called exit status.

         0 → Command succeeded

          Non-zero (1, 2, 127, etc.) → Command failed

You can check this using:

echo $?

 > Example:

          ls /some/folder

          echo $?  # Shows 0 if folder exists, else non-zero (like 2)

>  How It Works:

$? is a special variable that always stores the exit code of the last run command.

You can use this in if conditions for logic like:

  if [ $? -ne 0 ]; then

       echo "Command failed!"
  
  fi

> 2. set -e: Stop on First Error

 What does set -e do?

 It tells Bash:

     "If any command fails, stop the whole script immediately."

>  Example:

 
     #!/bin/bash
     
        set -e
        
        echo "Start"
        
        false          # Simulates a failure
        
        echo "Won’t reach here"
        
>  Explanation:

false is a Bash command that always fails (returns exit code 1).

Because of set -e, the script exits immediately after false.

echo "Won’t reach here" is never executed.

 > 3. set -x: Print Commands While Executing

What does set -x do?

It puts the script into debug mode — every command will be printed before it's run.

> Example:

      #!/bin/bash

      set -x

      name="Ramya"

      echo "Hi $name"

>  Explanation:

set -x adds a + prefix before every command it runs.

> 4. trap: Catch Signals and Errors

    What is trap?

    trap allows you to run a custom function or command when:

The script exits

It’s interrupted

It receives a specific signal (like SIGINT or EXIT)

> Important Keywords:

Keyword	    What It Means

trap	       Keyword to catch events

EXIT	       Triggered when the script ends (normally or with exit)

SIGINT     	 Signal sent when user presses Ctrl+C

sleep        Delays execution for a number of seconds

SIGTERM	    Signal for graceful shutdown

ERR	       Special signal when any command fails (good with set -e)

#  Example: Trap on Script Exit (EXIT)

    #!/bin/bash

    cleanup() {

            echo "Cleaning up before exit..."
    }

    trap cleanup EXIT

    echo "Doing work..."

    sleep 1
    
>  Explanation:

trap cleanup EXIT: When the script ends, call the cleanup function.

sleep 1: Pauses the script for 1 second.

Useful for removing temporary files or closing connections safely.

# Example: Trap Ctrl+C (SIGINT)

      #!/bin/bash

       trap 'echo "You pressed Ctrl+C! Exiting..." ; exit' SIGINT

       while true; do

                echo "Working... press Ctrl+C to stop"
  
                 sleep 1
  
       done

>  Explanation:

SIGINT is the signal sent when user presses Ctrl+C.

trap intercepts that signal and runs a custom message.

while true: Infinite loop — runs forever.

sleep 1: Waits 1 second before repeating.

   This is helpful for gracefully shutting down scripts.

> Recap: What Each Command Means

Command                   	Purpose

set -e	                  Stop the script when any command fails

set -x	                  Show commands as they are run (for debugging)

trap	                     Catch events or signals like EXIT, SIGINT

sleep N	                  Wait N seconds (simulate time delay or retry logic)

$?                       	Shows the result of the last command (0=success, non-zero=failure)







































