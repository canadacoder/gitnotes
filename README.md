Welcome to the Unix Shell session of the Research Computing Workshop

1 - Red
2 - Green
3 - Blue
4 - Yellow

Lesson:    http://swcarpentry.github.io/shell-novice/
Reference: https://www.sharcnet.ca/help/index.php/Using_Unix_Overview
Data:      http://swcarpentry.github.io/shell-novice/shell-novice-data.zip

data-shell
+-- creatures
+-- data
¦   +-- elements
¦   +-- pdb
+-- Desktop
+-- molecules
+-- north-pacific-gyre
¦   +-- 2012-07-03
+-- writing
    +-- data
    +-- old
    +-- thesis
    +-- tools
        +-- old

look up command by googling: <command> man page

whoami -- who am i
pwd -- print working directory
cd <dir> -- change to directory <dir>
ls [-l] [-F] [-R] -- list files
rm [-r] <file> ... -- remove files
mkdir <dir> -- make directory <dir>
rmdir <dir> -- remove directory <dir>
mv <file1> <file2> -- rename <file1> to <file2>
mv <file> ... <dir> -- move <file> ... to directory <dir>
cp <file1> <file2> -- copy <file1> to <file2>
cp <file> ... <dir> -- copy <file> ... to directory <dir>
man <command> -- Display manual page for <command> Example: man mkdir
tree <dir> -- List directories in a tree view
wc <filenames> -- word count, default output is line count, word count, character count
touch -- creates a blank file
wget <url> -- download file
unzip <file> -- unzip the contents of zip file <file>

<command> -- run command and print output to screen
<command> < <input-file> -- run command and take input from <input-file>
<command> > <output-file> -- run command and save output to <output-file> (Note: Overwrites previous file)
<command1> | <command2> ... -- run <command1> and put output into <command2>

<Cursor Up> -- Go back one step in command-line history
CTRL + r -- Recursive search command-line history
CTRL + c -- Abort current command
CTRL + d -- End of input (on a new line)
Pattern matching "Globbing":
* -- Select all or nothing, Ex: word count all PDB files in the directory: wc *.pdb
? -- Single character match
[...] -- match any of the enclosed characters, Ex: [AB] matches A or B
{...} -- expand out once for each listed value, Ex: file.{exe,txt} is the same as file.exe file.txt

Standard Text Editors:
nano <filename.txt>
vi <filename.txt>
emacs <filename.txt>

If you have TextWrangler,
tw <filename.txt>

Creating new txt files
touch <commandname>


## If pwd displays /Users/thing, what will ls ../backup display?

1. ../backup: No such file or directory
2. 2012-12-01 2013-01-08 2013-01-27
3. 2012-12-01/ 2013-01-08/ 2013-01-27/
4. original pnas_final pnas_sub


alternative to list the same thing using absolute paths

ls /Users/backup

what does the -s option mean
print the size? 
print the allocated size of each file, in blocks

what does the -h option mean
ls -h means human read-able size format (used with -l), for example 1K 234M 2G


# Questions

## Many ways to do the same thing - absolute vs relative paths

For a hypothetical filesystem location of /home/amanda/data/,
select each of the below commands that Amanda could use to
navigate to her home directory, which is /home/amanda

1. cd .
2. cd /
3. cd /home/amanda
4. cd ../..
5. just cd .. will also work -- correct
6. cd ~ -- correct
also cd by itself (didn't teach this one) or the third one (cd /home/amanada)

## What is the output of the closing ls command in the sequence
shown below?

$ pwd
/Users/jamie/data
$ ls
proteins.dat
$ mkdir recombine
$ mv proteins.dat recombine
$ cp recombine/proteins.dat ../proteins-saved.dat
$ ls

R1. proteins-saved.dat recombine
G2. recombine
B3. proteins.dat recombine
Y4. proteins-saved.dat

## Say your directory contains file1 file2 and file3.  Make a for loop to make a copy of these files as file1-backup file2-back and file3-backup.


steps

1 - do the first couple of examples by hand and copy the commands to a file (or on a piece of paper)
2 - look at the commands and identify the pattern
3 - create a template from what you have identified
4 - wrap the template with a for statement

for <varname> in <value1> <value2> ...
do
  <command>
  ...
done

bonus: get it to print the command it runs without using "set -x" (good for debugging)
bonus: try to do the same thing with file names with spaces in them (e.g., "file 1", "file 2", "file 3")

$name -- put in the value of <name>
${name} -- put in the value of <name>
${name%pattern} -- put in the value of <name> with <pattern> removed from end
${name#pattern} -- put in the value of <name> with <pattern> removed from the start
${name/pattern/substitution} -- put in the value of <name> with <pattern> repaced with <substitution>

bonus: repeat above but copy file1.txt to file1-backup.txt, file2.txt to file2-backup.txt, etc.

bash <scriptfile> <arguments> ... -- run the commands in <scriptfile> replacing $* with <arguments> ...

# SHARCNET

sqsub -r <runtime> -q <queue> -o <logfile> <command> <arguments> ...
- submit <command> <arguments> ... to the list of programs to run at sometime in the future
- specify it requires <runtime> to run (add some extra but not too much)
- specify it require <queue> (normally serial, but also gpu or mpi)
- specify the log of the run is to be saved in <logfile>
sqjobs -- list my jobs
sqkill <jobid> -- cancel job

sqsub -r 5m -q gpu -o output-NENE01729A.txt bash goostats NENE01729A.txt stats-NENE01729A.txt

for input in N*[AB].txt
do
  echo sqsub -q gpu -r 5m -o log-$input bash goostats $input stats-$input   -- run first with echo to check
done

for input in N*[AB].txt
do
  sqsub -q gpu -r 5m -o log-$input bash goostats $input stats-$input
done

## Getting a personal account

https://www.sharcnet.ca/help/index.php/Getting_an_Account_with_SHARCNET
https://ccdb.computecanada.ca


## Lab accounts

Use eduroam or uwo-secure if you can.  If not use SS2015-2.  If you fail to login too many times your internet address will be locked out.

password: 8mdD5n-XX (where XX matches the number in labXX)

lab01-- Tyson
lab02-- Haidy
lab03-- Chen
lab04-- Jacob
lab05-- James
lab06-- Masoud-Armin
lab07 -- Gordon!  8mdD5n-07
lab08
lab09 -- Sina
lab10 -- Steve
lab11 -- Abhishek
lab12-- Violet
lab13
lab14 -- Mahnaz
lab15
lab16
lab17--Ayushi Gaur
lab18
lab19
lab20
lab21
lab22
lab23--Erika
lab24
lab25
lab26
lab27
lab28
lab29
lab30

Welcome to the GIT research computing workshop

Installing

MAC OSX - https://sourceforge.net/projects/git-osx-installer/files/
(pick most recent -- if works you should be able to type "git" at the command line)

Windows - should already be installed from bash workshop, if you weren't there
https://git-for-windows.github.io/

Linux - possibly already installed, if "git" at the command doesn't work
Ububtu/Debian: sudo apt-get install git
Fedora: sudo dnf install git

# Configuration 

Global configuration stored under ~/.gitconfig. Local configuration store$ 

```bash 
git config --global user.name "Tyson Whitehead"   
git config --global user.email "twhitehead@gmail.com" 
```
```bash
git config --global color.ui auto
```
```bash 
git config --global core.editor nano
```

# Initialization 

Creates the .git directory. To undo `rm -r .git`. 

```bash 
mkdir $folder
cd $folder
git init
```

# Creating the next version

First view the status to see where things are at

```bash
git status
```

Add the changes you want in the next version (the `-p` option asks you change by change and is not required to just add everything)

```bash
git add -p $file
```

If you want to remove a file

```bash
git rm $file
```

# Save the next version

To save the next version run

```bash
git commit
```

For a log message, describe why you made the change, not what change you made as the computer can tell you the latter but not the former. Make the first line a brief oneline overview.