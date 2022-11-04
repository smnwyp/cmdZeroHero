# Chapter 2. Navigation

## File System Tree
Linux (like Windows) organizes its files in a `hierachical directory structure`, which is a tree-like pattern
of directories (AKA folders).

### root directory
is the **first** directory in the file system.

For Linux systems, there is always a single file system tree, regardless of how many drives or storage devices 
that are attached to the computer, which are simply just **mounted** on the tree.

## Directory Path
### absolute pathnames
it begins with the root directory and follows the tree branch by branch
### relative pathnames
it starts from the working directory, the relative position in the file system tree is represented by :
1. `.` -- current working directory
2. `..` -- parent directory of current working directory

## text
one of the earliest and simpleest representation system between information and some numbers is `ASCII text`.

`ASCII text` is very simple, which only contains a simple mapping of characters to numbers, 
and a few rudimentary controls like tab, carriage returns `\r` and line feeds `\n`.
In contrast, a word document by Microsoft is super different, 
it includes other stuff like non-text elements used to describe structure and formatting.

## Links
the file pointed to by a symbolic link, and the symbolic link itself are largely indistinguishable. 
edit the link, edit the file











