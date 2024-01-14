## Shell Scripting

## Shell Scripting

<details>
<summary><b>What does this line in shell scripts means?: <code>#!/bin/bash</code></summary><br></b>

`#!/bin/bash`

/bin/bash is the most common shell used as default shell for user login of the linux system. The shell’s name is an acronym for Bourne-again shell. Bash can execute the vast majority of scripts and thus is widely used because it has more features, is well developed and better syntax.

</details>


<details>
<summary><b>True or False? When a certain command/line fails in a shell script, the shell script, by default, will exit and stop running</summary><br></b>

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
<summary><b>Advantages of shell scripts</b></summary><br>

  * Shell scripting is meant to be simple and efficient. 

  * It uses the same syntax in the script as it would on the shell command line, removing any interpretation issues.
  * Writing code for a shell script is also faster and requires less of learning curve than other programming languages.
  * The module we need doesn't exist (perhaps a weak point because most CM technologies allow to use what is known as "shell" module)
  * We are delivering the scripts to customers who don't have access to the public network and don't necessarily have Ansible installed on their systems.
</details>

#### Shell Script - Variables

<details>
<summary><b>How to define a variable with the value "Hello World"?</b></summary><br>

`HW="Hello World`
</details>

<details>
<summary><b>How to define a variable with the value of the current date?</b></summary><br>

`DATE=$(date)`
</details>

<details>
<summary><b>How to print the first argument passed to a script?</b></summary><br>

`echo $1`
</b></details>

<details>
<summary>Write a script to print "yay" unless an argument was passed and then print that argument</summary><br><b>

```
echo "${1:-yay}"
```
</b></details>


<details>
<summary><b>Explain what would be the result of $_ commands:</b></summary>


$_- The default parameter for a lot of functions.
$.- Holds the current record or line number of the file handle that was last read. It is read-only and will be reset to 0 when the file handle is closed.
$/- Holds the input record separator. The record separator is usually the newline character. However, if $/ is set to an empty string, two or more newlines in the input file will be treated as one.
$,- The output separator for the print() function. Nor-mally, this variable is an empty string. However, setting $, to a newline might be useful if you need to print each element in the parameter list on a separate line.
$\-- Added as an invisible last element to the parameters passed to the print() function. Normally, an empty string, but if you want to add a newline or some other suffix to everything that is printed, you can assign the suffix to $.
$#-- The default format for printed numbers. Normally, it's set to %.20g, but you can use the format specifiers covered in the section "Example: Printing Revisited" in Chapter 9to specify your own default format.
$%-- Holds the current page number for the default file handle. If you use select() to change the default file handle, $% will change to reflect the page number of the newly selected file handle.
$=-- Holds the current page length for the default file handle. Changing the default file handle will change $= to reflect the page length of the new file handle.
$- -- Holds the number of lines left to print for the default file handle. Changing the default file handle will change $- to reflect the number of lines left to print for the new file handle.
$~-- Holds the name of the default line format for the default file handle. Normally, it is equal to the file handle's name.
$^-- Holds the name of the default heading format for the default file handle. Normally, it is equal to the file handle's name with _TOP appended to it.
$|-- If nonzero, will flush the output buffer after every write() or print() function. Normally, it is set to 0.
$$-- This UNIX-based variable holds the process number of the process running the Perl interpreter.
$?-- Holds the status of the last pipe close, back-quote string, or system() function.
$&-- Holds the string that was matched by the last successful pattern match.
$`- Holds the string that preceded whatever was matched by the last successful pattern match.
$'-- Holds the string that followed whatever was matched by the last successful pattern match.
$+-- Holds the string matched by the last bracket in the last successful pattern match. For example, the statement /Fieldname: (.*)|Fldname: (.*)/ && ($fName = $+); will find the name of a field even if you don't know which of the two possible spellings will be used.
$*-- Changes the interpretation of the ^ and $ pattern anchors. Setting $* to 1 is the same as using the /m option with the regular expression matching and substitution operators. Normally, $* is equal to 0.
$0-- Holds the name of the file containing the Perl script being executed.
$<number>-- This group of variables ($1, $2, $3, and so on) holds the regular expression pattern memory. Each set of parentheses in a pattern stores the string that match the components surrounded by the parentheses into one of the $<number> variables.
$[-- Holds the base array index. Normally, it's set to 0. Most Perl authors recommend against changing it without a very good reason.
$]-- Holds a string that identifies which version of Perl you are using. When used in a numeric context, it will be equal to the version number plus the patch level divided by 1000.
$"-- This is the separator used between list elements when an array variable is interpolated into a double-quoted string. Normally, its value is a space character.
$;-- Holds the subscript separator for multidimensional array emulation. Its use is beyond the scope of this book.
$!-- When used in a numeric context, holds the current value of errno. If used in a string context, will hold the error string associated with errno.
$@-- Holds the syntax error message, if any, from the last eval() function call.
$<- This UNIX-based variable holds the read uid of the current process.
$>-- This UNIX-based variable holds the effective uid of the current process.
$)-- This UNIX-based variable holds the read gid of the current process. If the process belongs to multiple groups, then $) will hold a string consisting of the group names separated by spaces.
$:-- Holds a string that consists of the characters that can be used to end a word when word-wrapping is performed by the ^ report formatting character. Normally, the string consists of the space, newline, and dash characters.
$^D-- Holds the current value of the debugging flags. For more information.
$^F-- Holds the value of the maximum system file description. Normally, it's set to 2. The use of this variable is beyond the scope of this book.
$^I-- Holds the file extension used to create a backup file for the in-place editing specified by the -i command line option. For example, it could be equal to ".bak."
$^L-- Holds the string used to eject a page for report printing.
$^P- This variable is an internal flag that the debugger clears so it will not debug itself.
$^T-- Holds the time, in seconds, at which the script begins running.
$^W-- Holds the current value of the -w command line option.
$^X-- Holds the full pathname of the Perl interpreter being used to run the current script.
</details>

<details>
<summary>What is <code>$@</code>?</summary><br><b>
</b></details>

<details>
<summary>What is difference between <code>$@</code> and <code>$*</code>?</summary><br><b>

`$@` is an array of all the arguments passed to the script
`$*` is a single string of all the arguments passed to the script
</b></details>

<details>
<summary>How do you get input from the user in shell scripts?</summary><br><b>

Using the keyword <code>read</code> so for example <code>read x</code> will wait for user input and will store it in the variable x.
</b></details>

<details>
<summary>How to compare variables length?</summary><br><b>

```
if [ ${#1} -ne ${#2} ]; then
    ...
```
</b></details>

#### Shell Scripting - Conditionals

<details>
<summary>Explain conditionals and demonstrate how to use them</summary><br><b>
</b></details>

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
<summary>How to perform arithmetic operations on numbers?</summary><br><b>

One way: `$(( 1 + 2 ))`
Another way: `expr 1 + 2`
</b></details>

<details>
<summary>How to perform arithmetic operations on numbers?</summary><br><b>
</b></details>

<details>
<summary>How to check if a given number has 4 as a factor?</summary><br><b>

`if [ $(($1 % 4)) -eq 0 ]; then`
</b></details>

#### Shell Scripting - Loops

<details>
<summary>What is a loop? What types of loops are you familiar with?</summary><br><b>
</b></details>

<details>
<summary>Demonstrate how to use loops</summary><br><b>
</b></details>

#### Shell Scripting - Troubleshooting

<details>
<summary>How do you debug shell scripts?</summary><br><b>

Answer depends on the language you are using for writing your scripts. If Bash is used for example then:

  * Adding -x to the script I'm running in Bash
  * Old good way of adding echo statements

If Python, then using pdb is very useful.
</b></details>

<details>
<summary>Running the following bash script, we don't get 2 as a result, why?

```
x = 2
echo $x
```
</summary><br><b>

Should be `x=2`
</b></details>

#### Shell Scripting - Substring

<details>
<summary>How to extract everything after the last dot in a string?</summary><br><b>

`${var//*.}`
</b></details>

<details>
<summary>How to extract everything before the last dot in a string?</summary><br><b>

${var%.*}
</b></details>

#### Shell Scripting - Misc

<details>
<summary>Generate 8 digit random number</summary><br><b>

shuf -i 9999999-99999999 -n 1
</b></details>

<details>
<summary>Can you give an example to some Bash best practices?</summary><br><b>
</b></details>

<details>
<summary>What is the ternary operator? How do you use it in bash?</summary><br><b>

A short way of using if/else. An example:

[[ $a = 1 ]] && b="yes, equal" || b="nope"
</b></details>

<details>
<summary>What does the following code do and when would you use it?

<code>diff <(ls /tmp) <(ls /var/tmp)</code>

</summary><br>
It is called 'process substitution'. It provides a way to pass the output of a command to another command when using a pipe <code>|</code> is not possible. It can be used when a command does not support <code>STDIN</code> or you need the output of multiple commands.
https://superuser.com/a/1060002/167769
</details>

<details>
<summary>What are you using for testing shell scripts?</summary><br><b>

bats
</b></details>

### Shell Scripting Exercises

|Name|Topic|Objective & Instructions|Solution|Comments|
|--------|--------|------|----|----|
|Hello World|Variables|[Exercise](hello_world.md)|[Solution](solutions/hello_world.md) | Basic
|Basic date|Variables|[Exercise](basic_date.md)|[Solution](solutions/basic_date.md) | Basic
|Great Day|Variables|[Exercise](great_day.md)|[Solution](solutions/great_day.md) | Basic
|Factors|Arithmetic|[Exercise](factors.md)|[Solution](solutions/factors.md) | Basic
|Argument Check|Conditionals|[Exercise](argument_check.md)|[Solution](solutions/argument_check.md) | Basic
|Files Size|For Loops|[Exercise](files_size.md)|[Solution](solutions/files_size.md) | Basic
|Count Chars|Input + While Loops|[Exercise](count_chars.md)|[Solution](solutions/count_chars.md) | Basic
|Sum|Functions|[Exercise](sum.md)|[Solution](solutions/sum.md) | Basic
|Number of Arguments|Case Statement|[Exercise](num_of_args.md)|[Solution](solutions/num_of_args.md) | Basic
|Empty Files|Misc|[Exercise](empty_files.md)|[Solution](solutions/empty_files.md) | Basic
|Directories Comparison|Misc|[Exercise](directories_comparison.md)|[Solution](solutions/directories_comparison.md) | Basic
|It's alive!|Misc|[Exercise](host_status.md)|[Solution](solutions/host_status.md) | Intermediate
