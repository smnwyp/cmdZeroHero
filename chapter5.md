# chapter 5 all about commands

## 4 types of commands
1. executable, like a script or compiled binaries
2. a shell builtin command, eg. `cd`
3. a shell function, eg. shell scripts in `environment`
4. an alias...

## third-degree with command
1. `type <command>` -- displays the type (one of the 4 above) of the command 
2. `which <command>`-- displays the location of the executables, for all other types, behaviour
falls back to `type <command>`

## how to get documentations
1. `man <command>` -- here, `man` is actually just a paging program used to read the documentations
provided by most executable programs.
2. `apropos <serach_term>` -- display appropriate commands.
3. `whatis <command>` -- displays a very brief description of a command
4. `info <command>` -- displays entry info