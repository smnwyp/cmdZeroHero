# chapter 6. I/O redirection

## standard input, output and error
**everything is a file**, output of a command will be sent to 2 different files, 
`standard output - stdout` and `standard error -- sterr`, and **by default** both files are
linked to the screen and not saved into a disk file.

for many programs, there's also sth called `standard input -- stdin` which is, **by default**, 
attached to the keyboard.

I/O redirection allows us to manipulate where `stdout`, `stderr` and `stdin` goes.

internally, a program can produce output on any number of file streams, we reference the 
first 3 as `stdin`, `stdout` and `stderr`, the shell itself references them as `0`, `1` and 
`2` respectively.

### redirecting `stdout`
`>` is used to redirect! and **writes from the top everytime**!

`>>` is also used to redirect, but only **appends**

### redirecting `stderr`
not quite as easy as redirecting `stdout`, one must refer to its `file descriptor`
(as described above).

`ls -l 2> ls-error.txt`

#### how to redirect `stdout` and `stderr` to one file?
old versions of shell:
```commandline
> ls > ls.txt 2>&1
```
in essense, 2 redirections are performed:
1. `stdout` is redirected to `ls.txt`
2. `stderr` is redirected to `stdout` via the notation `2>&1`

new version of shell:
```commandline
> ls &> ls.txt
> ls &>> ls.txt
```
the notatioin `&>` reidrects both `stdout` and `stderr` to the file.


#### how to throw away unwanted output
the system does it by redirecting it to a special file called `/dev/null` which is a system 
device called `bit bucket` which accepts input and does nothing with it lol!!!
```commandline
> ls 2> /dev/null
```
suppresses error msgs.

### redirecting `stdin`
1. `cat` command redirects `stdin`, eg.one or more files, and copies them to `stdout`.
can also be used to join files together!
```commandline
> cat < source_of_file.txt
```
in which, `<` is a redirection operator.


### Pipelines
`pipelines` is a shell feature that reads data from `stdin` and sends to `stdout`.
`|` is a pipe operator to relay the `stdout` of one command to be the `stdin` of the next command. 
```commandline
> ls | less
```

```commandline
> <command1> > <file1>
> <command2> | <command2>
```

#### filters
every transformation in the pipelines is called `filter`

#### `wc` -- print line, word, and byte counts
```
> wc asdfas.txt
> ll | sort | wc -l
> ll | sort | wc
```

#### `tail` how to view in real time
```commandline
> tail -f <file>
```

#### `tee` -- read from `stdin` and output to `stdout` and files
good for capturing intermediate status in a pipelines stages, debug companion.

```commandline
> ll | sort | tee <filename> | grep <keyword>
```
