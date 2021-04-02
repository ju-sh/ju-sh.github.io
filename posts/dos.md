# DOS Commands for Linux users

 - Date created: 28-Mar-2021

As seen in Windows XP.

---

# Cheatsheet

Similar commands. Not exact same ones. There are differences.

    Linux   | DOS
    --------+--------
    ls      | DIR
    cp      | COPY
    cd      | CD or CHDIR
    pwd     | CD
    clear   | CLS
    cat     | TYPE
    edit    | Launch editor
    rm      | DEL or ERASE
    echo    | ECHO
    man     | HELP
    diff    | FC
    rmdir   | RMDIR or RD
    mkdir   | MKDIR or MD
    chmod   | ATTRIB
    grep    | FIND (and FINDSTR ?)
    free    | MEM
    more    | MORE
    mv      | MOVE
    ping    | PING
    sort    | SORT
    date    | DATE

Options in DOS start with `/` as in `/a` instead of `-a` in Linux.

Help text of DOS commands is usually obtained using `/?`, like `--help` in Linux.

# Compare files
With `FC` command. As in 'File Compare'.

    fc file1.txt file2.txt

Or with `COMP` command which is a bit different from `FC`.

# Edit
Launch an editor.

    edit [file]

MS-DOS editor in XP.

MS-DOS editor not available in any 64-bit Windows.

# Managing directories
## Create directory

    mkdir [dirs]
    md [dirs]

## Delete directory
Remove an empty directory.

    rmdir [dirs]
    rd [dirs]

Or remove entire directory along with all its sub-directories and files with `DELTREE`:

`DELTREE` is considered a 'dangerous' command due to the possibility of accidental file deletion.

# Navigating directories
## Changing current directory
`CD` command.

### Go to the parent directory

    cd ..

## Print current directory
Run `cd` without any parameters.

    cd

# Help
## --help option for DOS commands
In DOS, `/?` fulfills the function of `--help` in Linux.

    cmd /?

## HELP

    HELP <command-name>

# Command options
In DOS, options are preceded by a '/' unlike Unix where hyphens are used instead.

# Change file permissions

Use `ATTRIB` command.

 - `+h`: hidden
 - `+r`: read-only
 - `+s`: system file
 - `+a`: archived file
 - `-h`: not hidden
 - `-r`: not read-only
 - `-s`: not system file
 - `-a`: not archived file

For example, the following command makes the file `file.txt` 'not hidden' and 'not read-only'.

    attrib -h -r file.txt

Without any switches, `ATTRIB` acts something like `ls -l` in Linux.

# Comments
Two ways:
 - `REM` command
 - `::`

These work only when at the beginning of a line.

Example:

    REM Hello script
    :: Another comment
    echo "Hello"
    
If we need comment after a command, we can use **command concatenation character** (&) like

    echo "hello" & REM A comment
    echo "world" & ::  Another comment

# Find memory usage
`MEM` command.

    mem

and get output like

    655360 bytes total conventional memory
    655360 bytes available to MS-DOS
    633456 largest executable program size

   1048576 bytes total contiguous extended memory
         0 bytes available contiguous extended memory
    941056 bytes available XMS memory
           MS-DOS resident in High Memory Area

# Pager
'MORE' command.

 - Next line: Return
 - Next page: Space
 - Exit     : q

# PATH command
Displays search path for executable files.

Like displaying or setting `$PATH` in Linux.

# PAUSE command
Suspends execution and by default, displays a "Press any key to continue . . ." message, till a key is pressed.

# Renaming files
Two ways:
 - move
 - ren

# Variables
Using `SET` command.

    set var=hello
    echo %var%

## Environment variables

%cd%     : $PWD
%date%   : 
%time%
   

# Wildcards
Unlike Unix, DOS considers file extension quite important.

## Asterisk

    REM Like `ls *` in Linux
    dir *.*
 
and

    REM Like `ls *.txt` in Linux
    dir *.txt

## Question mark

    *.sw?

would match ab.swp, 12a.swo, etc.

# Date and time

Display current date and prompt for new date value: `date`

Just display current date: `date /t`

Likewise with time: `time` and `time /t`.

# Shell
## Piping commands
Like in Unix.

For example, the following is like `cat file.txt | more` in Linux:

    type file.txt | more

## Input/output redirection
Todo: Todo

# Copy entire directory trees
Todo: `XCOPY` command.

# Less oftenly used commands
## Change title of DOS window
Change title of command prompt window with `TITLE` command.

## Get DOS version
`VER` command.

# Some 'equivalent' DOS commands
## `grep -r`

    dir *.txt /s /b

`/s` look in all sub-directories and `/b` keeps output concise.

# References
 - [https://en.wikipedia.org/wiki/List_of_DOS_commands](https://en.wikipedia.org/wiki/List_of_DOS_commands)
 - Help output of the commands
