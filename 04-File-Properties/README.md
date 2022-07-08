# File Properties
1. `stat` ==>Display attributes and of files and directories.
2. `wc` ==>Count words, bytes, and lines in a file.
3. `du` ==>Measures the disk usage of the files and directories.
4. `file ` ==>Identify (guess) the type of a file.
5. `touch` ==>Change timestamps of files and directories.
6. `chown` ==>Change owner of files and directories. 
7. `chgrp` ==>Change group ownership of files and directories.
8. `chmod ` ==>Change protection mode of files and directories
9. `umask ` ==>Set a default mode for new files and directories.
10. `chattr ` ==>Change extended attributes of files and directories
11. `lsattr ` ==>List extended attributes of files and directories.
# 1) <ins> stat <ins>✅
`stat [options] files`
<br> ` stat ` is a command-line utility that displays detailed information about given files or file systems.
<br> For Example:
<br> `stat file.txt`
<br> ![statexamples](./Extras/file1.png)
<ins> **File** </ins>- The name of the file.
<br><ins> **Size** </ins>- The size of the file.
<br><ins>**Blocks** </ins>- The number of allocated blocks the file will takes.
<br><ins>**IO Blocks**</ins> - The size in bytes of every block.
<br><ins>**File type** </ins>- (ex. regular file, directory, symbolick link)
<br><ins>**Device**</ins> - Device number in hex and decimals
<br><ins>**Inode**</ins> - Inode number.
<br><ins>**Links** </ins>- Number of hard links.
<br><ins>**Access**</ins> - File permissions in the numeric and symbolick methods.
<br><ins>**Uid**</ins> - User ID and name of the owner
<br><ins>**Gid**</ins> - Group ID and name of the owner.
<br><ins>**Context** </ins>- The SELinux security context.
<br><ins>**Access** </ins>- The last time file was accessed.
<br><ins>**Modify** </ins>- The last time file content was modified.
<br><ins>**Change** </ins>- The last time the file's attribute or content was changed.
<br><ins>**Birth** </ins>- File creation time ( not supported in Linux)

### **Displaying information about file system.**
You can get information about file system where the given files resides, instead of information about the file itself use `-f` option.
<br> `stat -f file.txt`
![statexamples](./Extras/file2.png)
<ins> **File** </ins>- The name of the file.
<br><ins> **ID** </ins>- File system ID in hex.
<br><ins> **Namelen** </ins>- Maximum length of file names.
<br><ins> **Fundamental block size** </ins>- The size of each block on the file system.

<br><ins> **Blocks:** </ins>
<br> **Total** -  Number of total blocks in the file system.
<br> **Free** - Number of free blocks in the file system.
<br> **Available** - Number of free blocks available to non-root users.

<br><ins> **Inodes:**</ins>
<br> **Total:** - Number of total inodes in the file system.
<br> **Free:** -  Number of free inodes in the file system.

The `-t` option presents the same data but on a single line,
without headings. **This is handy for processing by shell scripts
or other programs**
![statexamples](./Extras/file3.png)

## <ins>Useful Options:</ins>
- (`-L`) ==>Follow symbolic links and report on the file they point to.
- (`-f`) ==>Report on the filesystem containing the file, not the file itself.
- (`-t`) ==>Terse mode: print information on a single line.

# 2) <ins> wc <ins>✅
`wc [options] [files]`
<br> The `wc` (word count) program prints a count of bytes, words,
and lines in (presumably) a text file:
<br> **`→ wc myfile`**
<br> <ins> 18 | 211 | 1168 |  myfile </ins>
<br> This file has `18 lines`, `211 whitespace-delimited words`, and
`1168 bytes`.

## <ins>Useful Options:</ins>
- (`-l`) ==>Print the line count only.
- (`-w`) ==>Print the word count only.
- (`-c`) ==>Print the byte count only.
- (`-L`) ==>Locate the longest line in each file and print its lenght in bytes.

# 2) <ins> du <ins>✅
`du [options][files | directories]`
<br> The `du` (disk usage) command measures the disk space occupied by files or directories. It is best applied to the specific directories and allows many variations for customizing the output to meet your needs. By default it measures the current directory and all its subdirectories, printing totals in blocks for each, with grand total at the bottom:
<br> <ins>Example: </ins>
  - ==> `du`
  <br> - `36 ======>./Mail`
  <br>- `340 ======>./Files/mine`
  <br>- `216 ======>./PC`

<br>It can also measure the size of the files:
<br> =====> **`du myfile emptyfile hugefile`**
<br> `4  myfile`
<br> `0 emptyfile`
<br> `18144 hugefile`

## <ins>Useful Options:</ins>
- (`-b`) ==>Measure usage in bytes.
- (`-k`) ==>Measure usage in kilobytes.
- (`-m`) ==>Measure usage in kilobytes.
- (`-h` or `--human-readable`) ==>Prints the files size output in human readable format.
![statexamples](./Extras/dufile1.png)
- (`-s` or  `--summarize`) ==>Print only the total size of the directory.Summarize.
![statexamples](./Extras/dufile2.png)
- (`--time`) ==>Shows the time of the last modification on file in the directory or the subdirectory that you run it against.
![statexamples](./Extras/dufile6.png)
- (`-a` or `--all`) ==>Lists the size of the all files and directories in the given file path. The `-a` option is often combined with the `-h` option for the Easy of use.
![statexamples](./Extras/dufile3.png)
- (`-c` or `--total`) ==>Add a line to the bottom of the output that gives you a grand total of all of the disk usage for the file path given.
![statexamples](./Extras/dufile4.png)
- (`-L`) ==>Follow symbolic links and measure the files they point to.
- (`-X` or `--exclude="pattern"`) ==>Useful if you want to exclude some files in the list. 
![statexamples](./Extras/dufile5.png)

# 2) <ins> file <ins>✅
`file [options] files`
The `file` command reports the type of the file. The output is an uducated guess based on the file content and other factors. File type may be of human-readable(e.g. ‘ASCII text’) or MIME type(e.g. ‘text/plain; charset=us-ascii’)
![statexamples](./Extras/file_1.png)

## <ins>Useful Options:</ins>
- (`-b`) ==>To show only file type.
![statexamples](./Extras/file_2.png)
![statexamples](./Extras/file_3.png)
- (`-i`) ==>Print the MIME types of files like the audio/mpeg or text/plain intstead of usual output.
![statexamples](./Extras/file_4.png)
- (`-f +name of the file`) ==>Read filenames, one per line, from the given file name and reports their types. Afterwards process filenames on the command line as usual.
- (`file *`) ==>Will display all the files and the directories.
- (`file directoryname/*`) ==>Will display all the files or the directories in the directories.
- (`file [a-z]*`) ==You can specify the range that you want to display.
- (`-s`) ==>For the special files.
- (`-L`) ==>Follows symbolic links, reporting the type of the destination file instead of the link.
- (`-z`) ==>Try to look inside compressed files. 
![statexamples](./Extras/file_5.png)


# 3) <ins> touch <ins>✅
`touch [options] files`
<br> The `touch` command changes two timestamps associated with a file; its modification time (when the files data was last changed) and its access time (when the file was last read). You can create a file with the touch command as well and if you want to change the files timestamp you can just run the file name with the touch:
<br>===>`touch myfile`
## <ins>Useful Options:</ins>
- (`-a`) ==>To change access time only.
![statexamples](./Extras/touch_1.png)
- (`-c`) ==>If the files doesnt exist do not create it (normally touch creates a file).
![statexamples](./Extras/touch_2.png)
- (`-m`) ==>Chages the modification time only. It will only update the modification time only.
![statexamples](./Extras/touch_3.png)
- (`-r`) ==>Updates the timestamp of the file with the file that you specify.For Example the file meena updates the timestamp with the file leena and the both files will hold  the same timestamp. the file to what you want to update and the file itself.
![statexamples](./Extras/touch_4.png)
- (`-d timestamp`) ==> updates the accessand modification times.
- (`-t timestamp`) ==>A more explicit way to set the files timestamp, using the format YY is the two digits for the year, MM is the two digits for the month, DD is the two digiti for the day, hh is the hour and mm is the minute, ss is the seconds. For emxaple -t 20030811140047 represents August 11, 2003, at 14:00:47
![statexamples](./Extras/touch_5.png)
- (`-c and -t`) ==> Can set the time explicitly.
![statexamples](./Extras/touch_6.png)

# 4) <ins> chown <ins>✅
`chown [options] user_spec files`
<br> The chown (change the owner) command sets the ownership fo files and directories. To make sure "alan" is the owner of several files and a directoies you can run: 
<br>` sudo chown alan file1 file2 file3 dir_name`
<br> The user *user_spec* paramter may be any of these possibilities:
- An existing username ( or any number user ID), to set the owner: or you can use chown -c option
<br> `chown alan file_name`
![statexamples](./Extras/chown_1.png)
![statexamples](./Extras/chown_2.png)
- An existing username (or any numeric ID), optionally followed by a clone and an existing group name (or any numeric group ID), to set the owner and group:
<br> `chown alan:any_group_name_or_ID file_name`
![statexamples](./Extras/chown_4.png)
- (`-v`) ==> It is used to show the verbose information for every file processed.
![statexamples](./Extras/chown_3.png)
- (`-f`) ==> Forcefully and silently change the ownership. 
- (`--from=old_owner_name_or id to new owner or id + file_name or directory_name`) ==> if you want to change the owner of the file from to the new ownner name or id and file_name
![statexamples](./Extras/chown_5.png)
- (`--from=:group_name or id  to new group owner or id + file_name or directory_name`) ==> if you want to change the owner of the file from to the new ownner name or id and file_name
![statexamples](./Extras/chown_6.png)
- To copy the ownership of one file to another:
![statexamples](./Extras/chown_7.png)
- To change the ownership of the multiple files:
![statexamples](./Extras/chown_8.png)
- (`-R`) ==> Recursively change permissions within a directory hierarchy.


# 4) <ins> chgrp <ins>✅
`chgrp [options] *group_spec* files`
<br> The chgrp (change group) command sets the group ownership of files and directories:
<br> `chgrp alan file1 file2 dir_name`
<br> The *group_spec* parmateters may be any of these possibilities:
- A group name or numeric group ID
- (`--reference=file`), to set the same group owner as another given file.
- (`-R`) ==> Recursively change permissions within a directory hierarchy.
- (`-- dereference`) Follows symbolic links and operate on the files they point to. 

# 5) <ins> chmode <ins>✅
