## Welcome to the Hacklab Unix Tools Introductory Workshop

#1. Getting Help (man pages)
`man` is your friend. If you're ever unsure the arguments to a command, the first place you should look is `man [command]`.

If you're unsure about how to use `man` then a quick `man man` in your terminal is your man.

Whenever you commit to this repository, GitHub Pages will run [Jekyll](https://jekyllrb.com/) to rebuild the pages in your site, from the content in your Markdown files.

#2 Moving Around With The Shell


The core of all shell mobility centers around a few simple commands. Once you familiarize yourself with these they will become the bread of butter of everything you do in the shell.

##2.1 `cd` - Change Directory
This command is used to navigate through the directories on your computer. Calling `cd` with no arguments will take you to your home directory which is denoted by `~` on most systems. `~` is equivalent to `/home/username`. So the command `cd/home/wolfe/Projects/BefungeVM` is the same as `cd ~/Projects/BefungeVM`.

##2.2 `ls` - List Files
This command is used to list the contents of a directory. If called with no arguments it lists the contents of your current folder. You can also call it with any number arguments and it will list the contends of those folders e.g.

```ls ~/Projects```

##2.3 `cp` & `mv` - Copy & Move
This is how you can manipulate file structure from the command line. The general syntax is for these two commands is

```cmd [source] [destination]```
So as an example you could run.

```cp test.txt /home/other_user/Documents/test.txt```
Note that the `/test.txt` isn't strictly needed if your destination is a folder than cp (and mv) will put the file into that folder with the same name.

```mv test.txt testing.txt```
**Note: There is no rename command in the shell you just move the file with a different name. As with the above command.**

##2.4 `pwd` - Print Working Directory
`pwd` stands for `print working directory` meaning that it prints the full path to your current location.

```pwd```
##2.5 Command Options

Commands can be called with addition options that augment their behavior. Take for example the `ls` command we just discussed. If you call `ls` with the flag `-l` it will provide you with more information about each file.

```ls -l```

##2.6 Tab Completion
While typing full file paths all the time may seem tedious this is mostly avoided by using what's called tab completion. For example say I wanted to type the path `/usr/lib/debug/usr/bin/terminology.debug` rather than typing the full thing I would type `/u` then hit tab and it would fill in the `sr` followed by `l` hit tab and so on. Usually you only need to type the first letter or two before tab will finish the work.

#3 Piping and Redirection
This is one of the things that makes the shell such a powerful tool it allows you to mix and match many small utilities, each of which does one thing very well.

##3.1 Standard File Descriptors
###3.1.1 `stdout`
This is the default output for a program or command i.e what's printed to your screen by default

###3.1.2 `stdin`
This is how programs and commands recieve data from the user. i.e. if a program prompts you for a username and password.

###3.1.3 `stderr`
This is used for errors and debug info. i.e. looks the same as `stdout` just kept in a seperate stream

##3.2 `|`- Piping
Piping is when you use the output from one command, as the input for another. The following command pipes the output from `cat` (which prints the contents of a file) into `sort` which sorts the lines of input alphanumerically. `cat file.txt | sort`

##3.3 `>` - Redirection
Redirection allows you to easily take input or give output from (or to) a file.

###3.3.1 Command to File
It is often done when you want to put the output of a command into a file. I.e. `ls -al > file_data.txt`

You can also redirect `stderr` with `2>` instead of `>`, or both with `&>`.

Additionally, you can use `>>` in place of `>` to append to the given file.

###3.3.2 File to Command
You can also direct from a file into a command using the syntax `CMD < File` I.e. `./my_program < input.txt`

This allows you to use a file as the input for a command, which can be very useful for automation.

#4 Globbing
Globbing is the lazy man's regex. It allows you to specify multiple files or folders without having all the additional syntax of a full regex.

##4.1 `*` matches zero or more characters
Say have a folder containing the files `foo.txt`, `bar.txt`, `bar/` and `bar.png` then running the command `ls *.txt` would list `foo.txt` and `bar.txt` or running `ls bar*` would list `bar.txt` and `bar/`.

##4.2 `?` matches exactly one character
So if you had `bar` and `baz` then `ba?` would match both but it wouldn't match `bar.txt`.

##4.3 Don't forget about `man`
For more complicated globbing check out `man 7 glob`

#5 Important Commands
Brief overview of some of the more used shell commands. I'd encourage you to skim the man pages for these commands.

##5.1 `cat`
Prints the contents of a file to `stdout`.

```cat ~/bin/anumgen```
##5.2 `less`
`Less` is what's referred to as a pager. Rather than having to scroll back through your terminal to read the output of a command. `Less` allows you to neatly scroll through the output page by page (hence the name).

This command is typically used by tacking it into the end of a command to neatly view the output e.g. `cat large_file | sort | uniq | less`.

##5.3 `touch`
Creates the file if it doesn't exist otherwise updates the timestamp.

```touch somefile.txt```
##5.4 `mkdir`
Creates a directory.

```mkdir somedir```
##5.5 `rm`
Removes a file or directory (`-r` flag is required to recursively remove a dir).

```rm somefile```
##5.6 `grep`
Search a file for a given string or regex. With options this can recursively search directories which is very handy.

```grep 'food' somefile```
##5.7 `find`
Find a file with a given name or matches a regex.

```find . -name *.txt```
##5.8 `sed`
Find a replace text from `stdin` or file. You can also match a regex.

```sed 's/old/new/'```
##5.9 `curl`
Makes web requests and downloads files.

```curl http://google.com```

