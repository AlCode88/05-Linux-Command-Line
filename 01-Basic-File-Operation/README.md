# Basic File Operation
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

### Useful Options to *ln* command. 
(`-s`) Make a symbolic link instead of hard link.
<br> (`-i`) Interactive mode. Ask before overwriting destination files.
<br> (`-f`) Force the link. If a destination file exists, overwrite it unconditionally.
<br> (`-d`) Create a hard link to a directory (super user only)