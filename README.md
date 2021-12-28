# Software-Tools
A notebook about software tools

## Shell Commands
### Basic
- $ ls -al dir1: [command] [options/flags] [arguments]
- pwd: print working directory
- cd: change directory
- ls: list files in current directory
  - ls *.java: list/print all java files
- mkdir: make new directory
  - mkdir 'CSE 391'
  - mkdir NewDir
- rmdir: remove directory (directory must be empty)
- cp [src] [des]: copy something from src to des
- mv: move/rename file
  - mv [src] [newname]: mv old.txt new.txt
  - mv [src] [des]: mv readme.md .
- rm: remove file
- touch: make new file: touch file_name
- man: show manual
  - man cd
- exit: log out of the shell
- clear: clear console
- date: print current date
- uname: print info about current system
- Ctrl C: give up current command

### More
- echo "string": print "string" to standard out
- wget [https://]: download via http request
- unzip zip_file.zip
- cat [file]: print content of file to console
- head [file]: print the head lines of file
  - head -n 20: print the first 20 lines
- tail [file]: print the end lines of file
  - tail -n 20: print the last 20 lines
- wc [file]: count words: return [# of lines] [# of words] [# of char]
  - wc -l [file]: count and return [# of lines] only
- less [file]: make a view of the file
  - /[keyword]: search for keywords
  - hjkl: left down up right
- more [file]: same as less
- sort [file]: return a view of sorted file, but not change the actual file 
- uniq [file]: return/print lines with adjacent, duplicated lines filtered out
- grep: global regular expression print
  - grep [regex] [file]: print all LINES in file that match regex
  - grep TODO project/*: find all LINES matching to "TODO" in all files in project
  - grep TODO project/*.java: find all LINES matching to "TODO" in all java files in
    project
- find [dir]: print the tree structure of dir
  - find -name "*.java": find all files ending with .java 
    recursively in current directory
- cut -flag: select text
  - echo "abcd" | cut -c4 : select and print the 4th char, d
  - echo "a,b,c,d" | cut -d, -f1 
    - -d, : delimit by ,
    - -f1 : select the first field after delimit, which is a
- javac Main.java: compile Main.java to Main.class
- java Main: run Main.class
- java Main.java: compile and run Main.java

### Vim
- :w (write/save current file)
- :wq (write/save and exit current file)
- :q! (quit and don't save current file)
- i (insert mode: write text freely)
- Esc (exit to normal home mode)
- hjkl (left down up right)
- u (undo)
- x (delete)

## Unix Sample File System
- NOTE: use slash '/'
- /bin: binary executable programs
- /dev: hardware devices
- /etc: configuration files
- /home: user's home directory
- /proc: running processes
- /tmp: temporary files
- /usr: universal system resources

## Stream
- stdin: standard input (0)
- stdout: standard output (1)
- stderr: standard error (2)
- command \> stream
  - cat test.c \> test.txt: direct the output of the program 
    "cat test.c" to test.txt
- cat test.c \>\> test.txt: append (not overwrite) output of the 
  program "cat test.c" to test.txt
- command \< stream
  - java Evil.java \< pswd.txt: make pswd.txt as the input of the program
- java Bug.java 2\> log.txt: direct the standard error output to log.txt
- java Bug.java 2\>&1 mix.txt === java Bug.java \> mix.txt 2\>&1 : 
  direct the standard error and standard output to mix.txt
- java Bug.java > output.txt 2> err.txt: direct the standard output to 
  output.txt and standard error to err.txt
- Ctrl D: shut down current stream

## Pipe
- command1 | command2 (direct command1's output as command2's input)
- command1 ; command (execute command1 then command2)
- command1 && command2 (execute command1 first. If it succeeds, 
  then execute command2)
- command1 || command2 (execute command1 first. If it fails,
  then execute command2)
- grep "a" berries.txt | grep "e" | wc -l (count # of berries names containing 
  'a' and 'e') Note: no input stream arg for later commands since it automatically 
  receives previous commands' output as input
- sort berries.txt | uniq | wc -l (count # of unique berries names) Note: sort
is important since uniq only eliminate adjacent, duplicated lines
- xargs  
> ls *.java | javac
- We want to compile all java files, but this will FAIL since javac doesn't
accept stream. It accepts arg instead
> ls *.java | xargs javac
- xargs convert standard input/output to arg, so this will work
> find -name "*.java" | xargs javac
- tee [file]: print standard output to both [file] and console
  - usage: java Main.java | tee output.txt : Main.java's standard output
  will appear in both console and output.txt
  - How to include standard error?
  - java Main.java 2\>&1 | tee mix.txt
  
## Git
- git clone [git@...]: clone repo
- git status: examine current status (updated or not)
- git stage readme.md : prepare change?
- git commit -m "commit message"
- git push
- 