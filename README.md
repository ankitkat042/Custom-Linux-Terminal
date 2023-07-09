# Custom Unix Terminal
1. Run `make` in terminal where project's MakeFile is located.
![image](https://github.com/ankitkat042/DES102-Assignments/assets/79627254/675c327a-0b8f-4e10-bd5f-8dd2770c03f3)

2. Run the custom terminal using `./Main` and explore all the custom commands I've programmed in it. Scroll down to know about those commands
![image](https://github.com/ankitkat042/DES102-Assignments/assets/79627254/dc7c27ca-5b72-42e4-9d42-2c08a5063f2a)

A simple shell that can handle three, internal commands – `cd`, `echo` and `pwd`. These commands would be handled directly by the shell. 

The shell also contains five external commands – `ls`, `cat`, `date`, `rm` and `mkdir`. For these external commands I wrote individual programs to  handle these commands. To handle these external commands, the shell create a new process, using the ```fork()``` system call and within each process you need to use the ```execl()``` family system call to run the individual program. The parent program must also wait for the child program to terminate using the ```wait()``` family of system calls.

# Command explanation

## Internal Commands

### cd
#### Options
- `-L` : force symbolic links to be followed: resolve symbolic links in DIR after processing instances of `..`
- `–help`: display the help manual and exits

#### Error handled
- If the directory is not present, it shows "No such file/directory"
- If the flag is absent or wrong, it shows no such option or file is present

#### Assumption
Home directory is the directory in which `./main` is present.

### echo 
#### Options
- `-n` : omit the trailing newline character
- `-E` : disable the interpretation of backslash escapes (default)

#### Error handled
- If no argument is passed then it shows an error that an argument is required

#### Assumption
Double quotes of the string are directly handled.

### pwd
#### Options
- `-L` : print the value of `$PWD` if it names the current working directory
- `-P` : print the physical directory, without any symbolic links
- `–help`: displays help and exit (implemented before professor's email)

#### Error handled
- If option is not present then outputs option not found

## External Commands

### ls
#### Options
- `-a` : show hidden files, which means it shows filenames starting with '.'
- `-m` : comma-separated names of files and folders
- `-1` : shows the names of folders and files as a vertical list

#### Error handled
- Arguments are not enough or wrong arguments

### cat
#### Options
- `-n` : number all output lines
- `-E` : display `$` at the end of each line

#### Error handled
Using fopen error library and errno.h header file:
- The file does not exist
- The user doesn't have access to the file

### date 
#### Options
- `-u` : print the UTC time
- `–help`: display help manual and exit(also implemented before sir's mail)

### rm
#### Options
- `-i` : output prompt as a warning before removing a file
- `–help`: display the help and exits

#### Errors
- The file does not exist
- The given path is a directory
- The user doesn't have access to files

### mkdir 
#### Options
- `-v` : print a message for each created directory
- `–help`: display help and exits :(

#### Errors
- The named directory already exists
- Readonly folder cannot have subfolders
- A component of the path prefix cannot be a directory


Ubuntu is my favourite Debian-based distro ❤