## Shell

### vi Editor

Editing files using the screen-oriented text editor vi is one of the best ways. This editor enables you to edit lines in context with other lines in the file.

You will notice a tilde (~) on each line following the cursor. A tilde represents an unused line. If a line does not begin with a tilde and appears to be blank, there is a space, tab, newline, or some other non-viewable character present.

vi always starts in the command mode. To enter text, you must be in the insert mode for which simply type `i`. To come out of the insert mode, press the `Esc` key.
|Command|Description|
|-----|-------------------------|
|`:q`| To quit out of vi|
|`:q!`| To ignore this message, the command to quit out of vi without saving|
|`:w`| The command to save the contents of the editor|
|`:wq`| To save and quit `ZZ` does the same|
|`:w filename2`| To save the currently working file with another name|
|`:s/search/replace/g`| The substitution command (:s/) enables you to quickly replace words or groups of words within your files|

**Editing Files**
|Command|Description|
|-----|-------------------------|
|`i`| Inserts text before the current cursor location|
|`I`| Inserts text at the beginning of the current line|
|`a`| Inserts text after the current cursor location|
|`A`| Inserts text at the end of the current line|
|`o`| Creates a new line for text entry below the cursor location|
|`O`| Creates a new line for text entry above the cursor location|

**Set Commands**

You can change the look and feel of your vi screen using the following `:set` commands.
|Command|Description|
|-----|-------------------------|	
|:set ic| Ignores the case when searching|
|:set ai| Sets autoindent|
|:set noai| Unsets autoindent|	
|:set nu| Displays lines with line numbers on the left side|
|:set sw| Sets the width of a software tabstop. For example, you would set a shift width of 4 with this command — :set sw = 4|
|:set ws| If wrapscan is set, and the word is not found at the bottom of the file, it will try searching for it at the beginning|
|:set wm| If this option has a value greater than zero, the editor will automatically "word wrap". For example, to set the wrap margin to two characters, you would type this: :set wm = 2|
|:set ro| Changes file type to "read only"|
|:set term| Prints terminal type|
|:set bf| Discards control characters from input|

**Running Commands**

The vi has the capability to run commands from within the editor. To run a command, you only need to go to the command mode and type `:!` command.

For example, if you want to check whether a file exists before you try to save your file with that filename, you can type `:! ls` and you will see the output of `ls` on the screen.

You can press any key (or the command's escape sequence) to return to your vi session.

**Word and Character Searching**

The vi editor has two kinds of searches: string and character. For a string search, the / and ? commands are used. When you start these commands, the command just typed will be shown on the last line of the screen, where you type the particular string to look for.

These two commands differ only in the direction where the search takes place −

The / command searches forwards (downwards) in the file.

The ? command searches backwards (upwards) in the file.

## Listing files
|File Type and Permission|no. of Memory blocks taken|Owner|Group|Size(bytes)|last modified time|name|
|---|--|--|--|--|--|--|
|-rw-r--r--|  1| anand|  staff|  9395| Jan  9 03:33| README.md|
|-rw-r--r-- | 1| anand|  staff |   86| Dec 30 15:38 |ansible.cfg|
|-rw-r--r--|  1| anand|  staff|   893| Jan  3 01:22| bootstrap.yml|
|-rw-r--r--|  1| anand|  staff|   215| Dec 25 09:26| consolidated_install_apache.yml|
|-rw-r--r--|  1| anand|  staff|   190| Dec 25 09:26| consolidated_inventory|
|drwxr-xr-x|  4| anand|  staff|   128| Dec 30 15:38| files|

|Prefix | Description|
|--|--|	
|- |Regular file, such as an ASCII text file, binary executable, or hard link.|
|b|Block special file. Block input/output device file such as a physical hard drive.|
|c|Character special file. Raw input/output device file such as a physical hard drive.|	
|d|Directory file that contains a listing of other files and directories.|	
|l|Symbolic link file. Links on any regular file.|	
|p|Named pipe. A mechanism for interprocess communications.|	
|s|Socket used for interprocess communication.|

## File System
A file system is a logical collection of files on a partition or disk. A partition is a container for information and can span an entire hard drive if desired.

Your hard drive can have various partitions which usually contain only one file system, such as one file system housing the /file system or another containing the /home file system.
|Directory|Description|
|--|--|
|/|This is the root directory which should contain only the directories needed at the top level of the file structure|
|/bin|This is where the executable files are located. These files are available to all users|
|/dev|These are device drivers|
|/etc|Supervisor directory commands, configuration files, disk configuration files, valid user lists, groups, ethernet, hosts, where to send critical messages|
|/lib|Contains shared library files and sometimes other kernel-related files|
|/boot|Contains files for booting the system|
|/home|Contains the home directory for users and other accounts|
|/mnt|Used to mount other temporary file systems, such as cdrom and floppy for the CD-ROM drive and floppy diskette drive, respectively|
|/proc|Contains all processes marked as a file by process number or other information that is dynamic to the system|
|/tmp|Holds temporary files used between system boots|
|/usr|Used for miscellaneous purposes, and can be used by many users. Includes administrative commands, shared files, library files, and others|
|/var|Typically contains variable-length files such as log and print files and any other type of file that may contain a variable amount of data|
|/sbin|Contains binary (executable) files, usually for system administration. For example, fdisk and ifconfig utlities|
|/kernel|Contains kernel files|

### df Command
The first way to manage your partition space is with the df (disk free) command. The command df -k (disk free) displays the disk space usage in kilobytes.<br>
You can use the -h (human readable) option to display the output in a format that shows the size in easier-to-understand notation.

### du Command
The du (disk usage) command enables you to specify directories to show disk space usage on a particular directory.<br>
This command is helpful if you want to determine how much space a particular directory is taking.

## grep

The grep filter searches a file for a particular pattern of characters and displays all lines that contain that pattern. The pattern that is searched in the file is referred to as the regular expression (grep stands for global search for regular expression and printout). 

Syntax of grep Command in Unix/Linux
```sh
grep [options] pattern [files]
```

Options Available in grep Command
|Options |Description|
|--------|-----------|
|-c|This prints only a count of the lines that match a pattern|
|-h|Display the matched lines, but do not display the filenames.|
|–i|Ignores, case for matching|
|-l|Displays list of a filenames only.|
|-n|Display the matched lines and their line numbers.|
|-v|This prints out all the lines that do not matches the pattern|
|-e exp|Specifies expression with this option. Can use multiple times.|
|-f file|Takes patterns from file, one per line.|
|-E|Treats pattern as an extended regular expression (ERE)|
|-w|Match whole word|
|-o|Print only the matched parts of a matching line, with each such part on a separate output line.|
|-A n|Prints searched line and nlines after the result.|
|-B n|Prints searched line and n line before the result.|
|-C n|Prints searched line and n lines after before the result.|

<details>
<summary>Create a file abc.txt with below content</summary>

```txt
Welcome to Linux !
Linux is a free and opensource Operating system that is mostly used by
developers and in production servers for hosting crucial components such as web
and database servers. Linux has also made a name for itself in PCs.
Beginners looking to experiment with Linux can get started with friendlier linux
distributions such as Ubuntu, Mint, Fedora and Elementary OS.
```
</details>

## Shell Scripting

<details>
<summary>What does this line in shell scripts means?: <code>#!/bin/bash</code></summary><br>

`#!/bin/bash`

/bin/bash is the most common shell used as default shell for user login of the linux system. The shell’s name is an acronym for Bourne-again shell. Bash can execute the vast majority of scripts and thus is widely used because it has more features, is well developed and better syntax.

</details>


<details>
<summary>True or False? When a certain command/line fails in a shell script, the shell script, by default, will exit and stop running</summary><br>

Depends on the language and settings used.
In case of a bash script even after a command fails, it will continue to execute next line(s). 
Let's see an example, create a simple `hello.sh` script.
We have a statement that‘s guaranteed to fail.
```bash
#!/bin/bash
echo hello
cat non-existing-file
echo world
```
If executed, this script will produce an output. Execution doesn't stop, but "world" is still outputted −
```bash
$ ./hello.sh
hello
cat: non-existing-file: No such file or directory
world
```
We also got a 0 exit code for our script which indicates everything went well.
```bash
$ echo $?
0
```
If we want to make a shell script exit whenever any command within the script fails, you can use the set -e option. This option tells the shell to exit immediately if any command within the script exits with a non-zero status.

Unfortunately, this solution won't help if your script contains piped statements. If we want to run multiple commands without failing if any one fails, let's add -o pipefail to the first command. `set -eo pipefail`
</details>

<details>
<summary>Advantages of shell scripts</summary><br>

  * Shell scripting is meant to be simple and efficient. 

  * It uses the same syntax in the script as it would on the shell command line, removing any interpretation issues.
  * Writing code for a shell script is also faster and requires less of learning curve than other programming languages.
  * The module we need doesn't exist (perhaps a weak point because most CM technologies allow to use what is known as "shell" module)
  * We are delivering the scripts to customers who don't have access to the public network and don't necessarily have Ansible installed on their systems.
</details>

#### Shell Script - Variables

<details>
<summary>How to define a variable with the value "Hello World"?</summary><br>

`HW="Hello World`
</details>

<details>
<summary>How to define a variable with the value of the current date?</summary><br>

`DATE=$(date)`
</details>

<details>
<summary><b>How to print the first argument passed to a script?</b></summary><br>

`echo $1`
</b></details>

<details>
<summary>Write a script to print "yay" unless an argument was passed and then print that argument</summary><br>

```
echo "${1:-yay}"
```
</details>


<details>
<summary>Explain what would be the result of $_ commands:</summary>

`$0` - Name of the script

`$n` - `$1` to `$9` - Arguments to the script. $1 is the first argument and so on.

`$@` - All the arguments

`$#` - Number of arguments in the script

`$?` - Return code of the previous command

`$$` - Process identification number (PID) for the current script

`$*` - It stores complete set of positional parameter in a single string

`$!` - check PID of last background Job

`!!` - Entire last command, including arguments. A common pattern is to execute a command only for it to fail due to missing permissions; you can quickly re-execute the command with sudo by doing sudo !!

`$_` - Last argument from the last command.


</details>

<details>
<summary>Difference between `$@` and `$*`?</summary><br><b>

`$@` is an array of all the arguments passed to the script
`$*` is a single string of all the arguments passed to the script
</b></details>

<details>
<summary>How to get input from user in shell script?</summary><br>

By using read in your shell scripts, you can prompt the user for input and store the results in a variable. You can also use read to read in one value using a variable to prompt the user for another value. 

This tells the script to prompt the user for input. The text inside the quotes after the -p is displayed to the user when they are prompted. 
```bash
$ read -p "What is your name? " my_var
```
The read command provides the silent mode option with “-s” to hide the input characters from the screen. A sample script to take password input from the user.
```bash
read -s -p "Enter a Password: " my_var
```
</details>

<details>
<summary>How to compare variables length?</summary><br>

```
if [[ ${#string} != ${#string_two} ]]; then
    run command
fi
```
</details>

#### Shell Scripting - Conditionals

<details>
<summary>Explain conditionals and demonstrate how to use them</summary><br>

**if statement**

This block will process if specified condition is true.

Syntax:
```bash
if [ expression ]
then
   statement
fi
```

**if-else statement**

If specified condition is not true in if part then else part will be execute.

Syntax
```bash
if [ expression ]
then
   statement1
else
   statement2
fi
```

**if..elif..else..fi statement (Else If ladder)**

To use multiple conditions in one if-else block, then elif keyword is used in shell. If expression1 is true then it executes statement 1 and 2, and this process continues. If none of the condition is true then it processes else part.

Syntax

```bash
if [ expression1 ]
then
   statement1
   statement2
   .
   .
elif [ expression2 ]
then
   statement3
   statement4
   .
   .
else
   statement5
fi
```

**if..then..else..if..then..fi..fi..(Nested if)**

Nested if-else block can be used when, one condition is satisfies then it again checks another condition. In the syntax, if expression1 is false then it processes else part, and again expression2 will be check.

Syntax:
```bash
if [ expression1 ]
then
   statement1
   statement2
   .
else
   if [ expression2 ]
   then
      statement3
      .
   fi
fi
```
eg:
```bash
#Initializing two variables 
a=10 
b=20 

#Check whether they are equal 
if [ $a == $b ] 
then 
	echo "a is equal to b"
fi 

#Check whether they are not equal 
if [ $a != $b ] 
then 
	echo "a is not equal to b"
fi 

```

**Switch statement**

case statement works as a switch statement if specified value match with the pattern then it will execute a block of that particular pattern
When a match is found all of the associated statements until the double semicolon (;;) is executed.
A case will be terminated when the last command is executed.
If there is no match, the exit status of the case is zero.

Syntax:
```bash
case  in
   Pattern 1) Statement 1;;
   Pattern n) Statement n;;
esac
```
```bash
CARS="bmw"

#Pass the variable in string 
case "$CARS" in 
	#case 1 
	"mercedes") echo "Headquarters - Affalterbach, Germany" ;; 
	
	#case 2 
	"audi") echo "Headquarters - Ingolstadt, Germany" ;; 
	
	#case 3 
	"bmw") echo "Headquarters - Chennai, Tamil Nadu, India" ;; 
esac 
```
</details>

<details>
<summary>In shell scripting, how to negate a conditional?</summary><br><b>
</b></details>

<details>
<summary>In shell scripting, how to check if a given argument is a number?</summary><br><b>

```
regex='^[0-9]+$'
if [[ ${var//*.} =~ $regex ]]; then
...
```
</b></details>

#### Shell Scripting - Arithmetic Operations

<details>
<summary>How to perform arithmetic operations on numbers?</summary><br>

One way: `$(( 1 + 2 ))`
Another way: `expr 1 + 2`
</details>


<details>
<summary>How to check if a given number has 4 as a factor?</summary><br>

`if [ $(($1 % 4)) -eq 0 ]; then`
</details>

#### Shell Scripting - Loops

<details>
<summary>What is a loop? What types of loops are you familiar with?</summary><br>

**While Loop**

The while loop executes the given commands until the given condition remains true; the until loop executes until a given condition becomes true.

Syntax

```bash
while [ condition ]
do
command1
command2
done
```

All the loops support nesting concept which means you can put one loop inside another similar one or different loops. This nesting can go up to unlimited number of times based on your requirement.

Syntax

```bash
while command1 ; # this is loop1, the outer loop
do
   Statement(s) to be executed if command1 is true

   while command2 ; # this is loop2, the inner loop
   do
      Statement(s) to be executed if command2 is true
   done

   Statement(s) to be executed if command1 is true
done
```
eg
```bash
#!/bin/sh

a=0
while [ "$a" -lt 10 ]    # this is loop1
do
   b="$a"
   while [ "$b" -ge 0 ]  # this is loop2
   do
      echo -n "$b "
      b=`expr $b - 1`
   done
   echo
   a=`expr $a + 1`
done
```

**For Loop**

For loop is another type of looping statement to execute a set of commands for a certain number of times.

Syntax:
```bash
for var in list
do
command 1
command 2
done
```

eg:

```bash
#!/bin/sh

for var in 0 1 2 3 4 5 6 7 8 9
do
   echo $var
done
```

**Until Loop**

Until loop is one of the looping statements in the shell scripting and this looping statement is similar to the while loop statement which we have discussed earlier. The difference between two is, it will execute the body of the loop until the conditional statement becomes true whereas while loop executes commands if the condition is true. 

Syntax:

```bash
until [ conditional statement ]
do
command1
command2
done
```
eg:
```bash
number = 1
until [ $number –gt 10 ]
do
echo $number
((number++))
done
```

**Select Loop**
The select loop provides an easy way to create a numbered menu from which users can select options. It is useful when you need to ask the user to choose one or more items from a list of choices.

Syntax
```bash
select var in word1 word2 ... wordN
do
   Statement(s) to be executed for every word.
done
```
eg:
```bash
#!/bin/ksh

select DRINK in tea cofee water juice appe all none
do
   case $DRINK in
      tea|cofee|water|all) 
         echo "Go to canteen"
         ;;
      juice|appe)
         echo "Available at home"
      ;;
      none) 
         break 
      ;;
      *) echo "ERROR: Invalid selection" 
      ;;
   esac
done
```
</details>



#### Shell Scripting - Troubleshooting

<details>
<summary>How do you debug shell scripts?</summary><br>

You need to pass the -x or -v argument to bash shell to walk through each line in the script.

Using the -x option to debug a bash shell script

Run a shell script with -x option. The syntax is:
```bash
bash -x script-name
bash -x domains.sh
```
Bash shell offers debugging options which can be turn on or off using the set command:

`set -x` : Display commands and their arguments as they are executed.
`set -v` : Display shell input lines as they are read.

Example

You can use above two command in shell script itself:
```bash
#!/bin/bash
clear
 
# turn on debug mode
set -x
for f in *
do
   file $f
done
# turn OFF debug mode
set +x
ls
# more commands
```
You can replace the standard Shebang line:

`#!/bin/bash`

with the following (for debugging) code:

`#!/bin/bash -xv`

**Debugging Common Bash Shell Scripting Errors**

Bash or sh or ksh gives various error messages on screen and in many case the error message may not provide detailed information.

When you write your first hello world bash shell script, you might end up getting an error that read as follows:

```bash
bash: ./hello.sh: Permission denied
```
Set permission using chmod command:
```bash
chmod +x hello.sh
./hello.sh
bash hello.sh
```

End of file unexpected Error

If you are getting an End of file unexpected error message, open your script file and and make sure it has both opening and closing quotes. In this example, the echo statement has an opening quote but no closing quote:
```bash
#!/bin/bash
...
....
echo 'Error: File not found
                                        ^^^^^^^
                                        missing quote
```
Also make sure you check for missing parentheses and braces ({}):
```bash
#!/bin/bash
.....
[ ! -d $DIRNAME ] && { echo "Error: Chroot dir not found"; exit 1;
                                                                    ^^^^^^^^^^^^^
                                                                    missing brace }
...
```
Missing Keywords Such As fi, esac, ;;, etc.

If you missed ending keyword such as fi or ;; you will get an error such as as “xxx unexpected”. So make sure all nested if and case statements ends with proper keywords. 

Tip: 
Turn On Syntax Highlighting when using vim text editor

Most modern text editors allows you to set syntax highlighting option. This is useful to detect syntax and prevent common errors such as opening or closing quote. You can see bash script in different colors. 

And use `man` and `help` to get list of all valid use cases for all commands


</details>

<details>
<summary>Running the following bash script, we don't get 2 as a result, why?

```
x = 2
echo $x
```
</summary><br>

Should be `x=2`
</details>

#### Shell Scripting - Substring

<details>
<summary>How to extract everything after the last dot in a string?</summary><br>

`${var//*.}`
</details>

<details>
<summary>How to extract everything before the last dot in a string?</summary><br>

${var%.*}
</details>

#### Shell Scripting - Misc

<details>
<summary>Generate 8 digit random number</summary><br>
	
```bash
rand=''
for i in {1..9}; do
    rand="${rand}$(( $RANDOM % 10 ))"
done

echo $rand
```
</details>


<details>
<summary>What is the ternary operator? How do you use it in bash?</summary><br>

The ternary operator is a compact and efficient way to write conditional expressions. It’s a shorthand way of writing an if-else statement that returns a value.

```bash
((condition ? value_if_true : value_if_false))

a=1; b=2
z=$((a > b ? a : b))
echo "$z"
2
```
</details>

<details>
<summary>What does the following code do and when would you use it?

<code>diff <(ls /tmp) <(ls /var/tmp)</code>

</summary><br>
It is called 'process substitution'. 

It provides a way to pass the output of a command to another command when using a pipe <code>|</code> is not possible. It can be used when a command does not support <code>STDIN</code> or you need the output of multiple commands.

https://superuser.com/a/1060002/167769

</details>


### Shell Scripting Exercises
<details><summary>
Define a variable with the string 'Hello World'. Print the value of the variable you've defined and redirect the output to the file "file1.txt"
</summary>
	
```bash
#!/usr/bin/env bash

HW_STR="Hello World"
echo $HW_STR > file.txt
```
</details>

<details><summary>
Read input from the user until you get empty string. For each of the lines you read, count the number of characters and print it
</summary>

```bash
#!/usr/bin/env bash

echo -n "Please insert your input: "

while read line; do
    echo -n "$line" | wc -c
    echo -n "Please insert your input: "
done
```
</details>
