# Directory Operations
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

