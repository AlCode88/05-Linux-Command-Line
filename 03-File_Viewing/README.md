# File Viewing
In Linux, you will encouneter files that contain readable text, and others that contain binary data that you want to view in a readable manner. This section is about how to display it is content in the most readable format.
- `cat` ==>View files in their entirety.
- `less` ==>View test files one page at a time.
- `nl` ==>View text files with their lines numbered.
- `head` ==>View the first lines of the text file.
- `tail` ==>View the last lines of the text file. 
- `strings` ==>Display text that is embedded in a binary file.
- `od` ==>View the data in octal (other formats).

## 1) <ins> cat <ins>✅
`cat [options] [files]`
<br> The simplest viewer is cat, which just prints it is files to standard output, concatinating them:
<br>`cat myfile` 
<br>Large files will likely scroll off the screen, so consider using `less` if you plan to read the output. Cat is extremely useful for sending a set of files into the shell pipeline:
<br>`cat myfile* | wc`
<br>Cat can also manipulate its output in small ways, optionally displaying nonprinitig characters, prepending line numbers (though the `nl` command is more powerful for this use case) and eliminating whitespace.
<br>Useful options:
- (`-T`) ==> Print tabs as ^I
- (`-E`) ==> Print newlines as $.
- (`-v`)*small* ==>Print other nonprinting characters in a human readable format.
- (`-n`) ==> Prepend line numbers to every line.
- (`-b`) ==> Prepend line numbers to nonblank lines. 
- (`-s`) ==> Squeeze each sequence of blank lines into a single blank line.

Examples:

- Some example on how using the `cat` command. 
- There are some examples on how to use <ins>`tac`</ins> ( reverse the cat) command. 
- The <ins>`rev`</ins> command will mix the words horizontally :) 
![catexamples](./README.md_Extras/file1.png) ![catexamples](./README.md_Extras/file2.png)
![catexamples](./README.md_Extras/file3.png) ![catexamples](./README.md_Extras/file4.png)
![catexamples](./README.md_Extras/file5.png) ![catexamples](./README.md_Extras/file6.png)

## 2) <ins> less <ins>✅
`less [options] [files]`
<br>Use less to view text one “page” at a time (i.e., one window or
screenful at a time):
<br>→ `less myfile`
<br>It’s great for text files, or as the final command in a shell pipeline with lengthy output:
<br>→ `command1 | command2 | command3 | command4 | less`
While running less, type `h` for a help message describing all its
features. Here are some useful keystrokes for paging through
files:

| Keystroke|       Meaninng        |
|----------|:-------------------:  |
| `h, H`   |  View a help page     |
| `Space bar, f, ^V, ^F`       |Move forward one screenful.                     |
| `Enter`  |            Move forward one line.           |
| `b, ^B, ESC -v`|  Move backward one screenful.         |
| `/` | Enter search mode. Follow it with a regular expression and press Enter, and `less` will look for the                                  first matching line.|
|`?` | Same as `/`, but it searches backward in the file. 
|`n`|Next match: Repeat your most recent search forward    |
|`N`| Repeat your most recent search backward. |
|`v`| Edit the current file with your default text editor (the value of environment variable VISUAL, or if not defined, EDITOR, or if not defined, the program `vi`).|
|`<, g`| Jump to beginning of file.|
|`>, G`| Jump to end of file.|
|`:n`|   Jump to next file.|
|`:p` |  Jump to previous file.|

Notes:
<br> `less` has a mind-boggling number of features; we’re presenting only the most common. (For instance, less will display the contents of a compressed `Zip file`: try `less myfile.zip.`) The manpage is recommended reading.

<br>Useful options:
- (`-c`) ==> Clear the screen before displaying the next page. This avoids scrolling and may be more comfortable on the eyes.
- (`-m`) Print a more verbose prompt, displaying the percentage of the file displayed
so far.
- (`-N`) ==> Display line numbers.
- (`-r`) ==> Display control characters literally; normally `less` converts them to a human-readable format. 
- (`-s`) ==> Squeeze multiple, adjacent blank lines into a single blank line.
- (`-S`) ==> Truncate long lines to the width of the screen, instead of wrapping.

Examples:
![lessexamples](./README.md_Extras/less1.png) 
![lessexamples](./README.md_Extras/less2.png)
![lessexamples](./README.md_Extras/less3.png)

## 3) <ins> nl <ins>✅
`nl [options] [files]`
<br>`nl` command is a Unix/Linux utility that is used for numbering lines, accepting input either from a file or from STDIN. It copies each specified file to STDOUT, with line numbers appended before the lines. 

<ins>Options and Examples:</ins>
-  **To display a file with line numbers:** Numbers all non-empty lines.
<br> `nl file.txt`

![nlexamples](./README.md_Extras/nl1.png)
- (`-b`) NUMBER or -bNUMBER : used for numbering body lines
<br> `nl -b a geekfile.txt`

![nlexamples](./README.md_Extras/nl2.png)
- (`-i`) NUMBER or -iNUMBER : line number increment at each line. Override default increment: The default increment pattern in Linux is 1. This can be changed using the `-i` option. The first line number is 1 and cannot be changed using `-i`.
<br> `nl -i 3 geekfile.txt or nl -i3 geekfile.txt`

![nlexamples](./README.md_Extras/nl3.png)
- (`-n`) FORMAT or -nNUMBER : insert line numbers according to FORMAT. To print the lines using a different number format: The numbering formats can be specified using the `-n` option. The default numbering format is `rn`.
  - ```ln -> left-justified, no leading zeros```
  - `rn -> right-justified, no leading zeros`
  - `rz -> right-justified with leading zeros`

![nlexamples](./README.md_Extras/nl4.png)
- (`-v`) NUMBER or -vNUMBER : change first line number of the given input. To make the starting line number different: The default line number is 1. This can be changed using the `-v` option.
<br> `nl -v 4 geekfile.txt or nl -v4 geekfile.txt`

![nlexamples](./README.md_Extras/nl5.png)
- (`-l`) NUMBER or -lNUMBER : group of NUMBER empty lines are counted as one
- (`-s`) STRING or -sSTRING : add any STRING after every logical line numbe. Add a string literal after line numbers: Any STRING literal can be added after a line number using the `-s` option.
<br> `nl -s "..." geekfile.txt`

![nlexamples](./README.md_Extras/nl6.png)
- (`-w`) NUMBER or -wNUMBER : use different NUMBER columns for line numbers. Change column for line numbers: Different columns can be used to display the file output using the `-w` option. The default column number is 1.
<br>`nl -w2 geekfile.txt`
<br>`nl -w4 geekfile.txt`
<br>`nl -w6 geekfile.txt`
<br>or
<br>`nl -w 2 geekfile.txt`
<br>`nl -w 4 geekfile.txt`
<br>`nl -w 6 geekfile.txt`
<br> Notice the change in column number (increase in indentation from left) in the example illustrated below.

![nlexamples](./README.md_Extras/nl7.png)

## 4) <ins> head <ins>✅
`head [options] [files]`
<br> The head command prints the first 10 lines of a file, which is great for previewing the contents:
<br> ` head myfile`
<br> `head myfile* | less`  *Previewing multiple files* 

<br> It’s also good for previewing the first few lines of output from a
pipeline—say, the most recently modified 10 files in the current
directory:
<br> `→ ls -lta | head`
<br> `$ ls -t | head -n 3 | sort`
<br> c.txt
<br> d.txt
<br> e.txt

### Useful options:
- (`-n`) N Print the first N lines instead of 10.
<br> `head -n 5 state.txt`
<br>`Line 1`
<br>`Line 2`
<br>`Line 3`
<br>`Line 4`
<br>`Line 5`

- (`-N`) Same as -n N.

- (`-c`) N Print the first N bytes of the file.
<br>`head -c 6 state.txt`
<br> `Line 6`
- (`-q`) Quiet mode: when processing more than one file, don’t print a banner
above each file. Normally, head prints a banner containing the filename. `-q` is useful for multiple files to list it in the alphabetical order.
<br> `head -q  state.txt capital.txt`

- (`-v`) By using this option, data from the specified file is always preceded by its file name
<br> `head -v state.txt`

## 5) <ins> tail <ins>✅
`tail [options] [files]`
<br> The tail command prints the last 10 lines of a file, and does other tricks as well:
<br>`tail myfile`
<br> `nl myfile | tail See line numbers too`

### Useful options
![nlexamples](./README.md_Extras/tail1.png)
<br> - The ultra-useful `-f` option causes tail to watch a file actively while another program is writing to it, displaying new lines. This is invaluable for watching a Linux log file in active use, as other programs write to it. This is commonly used to watch log files in real-time. As new lines are written to the log the console will update will new lines.
- (`-f`)
`tail -f /var/log/syslog`

![nlexamples](./README.md_Extras/tail2.png)
![nlexamples](./README.md_Extras/tail3.png)

- (`-n`) N Print the last lines in the file by defuault it is 10 lines.
- (`-N`) Same as -n N.

![nlexamples](./README.md_Extras/tail4.png)

- (`-n`) +N Print all lines except the first N.
For command: tail +n file_name, data will start printing from line number ‘n’ till the end of the file specified.

![nlexamples](./README.md_Extras/tail5.png)

- (`-q`) Quiet mode: when processing more than one file, don’t print a banner above each file. Normally tail prints a banner containing the
filename. 

![nlexamples](./README.md_Extras/tail6.png)

<<<<<<< HEAD
## 5) <ins> string <ins>✅
string [options][files]
First you need to install packages for to use strings command.  `binutils`
<br>Binary files, such as executable programs and object files, usually contain some readable text. The strings program extracts
that text and displays it on standard output. You can discover
version information, authors’ names, and other useful tidbits
with strings:
<br> `→ strings /usr/bin/who`
=======
## 5) <ins> strings <ins>✅
>>>>>>> 1465217 (Linux Mastering Command Line)
