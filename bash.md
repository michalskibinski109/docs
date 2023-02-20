# usefull bash commands
- [usefull bash commands](#usefull-bash-commands)
  - [advenced examples 🤯](#advenced-examples-)
  - [navigation 🗺](#navigation-)
    - [`history` - show history of commands](#history---show-history-of-commands)
    - [`pwd` print working directory](#pwd-print-working-directory)
    - [`pushd` and `popd` 📌](#pushd-and-popd-)
    - [`find` find file by name 👁](#find-find-file-by-name-)
  - [manipulate output 📄](#manipulate-output-)
    - [`sort` - sort lines of text files](#sort---sort-lines-of-text-files)
    - [`colordiff` - color diff <old> <new>](#colordiff---color-diff-old-new)
    - [`uniq` - remove duplicate lines (looks only one line ahead) 🎅](#uniq---remove-duplicate-lines-looks-only-one-line-ahead-)
  - [get help ❓](#get-help-)
  - [file permissions 🔏](#file-permissions-)
    - [summary](#summary)
    - [`chmod` - change mode (permissions) of file](#chmod---change-mode-permissions-of-file)
  - [Working with files 📄](#working-with-files-)
    - [`wc` 🚻 🧮](#wc--)
    - [`file`](#file)
    - [`head`/`tail` (print first/last 10 lines of file) 📄](#headtail-print-firstlast-10-lines-of-file-)
    - [`cat` (concatenate) 🐈](#cat-concatenate-)
    - [`more` (page through a file) 🖨](#more-page-through-a-file-)
    - [`less` (page through a file more advanced) 🖨🖨](#less-page-through-a-file-more-advanced-)
    - [`nano` (text editor) 📝](#nano-text-editor-)
    - [`grep` (global regular expression print) 🔎](#grep-global-regular-expression-print-)
  - [Sudo 🤴](#sudo-)
  - [users 🧑‍🤝‍🧑](#users-)
  - [manipulating processes 🔄](#manipulating-processes-)
    - [`ps` - list processes](#ps---list-processes)
    - [`watch` - run command periodically ⏱](#watch---run-command-periodically-)
    - [`kill` - kill process](#kill---kill-process)
  - [expansions 📈](#expansions-)
  - [time](#time)
  - [other](#other)
    - [`du` - disk usage 💽](#du---disk-usage-)
    - [`df` - disk free 📉](#df---disk-free-)
    - [`>` (redirect) 🧭](#-redirect-)
    - [`|` (pipe) 🚰](#-pipe-)



## advenced examples 🤯
- `ls -al / > lsout.txt`  - redirect list of all files in folder to file
- `sort file.txt -u | wc -l` - sort file and count unique lines
- `touch {main,test}.py` - create two files `main.py` and `test.py` DO NOT USE SPACES
## navigation 🗺
### `history` - show history of commands
- `history | grep <command>` - show history of commands with `command` in it
- `!<num>` - runs command with number `num` from history
### `pwd` print working directory
### `pushd` and `popd` 📌
- `pushd <directory2>` - save current directory to stack
- `popd` - go to last directory from stack (saved by `pushd`)

### `find` find file by name 👁
- `find -name "file.txt"` - find file in current folder
- `~` - home directory of current user
- `find . -f -name *.py -exec rm {} \;` - find all python files.and delete them
- `find . -name '*7*'` - find all files with 7 in name USE BRACKETS
- `find. -size -100k -exec cat {} \;` - find all files smaller than 100k and print them
args:
- `-iname` - case insensitive search (no matter if file is `file.txt` or `FILE.txt`
- `-f`/`-d` - find files / directories 
- `-exec` - execute command on found files
- `-size <min> <max>` - find files with size eg. `find . -size +100k` - find files bigger than 100kb
- `-mtime <min> <max>` - find files modified in last `min` days
## manipulate output 📄
### `sort` - sort lines of text files 
- `sort -nr <file>`  - sort lines numerically in reverse
- `sort -k 2 -u <file>` - sort by second column and remove duplicates 
### `colordiff` - color diff <old> <new> 
- `y` - to see side by side
- `u` - to see context
### `uniq` - remove duplicate lines (looks only one line ahead) 🎅
- `sort <file> uniq -c ` - count duplicates
- `-d` - only print duplicated values
## get help ❓
- `whatis <command>` - get a one-line description of a command
- `man <command>` - get extended help for a command
- `which <command>` - get path to given command
- `apropos <keyword>` - search for commands with given keyword

## file permissions 🔏
### summary 
permissions are represented by 3 sets of 3 bits (rwx) for user, group and other
- `r` (4) - read 📖
- `w` (2) - write 🖊
- `x` (1) - execute 🏃‍♂️
- `-` (0) - no permission 🚫
- `-rwxr-xr-x` = `755` 

- `-d` -  directory 📁
### `chmod` - change mode (permissions) of file
- `chmod 777 <file>` - give all permissions to all users
- `chmod 755 <file>` - give all permissions to owner, read and execute to group and other
- for directories `x` means that you can enter the directory

## Working with files 📄

### `wc` 🚻 🧮
- `wc <file>` - prints `<words number> <lines number> <bytes number> <file name>` 
### `file`  
- `file file.txt` - get file type 
- `file -i file.txt` - get file type and encoding
### `head`/`tail` (print first/last 10 lines of file) 📄
- `head -n 5 file.txt` - print first 5 lines of file.txt
- `tail -f logs.log` - print last lines of file and follow (print new lines as they appear)



### `cat` (concatenate) 🐈
- `cat <file>` - print file contents
- `cat <file1> <file2>` - print file1 and file2 contents
- `cat > <file>` - **create** file and write to it
- `cat >> <file>` - **append content** of file (create file if not exists). Press `Ctrl+D` to save and exit
- 
### `more` (page through a file) 🖨
- `more <file>` - print file contents 
  - `space` to scroll down
  -  `b` to scroll up
  -   `q` to exit
  -   
### `less` (page through a file more advanced) 🖨🖨
- `less <file>` - print file contents
  - `arrow down`/`arrow up` to scroll 
  - find text with `/<text to find>` and `n` to go to next match
  - `G` to go to end of file
  - `g` to go to start of file
  - `q` to exit
  - `Ctrl+F` to scroll down
  - `Ctrl+B` to scroll up 
  
### `nano` (text editor) 📝
- `nano <file>` - edit file
  - `Ctrl+O` to save
  - `Ctrl+X` to exit
  - `Ctrl+G` to get help
  
### `grep` (global regular expression print) 🔎
- `grep <text to find> <file>` - find text in file
- `grep  -rE  "\b[A-Za-z0-9._%+-]+@[A-Za-z0-9.-]+\.\b" ~ ` - find all emails in every file in home directory

## Sudo 🤴
- `sudo !!` - repeat last command as sudo
- `sudo -s` - get root shell (exit with `exit`)
- `su - <user>` - get shell of another user (exit with `exit`)
- `su -` - get shell of root user IT IS NOT RECOMMENDED 💀
  
## users 🧑‍🤝‍🧑
- `whoami` - get current user
- `users` - get list of users
- `id` - get user id


## manipulating processes 🔄
- `shutdown -h now` - shutdown computer 
### `ps` - list processes 
- `ps axww | grep "Visual Studio Code"` - find vscode process
### `watch` - run command periodically ⏱
- `watch free -h` - check memory usage every 2 seconds (`Ctrl+C` to exit)
### `kill` - kill process
- `kill -9 <pid>` - `-9` stands for brutal way. kill process with given pid
- `killall <process name>` - kill all processes with given name (you have to own this process)
- u can check if program existis with `which <program name>`

## expansions 📈
| expansion     | description                           |
| ------------- | ------------------------------------- |
| `~`           | matches home dir of user              |
| `*`           | matches all files in folder           |
| `*.txt`       | matches all txt files                 |
| `*.??`        | matches all  files with `<name>.<xx>` |
| `{a,b,c}`     | matches a, b and c DON'T USE SPACES   |
| `{1..5}`      | matches 1,2,3,4,5                     |
| `{a,b,c}.txt` | matches a.txt, b.txt, c.txt           |
| `$PATH`       | contains all dirs in PATH             |
| `$USER`       | contains current user                 |
| `$SHELL`      | contains current shell                |
| `$RANDOM`     | contains random number                |
| `$HOSTNAME`   | contains hostname                     |
| `$PWD`        | contains current directory            |
| `$HOME`       | contains home directory               |
| `$OLDPWD`     | contains previous directory           |

## time
- `date` - get current date and time

## other

- `ctrl+l` - clear terminal
- `ctrl+shift + +` - incrase font size  
- `ctrl + -` - decrease font size
- `ctrl + -` - recursive search (USEFULL)
  
### `du` - disk usage 💽
- `du -h | sort -h` - print human readable sizes from smallest to biggest
- `du -sh` - print size of current directory

### `df` - disk free 📉
- `df -h` - print human readable sizes of all mounted partitions
### `>` (redirect) 🧭
- `echo "hello" > file.txt` - write "hello" to file.txt
- `>>` - append to file 
### `|` (pipe) 🚰
- `<command1> | <command2>` - pass output of command1 to command2
- e.g. `cat <file> | grep <text>` - print lines from file that contain text
- E.G. `history | less` - print file contents with less
### `tmux`
- `tmux new` to start new session . Also starts server if it is first session.
  - default session name: `0` to change it use `tmux new -syour_name`
- `ctrl + b`(`C-b`) - default tmux prefix. Must be run before any command.
- `C-b ?` - show all shortcouts.
- `C-b c` - create new window (`tmux new-window -n<name>`)
- `C-b d` - detaches session
- `tmux attach -t<session_name>` - attach session to given tmux session.
  - `C-b down/up/left/right` to change focussed window.
- `tmux ls` - lists sessions
- `tmux kill-server` - kills tmux server
- `tmux split-window` - `C-b %` (horizontally) `C-b "` (vertically)
- `select-window` - `C-b <number of window>`
- `tmux choose-tree` - `C-b s` shows attached sessions.
  
  
