# *nix Scavenger Hunt

Complete the following challenges using the command-line interface on your favorite
Unix or Linux operating system. You are welcome and encouraged to consult any
additional documentation online or in books.

Please add your answers/responses/text pastes to the document after each prompt.

Note: For some of the challenges you will need to reference files included with
this repository, so you will need to fork the repo into your own Github account
and then clone it to your development environment.

## The Challenges

### Navigating the Filesystem

* Get an idea of where you are in the operating system. Use the `pwd` command to find your "path to working directory"--your current location in the filesystem of your devbox. *Paste the output of the `pwd` command here:
- /c/Users/browsy/Documents/Web Development/wats1030-intro-to-unix

* Discover more about this filesystem. Use `ls` (the "list" command)to see what is in this directory. *What directories and files do you see when you run `ls`?*
-Im am given all the files found within the current folder

* You can use *options* to modify how a command runs. Try using `ls -alh` to see the contents of your current directory. *How are the results different when you use the `-alh` options?*
-the main difference is that all the files found are now in detail in terms of view, showing their type via readable and directory, size, and date created.

* The `man` ("manual") command tells you more about how any given command works. (*WARNING:* CodeAnywhere does not support the man command. You can click the following link to complete this task: http://man.he.net/). Run `man` to see instructions about how to use `man`. Then use `man` to learn what the `a`, `l`, and `h` options mean when used with the `ls` command. *Write down what those options do?*
-a, --all
    do not ignore entries starting with . 

-l
    use a long listing format 

-h, --human-readable
    with -l, print sizes in human readable format (e.g., 1K 234M 2G) 

* Commands can also take *arguments*, which are usually the names of files or locations that you want the command to work with. Try running `ls /` to see what files are in the *root* directory of the filesystem. *What files and directories do you see listed?*
- in my root: bin  cmd  dev  etc  git-bash.exe  git-cmd.exe  LICENSE.txt  mingw64  proc  ReleaseNotes.html  tmp  unins000.dat  unins000.exe  unins000.msg  usr

* A Unix filesystem has a few special shortcuts to refer to specific locations. `/` indicates the *root* of the filesystem, meaning the top-most directory in the filesystem hierarchy. Use the `cd` ("change directory") command to move to the root directory. (Hint: Use `man` to look up the `cd` command if you have any issues) *Then run `pwd` and paste the output here:*
when chaning to the root / all i get with pwd is "/"

* Another special shortcut in Unix is the `~` location. This indicates the *user root* directory, meaning the top-most directory in the hierarchy that comes below your user account. Use `cd` to move to `~`. *Run `pwd` and paste the response here:*
/c/Users/browsy


* Change directory into the `challenge_files` directory. Use `ls` to find only the files with a `.demo` pattern. *How many files do you find?*
(ls *demo )
- 3

* Use the `cd` command to move "up" one directory. *Where are you in the filesystem now?*
 ~/Documents/Web Development/wats1030-intro-to-unix

* Press the up arrow on your keyboard. *What just happened?*
i got .. 

* Press the up arrow a few more times. *What do you see?*
i see my prevous entered commands 

* Run the `history` command. *What do you see?*
all my prevous entered commands 

### Observing the System

* Discover what account you are logged into using the `whoami` command. *What username are you currently using?*
browsy
* Discover who else is on your system with the `who` command. *Are any other users using your system? If so, list them here:* 
i dont get a response, so its just me as the user
* How long has your system been running? Use `uptime` to see, and *paste the result here:* bash: uptime: command not found
* Run `ps aux` and review the results. (Hint: Use `man` to learn more about the `ps` command and options.) *How do you interpret what you see here?*
ps:first process shows the process under which this terminal is opened
a:- This option prints the running processes from all users.

u:- This option shows user or owner column in output.

x:- This option prints the processes those have not been executed from the terminal.

Collectively the options "aux" print all the running process in system regardless from where they have been executed.

basically it seems like a set of main commands and where they are stashed.

<!-- http://www.linfo.org/ps.html -->

* Run `top` and review the results. (Hint: You may need to use `ctrl-c` to get out of this app.) *How do you interpret what you see here?*
 displays processor activity of your Linux box and also displays tasks managed by kernel in real-time. It'll show processor and memory are being used

### Finding and Viewing Files

* Make sure you are in the `challenge_files` directory. Use the `*` wildcard to find all the files that have the word "credit" in the filename. *How many files did you find?*
-2
$ find . -name "credit*"
./credit_cards.txt
./credit_cards2.txt

<!-- alternative 
find * | grep credit
credit_cards.txt
credit_cards2.txt
 -->

 <!-- https://www.youtube.com/watch?v=KCVaNb_zOuw -->

* Use the `more` command to view one of the `credit_cards` files you just discovered. (Hint: Type `q` to quit viewing the file. Press the `spacebar` to page down. Use your keyboard arrows to move up/down.) *What is the date in the file you have viewed?*
$ less "credit_cards.txt"
Last updated: 01-15-2015


* Use the `find` command to search for files more effectively. Search the sub-directories under `challenge_files` to find the location of the file named `modi_laboriosam.txt`. *Where is that file located?*
find . -name "modi_laboriosam.txt"
-./tmp/modi_laboriosam.txt

* Use the `grep` command to search for text within a file. Use `grep` on all the `.user` files in `challenge_files` to find which files contain "WA" (the abbreviation for Washington state). *How many files did you find?*
$ grep WA *
grep: 01: Is a directory
Britt-Erdman.user:O'Harachester, WA 37261
Lissie-Strosin.user:Jewessfurt, WA 00816-7241

<!-- https://www.youtube.com/watch?v=2-3i42XXzek
grep -c WA * would have worked too -->

* Use the `-r` option of `grep` to *recursively* find the text "Waldo" hidden in a file somewhere under the `challenge_files` directory. *Paste the result showing the file and line where the word "Waldo" shows up.*

$ grep -r "Waldo" 
 <!-- case sensitive Waldo -->
serial-numbers/eaque_molestiae.txt

### Pipes and Connecting Commands

* Sometimes it's useful to output the results of a command to a text file for further analysis, reference, or processing. Try running `ls > files.txt`. Notice that the file `files.txt` was created. View that file using `more`. *What do you see in the `files.txt` file?*
I found all the users, it was sort of like a copy and paste.

* Notice that if you run `ls -alh` in the `challenge_files` directory, the files scroll by very quickly. Sometimes it would be better to get the results in a paginated format. Try running `ls -alh | more`. *Describe what you see when you run `ls -alh | more`.*
it stopped midway when listing all the names


* Earlier, when you viewed the list of active processes on your devbox using `ps aux`, the list was probably really long. You can make this list more manageable by using the pipe (`|`) to filter the results of `ps` using `grep`. Run `ps aux | grep <your_username>` to see what processes are running for your specific user. *Paste the list of processes that reference your username here:*

$ ps -ef | grep browsy
  browsy    2031       1 cons0    11:03:54 /usr/bin/bash
  browsy    2108    2031 cons0    11:24:41 /usr/bin/ps


<!-- http://www.linfo.org/ps.html -->