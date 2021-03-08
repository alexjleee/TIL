# CLI Basics

## Directory

> CRUD : `mkdir`(make directory) `ls`(list) `mv`(move) `rm`(remove)

> `cd`(change directory) `pwd`(print working directory)

Create : `mkdir` : make directory

- `mkdir dir1` : create a directory called 'dir1'
- `mkdir dir1 dir2 dir2` : create directories called 'dir1', 'dir2', 'dir3'
- `mkdir dir1/subdir` : create a directory called 'subdir' inside 'dir1' directory

Read : `ls` : list

- `ls` : list files and directories of the current directory
- `ls ..` : list files and directories of the **parent** directory one level above
- `ls ~` : list files and directories of the **home** directory
- `ls /` : list files and directories of the **root** directory
- `ls -a` : list files and directories including hidden ones
- `ls -l` : list files and directories with detailed information (size, modified date and time, owner, permission)
- `ls -R` : list all subdirectories

Update : `mv` : move

- `mv subdir dir2` : move 'subdir' directory into 'dir2' directory
- `mv dir newdir` : rename 'dir' directory 'newdir'

Remove : `rm` : remove

- `rm -r dir1` : remove 'dir1' directory

Change Directory : `cd`

- `cd ..` : change to the parent directory one level above

Print Working Directory : `pwd`

- `pwd` : print current directory path

## File

> CRUD : `touch` `cat`(concatenate) `mv` `rm`

> `open` `nano`(text editor)

Create : `touch`

- `touch text.txt` : create an empty file called 'text.txt'
- If a file with the same name already exists, it only change the modified time of the file to the current time.
- `touch text1.txt text2.txt text3.txt` : create multiple files at once

Read : `cat` : concatenate

- `cat text.txt` : display contents of the file 'text.txt'

Update : `mv`

- `mv text.txt ~` : move 'text.txt' into the home directory
- `mv text.txt newtext.txt` : rename 'text.txt' file 'newfile.txt'

Remove : `rm`

- `rm text.txt` : remove 'text.txt'

Open : `open`

- `open text.txt` : open 'text.txt' file
- `open -a "Visual Studio Code"` : open 'Visual Studio Code' program
- `open -a "Visual Studio Code" text.txt` : open 'text.txt' in 'Visual Studio Code'

Text Editor : `nano`

- `nano text.txt` : open the file called 'text.txt' (if there's no such file, create a new file)
- To save, press `Ctrl + O`
- To exit, press `Ctrl + X`
