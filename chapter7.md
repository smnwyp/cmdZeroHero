# chapter 7. seeing the world as the shell sees it

## expansion
the process of `expansion` is the process where the shell figures out
what the command really means in what context and `expands` it into sth else 
before the shell could act upon it.

### path expansion
```commandline
> echo .[!.]*
```
this pattern would expands into every filename beginning with `.`, but 
does **NOT** include a second `.`. will work with most hidden files.

### tilde `~` expansion
when used in the beginning of a word, it expands into the name of home
directory of the named user
```commandline
> echo ~
/home/me
> echo ~<username>
/home/<username>
```

### arithmetic expansion
```commandline
> # ((<expression>))
> echo $((2+2))
4
> echo $((2**3))
8
> echo $(( $((1+2)) * 3 ))
9
> echo hello there world $(( 2 * 3))
hello there world 6
```

### brace expansion
used to create text string from patterns.

Best use-case: make lists of files or dirs 

```commandline
> #{<preamble><common-sep list of str><postscript>}
> #{<preamble><range of int><postscript>}
> #{<preamble><range of single char><postscript>}

> echo Front~{A,B,C}~Back
Front~A~Back Front~D~Back Front~C~Back
> echo fasdf_{1..5}
fasdf_1 fasdf_2 fasdf_3 fasdf_4 fasdf_5
> echo {001..3}
001 002 003
> echo a{A{1,2},B{3,4}}b
aA1b aA2b aB3b aB4b
> mkdir {2007..2000}-{01..12}
```

## Quoting
a way to selectively suppress unwanted `expansions`

#### double quotes `"`
all special characters used by the shell would lose their meaning.
- word-splitting, pathname expansion, tilde `~` expansion, `{}` expansion 
would be suppressed
- but parameter expansion `*`, arithmetic `$((<exp>))` expansion and command substition
can still be carried out.
```commandline
$ echo "$USER $((1+3)) $(cal)"
chloe 4    November 2022      
Su Mo Tu We Th Fr Sa  
       1  2  3  4  5  
 6  7  8  9 10 11 12  
13 14 15 16 17 18 19  
20 21 22 23 24 25 26  
27 28 29 30 
```

`newline` is considered as delimiters

#### single quote `'`
to suppress **ALL** expansions!

#### escaping characters `\`
used to quote a single character
```commandline
$ echo "hello $USER is : \$5.00"
hello chloe is : $5.00
$ sleep 5; echo -e "\a" # will beep
$ echo ""
```











