# 05-Linux-Command-Line
# BASIC FILE OPERATIONS
###################################################################################
####################         ls - cp - mv - rm - ln           #####################
###################################################################################
# Commands to learn
- `ls` ==>List in a file directory
- `cp` ==>Copy a file
- `mv` ==>Rename ("move") file.
- `rm` ==>Delete ("remove") file.
- `ln` ==>Create a links ( alternative names) to a file.

## <ins> ls <ins> ✅
`ls [options][files]`
<br> The `ls` comamnd lists the attriburtes of files and directories. You can list files in the current directory:

### Useful options for `ls`
 `-a` Lists all files including the hidden files.
<br> `-l`  Long list including the file attributes. Add the `-h` option and it will became the humand readable format for the size of the files.
<br> `-G` in a long list do not print the group ownership of the file.
<br> `-S` sort the file by their size.
<br> `-t` Sort the file by the time they last modified.
<br> `-r` Reverse the sorted order.
<br> `-d` If listing a directory do not list it is content just the directory itself.


## <ins> cp <ins> ✅
`cp [options] file (file | directory)`
<br> The `cp` command normally copies files:
<br> `cp myfile another_file` <br>or you can copy multiple files into a directory (mydir)
<br> `cp myfile myfile2 myfile3 myfile4 mydir`

<br> Note: Using `-a` or `-r` options, you can copy the directories recursevly.

### Useful Options 
(`-p`) Copy not only the content but also the file permissions, timestamp, and if you habe enough permissions to do so, it will copy it is owner and group.
<br> (`-a`) Copy the directory hiererachy recursevly, preserving all files attributes and links.
<br> (`-r`) Copy the directory hiererachy recursevly. This option does not preserve the files attributes such as permissions and timestamps. It does not preserve symbolic links.
<br> (`-i`) Inteactive mode. Ask before overwriting destination files.
<br> (`-f`) Force the copy. If a destination file exists, ovewrite it unconditionally.

## <ins> mv <ins> ✅
`mv [options] sorce target`
<br> The mv (move) command can rename a file:
<br> `mv somefile newfilename`
<br> or move files and directories into a destination directory:
<br> `mv myfile myfile2 dir1 dir2 destination_directory_name`

### Useful Options
(`-i`) Interactive mode. Ask before overwriting destination files.
<br>(`-f`) Force the move. If a destination file exists, overwrite it unconditionally. 

## <ins> rm <ins> ✅
`rm [options] files | directories`
<br> The `rm` (remove) command can delete files:
<br> `rm deleteme deleteme2`
<br> or recursively delete directories:
<br> `rm -r dir1 dir2`

### Useful Options
(`-i`) Interactive mode. Ask before deleting each file.
<br>(`-f`) Force to deletion ignoring any errors or warnings.
<br> (`-r`) Recursively remove a directory and it is contents. Use with caution, especially if combined with the `-f` option, as it can wipe out all your files. 

## <ins> ln <ins> ✅
`ln [options] source target`
<br> A *link* is a referece to another file, created by the `ln` command. Intuitively, links give a the same file multiple names, allowing it to live in two (or more) locations at once.
There are two types of links.
<br> 1)<ins> **Symbolic Link** </ins> (also called *sym-link* or *soft link*) refers to another file by it is path, much like a Windows "short cut" or Mac aliase. To create a symbolic link use `-s` option. If you delete the original file, the sym-link will be invalid, pointing to non-existing file path.
<br> `ln -s file_name_A file_name_B`
<br> 2) <ins>**Hard Link:** </ins> On the other hand it is a *second name* for a physical file on disk (it points to the same indoe). If you delete the original file, the link works. 
<br> `ln file_name A file_name B`\
Note: 
- Symbolic links can point to files on other disk partitions as they are just a reference to the file path; hard links can not, because an inode on one disk has no meaning on another. 
- Symbolik links can also point to directories wherease hard links can not unless you are the superuser and use the `-d` option.
- To find out where a symbolic link points run either of the following commands that shows the path to the link. 
<br> `readlink examplelink  => original_file_name` 
<br> or `ls -l examplelink  => lwrxwrxwrx  1 al  .... examplelink => original_file_name`
- Symbolic link can point to another symbolic links. To find out the whole chain use `readlink -f link_name` option. 

## Useful Options to *ln* command. 
(`-s`) Make a symbolic link instead of hard link.
<br> (`-i`) Interactive mode. Ask before overwriting destination files.
<br> (`-f`) Force the link. If a destination file exists, overwrite it unconditionally.
<br> (`-d`) Create a hard link to a directory (super user only)

# Directory Operations
############################################################################################################################
#############################     cd - pwd - basename - mkdir - rmdir - rm -r      #########################################
############################################################################################################################
### This section of the command line helps you to modify, create, delete and manipulate the directories within that structure

- `cd` ==> Change your current directory 
- `pwd`==> Print the name of the current directory.
- `basename`==> Print the final part of the path
- `mkdir`==> Create (make) directory 
- `rmdir`==> Delete (remove) and empty directory
- `rm -r`==> Delete non empty directory and it is content

## 1) <ins> cd <ins>✅
`cd [directory]`
<br> The `cd` (change directory) command sets your current working directory: 
<br> => `cd /usr/games`
<br> With no directory supplied `cd` will bring you to the users home directory:
<br> `cd`

## 2) <ins> pwd <ins>✅
`pwd`
<br> The `pwd` command prints the absolute path of your current working directory:
`Pwd `=>    `/user/al/current_directory`

## 3) <ins>  basename <ins>✅
`Basename path [extension]` 
<br> The `basename` command prints the final component in the file path: 
<br> `basename /users/smith /financemoney/money.txt`
<br> The result will come up as =>  `money.txt`
<br> If you provide an optional extension, it gets stripped from the result
<br> `basename /users/smith/finance/money.txt  .txt` => 
money

## 4) <ins> dirname <ins>✅
`dirname path`
<br> The dirname command prints a file path with its final component removed: 
<br> `dirname /users/smith/mydir` => 
`/users/smith`
<br> `dirname` does not change your current working directory, it simply manipulates and prints the string just like the `basename` does.

## 5) <ins> mkdir <ins>✅
`mkdir [options] directories`
<br> `mkdir` Creates one or more directories:
<br> `mkdir directory1 directory2 directory3`
Useful options:
- (`-p`) ==>  Given a directory path (not just a simple directory name), creates any necessary parent directories automatically. The command: 
<br> `mkdir -p one/two/three` 
<br> Creates one, after one => two and after two => three if they already don’t exists. 
-  (`-m`)  means *mode* Creates directory with the given permissions: 
<br> `mkdir -m 0755 publicdir`

## 6) <ins> rmdir <ins>✅
`rmdir [options] directories`
<br> The `rmdir` (remove directory) command will remove one or more empty directories you name:
<br>`mkdir /tmp/empty_dir`
<br>`rmdir /tmp/empty_dir`
<br>Useful Options:
- (`-p`) if you supply a directory path ( not just a simple directory name), delete not only the given directory but the specified parent directories automatically, all of which must be empty. <br> So `rmdir -p one/two/three` will delete not only one/two/three but also one and two and three.

<br>**Note:** 
<br>To delete nonempty directory and it is contents, use (carefully)  `rm -r directory_name`. Use `rm -ri` to delete interactively or `rm -rf` to force the deletion without any error messages or confirmation. 

# File Viewing
####################################################################################
##########################         VIM      ########################################
####################################################################################
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
![catexamples](./extras-file-viewing/file1.png) ![catexamples](./extras-file-viewing/file2.png)
![catexamples](./extras-file-viewing/file3.png) ![catexamples](./extras-file-viewing/file4.png)
![catexamples](./extras-file-viewing/file5.png) ![catexamples](./extras-file-viewing/file6.png)

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
![lessexamples](./extras-file-viewing/less1.png) 
![lessexamples](./extras-file-viewing/less2.png)
![lessexamples](./extras-file-viewing/less3.png)

## 3) <ins> nl <ins>✅
`nl [options] [files]`
<br>`nl` command is a Unix/Linux utility that is used for numbering lines, accepting input either from a file or from STDIN. It copies each specified file to STDOUT, with line numbers appended before the lines. 

<ins>Options and Examples:</ins>
-  **To display a file with line numbers:** Numbers all non-empty lines.
<br> `nl file.txt`

![nlexamples](./extras-file-viewing/nl1.png)
- (`-b`) NUMBER or -bNUMBER : used for numbering body lines
<br> `nl -b a geekfile.txt`

![nlexamples](./extras-file-viewing/nl2.png)
- (`-i`) NUMBER or -iNUMBER : line number increment at each line. Override default increment: The default increment pattern in Linux is 1. This can be changed using the `-i` option. The first line number is 1 and cannot be changed using `-i`.
<br> `nl -i 3 geekfile.txt or nl -i3 geekfile.txt`

![nlexamples](./extras-file-viewing/nl3.png)
- (`-n`) FORMAT or -nNUMBER : insert line numbers according to FORMAT. To print the lines using a different number format: The numbering formats can be specified using the `-n` option. The default numbering format is `rn`.
  - ```ln -> left-justified, no leading zeros```
  - `rn -> right-justified, no leading zeros`
  - `rz -> right-justified with leading zeros`

![nlexamples](./extras-file-viewing/nl4.png)
- (`-v`) NUMBER or -vNUMBER : change first line number of the given input. To make the starting line number different: The default line number is 1. This can be changed using the `-v` option.
<br> `nl -v 4 geekfile.txt or nl -v4 geekfile.txt`

![nlexamples](./extras-file-viewing/nl5.png)
- (`-l`) NUMBER or -lNUMBER : group of NUMBER empty lines are counted as one
- (`-s`) STRING or -sSTRING : add any STRING after every logical line numbe. Add a string literal after line numbers: Any STRING literal can be added after a line number using the `-s` option.
<br> `nl -s "..." geekfile.txt`

![nlexamples](./extras-file-viewing/nl6.png)
- (`-w`) NUMBER or -wNUMBER : use different NUMBER columns for line numbers. Change column for line numbers: Different columns can be used to display the file output using the `-w` option. The default column number is 1.
<br>`nl -w2 geekfile.txt`
<br>`nl -w4 geekfile.txt`
<br>`nl -w6 geekfile.txt`
<br>or
<br>`nl -w 2 geekfile.txt`
<br>`nl -w 4 geekfile.txt`
<br>`nl -w 6 geekfile.txt`
<br> Notice the change in column number (increase in indentation from left) in the example illustrated below.

![nlexamples](./extras-file-viewing/nl7.png)

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
![nlexamples](./extras-file-viewing/tail1.png)
<br> - The ultra-useful `-f` option causes tail to watch a file actively while another program is writing to it, displaying new lines. This is invaluable for watching a Linux log file in active use, as other programs write to it. This is commonly used to watch log files in real-time. As new lines are written to the log the console will update will new lines.
- (`-f`)
`tail -f /var/log/syslog`

![nlexamples](./extras-file-viewing/tail2.png)
![nlexamples](./extras-file-viewing/tail3.png)

- (`-n`) N Print the last lines in the file by defuault it is 10 lines.
- (`-N`) Same as -n N.

![nlexamples](./extras-file-viewing/tail4.png)

- (`-n`) +N Print all lines except the first N.
For command: tail +n file_name, data will start printing from line number ‘n’ till the end of the file specified.

![nlexamples](./extras-file-viewing/tail5.png)

- (`-q`) Quiet mode: when processing more than one file, don’t print a banner above each file. Normally tail prints a banner containing the
filename. 

![nlexamples](./extras-file-viewing/tail6.png)

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


# VIM
####################################################################################
##########################         VIM      ########################################
####################################################################################
# <ins> vim <ins>✅
`vim [options][files]`
<br>On Unix-like operating systems, `vim`, which stands for `"Vi Improved"`, is a text editor. It can be used for editing any kind of text and is especially suited for editing computer programs.

## Command execution
<br> `gvim` - to invoke the editor in a new window.
<br> `vim` - to run existing shell window:
<br> `vimtutor` - to run the vim tutorial

## Basic Keystrokes in the `vim`
| Taks     | VIM Commands |
| ----------- | ----------- |
| To Start to type text     | **Switch to `i` - insert mode and start to type anything that you want**      |
| Save and quit |**`:wq`**        |
| Quit without saving   | **`:q!`**    |
| Save   | **`:w`**        |
| Save As   |  **`:w filename`** |
| Undo  |   **`u`**   |
| Redo | **`^R`**        |
| Copy the line  | **`yy`**        |
| Paste the line  | **`p`**        |
| To switch to the Visual mode / handy when you want to slect many lines of codes | **`V`**        |
| To add an empty line and puts you to the insert mode  | **`o`**        |
| Add the line above and puts you into insert mode  | **`O`**        |
| Switch to insert mode| **`i`**       |
| Switch to command mode    |**`ESC`** |
| Switch to command-line mode   | **`:`**       |
| Move forward    |**`l or right arrow`**       |
| Move backward    | **`h or left arrow`**       |
|Move up   | **`k or up arrow`**        |
| Move down   | **`j or down arrow`**       |
| To jump to the line number | **`: number of the line`**        |
| Move to next word   | **`w`**       |
| Jump to the next space  | **`W`**        |
| Move to previous word  | **`b`**      |
| Move to beginning of line   |**`0w`**       |
| Move to end of line   | **`$`**        |
| Move down one screen    | **`^f`**         |
| Move to beginning of documen | **`gg`**       |
| Move to end of document  | **`G`**        |
| Delete next character  | **`x`**        |
| Delete previous character   | **`X`**        |
| Delete next word  | **`de`**        |
| Delete previous word  | **`db`**        |
| Delete current line   | **`dd`**        |
| To delete a word  | **`dw`**        |
| Just to delete what you have selected or the single character | **`d`**        |
| Delete to end of line  | **`D`**        |
| Move text to the next blocks  | **`{ barce }`**        |
| You can move by numbers / will take you 10 lines down  | **`10 j`**        |
| Move up one screen  | **`^b`**        |
