# Learn command line

Please follow and complete the free online [Bash Scripting Tutorial](https://ryanstutorials.net/bash-scripting-tutorial/) or [Codecademy's Learn the Command Line](https://www.codecademy.com/learn/learn-the-command-line). These are helpful tutorials. You should be able to go through these in a couple of hours.

**Note:** Bash is not installed on a PC. Rather, PC users must install Cygwin. Once Cygwin has been installed, the command line interface witll _emulate_ bash. You can find all information regarding Cygwin [here](https://www.cygwin.com/).

---

### Q1.  Cheat Sheet of Commands  

Here's a list of items with which you should be familiar:  
* show current working directory path
* creating a directory
* deleting a directory
* creating a file using `touch` command
* deleting a file
* renaming a file
* listing hidden files
* copying a file from one directory to another

Make a cheat sheet for yourself: a list of at least **ten** commands and what they do.  (Use the 8 items above and add a couple of your own.)  

> > * show current working directory path: `pwd`  
> > * creating a directory: `mkdir <directory name>`  
> > * deleting a directory: `rmdir <directory name>` (if the  directory is empty) else use `rm -r <directory name>`   
> > * creating a file using `touch` command: `touch <filename>`  
> > * deleting a file: `rm <filename>`   
> > * renaming a file: `mv <filename1> <filename2>`
> > * listing hidden files: `ls -a` (but it will also list other files)
> > * copying a file from one directory to another: `cp <filename> destination_directory/`
> > * pipe operator to redirect standard output of the previous command to the next command: `|`  
> > * search for a specific text in a file or files: `grep <specific string> <filename>`    
> > * read an inpt file without needing to print the whole content on the terminal: `less <filename>`  
> > * sorts the lines of a text file alphabetically: `sort <filename>`  
> > * redirect the standard output of a command to a new or existing file: `>`   
> > * append the standard output of a command to an existing file: `>>`  

---

### Q2.  List Files in Unix   

What do the following commands do:  
`ls`  
`ls -a`  
`ls -l`  
`ls -lh`  
`ls -lah`  
`ls -t`  
`ls -Glp`  

> > `ls`: list the files and directories in the current working directory  
> > `ls -a`: list all the contents, including hidden files in the current working directory  
> > `ls -l`: list the files in the long list format in the current working directory  
> > `ls -lh`: list the files in the long list format with readable file size  
> > `ls -lah`: list all the contents, including hidden files, in long list format with readable file size  
> > `ls -t`: list the files and directories that are sorted by their last modified date and time  
> > `ls -Glp`: list the files and directories in the long list format, excuding the group ID or owner name. The -p option includes a / at the end of the directories' names  

---

### Q3.  More List Files in Unix  

Explore these other [ls options](http://www.techonthenet.com/unix/basic/ls.php) and pick 5 of your favorites:

> > `-a`  
> > `-l`  
> > `-t`  
> > `-R`  
> > `-u`  

---

### Q4.  Xargs   

What does `xargs` do? Give an example of how to use it.

> > It takes the items from standard input, and executes a command with these items, as its arguments, one at a time.  
> > Here is an example of a command line using `xargs` to create 5 new directories in your working directory.  
> >       `echo "file1 file2 file3 file4 file5" | xargs mkdir`  
> > Here, the standrad output from `echo` command (i.e., the five strings) are redirected to `xargs` command and becomes the arguments for the `mkdir` command with which each will be executed one at a time. Thus, `mkdir` is automatically ran 5 times to create 5 new directories.  
        
