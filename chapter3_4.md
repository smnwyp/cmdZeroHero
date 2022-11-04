# chapter 3&4

## key concepts

### Symbolic Links
In Unix-like systems, it's likely to have a file referenced by multiple names.
**BUT**, if one deletes a symbolic link, only the link is deleted.
If file is deleted prior to the symbolic link, then the link would point to null.

**DOUBLE BUT** if you then recreate a file under the same name, it would all work again. 
think it's reference by value lol, bery dynamic.

### Hard links
it's different from `symbolic links`, a hardlink is exactly the same as the file it links to.

every file by default has a hard link that gives the file its name, the file gets an additional directory 
entry for the file when a hard link is created.

1. a hard link may not reference a directory
2. a hard link shall not referene a file outside its own file system

**BUT** if one deletes the file the hard link links to, the hardlink can still function meaning the 
value is not lost. hardlink is just the same as the file it links to.

### **try it out**
create a hardlink and a softlink on the same file F1, and then delete F1.
check which link still works and why.
