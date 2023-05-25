# Lab Report 3: Researching Commands
## More on Find Command (Source: ChatGPT for all commands)
Prompt given to ChatGPT: Show me six interesting command-line options in bash with explinations for what they do
Response: Certainly! 
- Option 1: -type - Searches for files or directories based on their type.
- Option 2: -size - Searches for files based on their size.
- Option 3: -mtime - Searches for files based on their modification time.
- Option 4: -exec - Executes a command on the files or directories found.
- Option 5: -name - Searches for files or directories based on their name patterns
- Option 6: -empty - Searches for empty files or directories.

Prompt: Give 1 example for each
Response: 
- find . -type d
- find . -type f -size +10M
- find . -type f -mtime -7
- find . - find ./technical -type f -name "*.log" -exec rm {} \;
- find . -name "example"
- find . -type f -empty

I then picked 4 of these commands, made one expample of my own, and wrote down what I understood from my testing

**Command -size:** The "-size" option allows you to search for files based on their size and it also allows for specifing a size threshold.

**Example 1**

```
  $ find ./technical -type f -size +10k
  ./technical/biomed/1471-2334-2-27.txt
  ./technical/biomed/1471-2334-2-29.txt
  ./technical/biomed/1471-2334-2-5.txt
  ...
```
This command searches for files larger than 10 kilobytes inside the './technical' directory. This can be useful when a user knows that the file he is searching for is definitely bigger than some certain limit.

**Example 2**
```
   find ./technical -type f -size -100000G
   ./technical/biomed/1471-2350-3-1.txt
   ./technical/biomed/1471-2350-3-12.txt
   ./technical/biomed/1471-2350-3-7.txt
   ...
```

This command searches for files smaller than 100000 kilobytes inside the './technical' directory. Conversly this command allows a user to search for a file whne he knows that it is smaller than a certain size.  So if somone is looking for a .txt file he probably knows it won't be very large and can therefore use -10M to search through all the text files.

**Command -mtime:** The '-mtime' option allows you to search for files based on their modification time. 

**Example 1**

```
  $ find ./technical -type f -mtime -13
  ./technical/biomed/1471-2350-3-1.txt
  ./technical/biomed/1471-2350-3-12.txt
  ./technical/biomed/1471-2350-3-7.txt
  ...
```
 This command searches for files modified within the last 13 days inside the './technical' directory. This can be useful if you recently edited a file but forgot which one you edited. 
 
**Example 2**
```
  $ find ./technical -type f -mtime +10
  ./technical/plos/pmed.0020275.txt
  ./technical/plos/pmed.0020278.txt
  ./technical/plos/pmed.0020281.txt
  ...
```
This command searches for files modified more than 10 days ago inside the './technical' directory. This command, while less usefull than - can be usefull if you know that you edited a file roughly 2 weeks ago for example. This will narrow your search and let you find the file quicker.

**Command -exec:** The "-exec" option allows you to execute a command on the files or directories found by 'find'.

**Example 1**
```
  $ find ./technical -type f -name "*.txt" -exec cp {} ./backup \;
```
![Image](backup.png)

This command finds all files with the extension '.txt' inside the './technical' directory and copies them to the './backup' directory. There is no output displayed (files are copied to './backup' directory). This is a fast an efficient way to store all the files of a certain type in different directories and is overall very usefull for file managment.

**Example 2**
```
  $ find ./technical -type f -name "*.log" -exec rm {} \;
```
This command finds all files with the extension '.log' inside the './technical' directory and deletes them. Since there are no .log files in "/technical" this command doesn't do anything, however, if I were to use the ".txt" extension every file would be deleated. This is usefull again for file management and system organization. 

**Command -empty with -deleat:** The "-empty" option allows you to search for empty files or directories. The "-deleat" option allows you to deleat any file you search for

**Example 1**
```
  $ find ./technical -type d -empty
```
This command searches for empty directories inside the './technical' directory. The "-type d" command ensures that only directories are considered. The '-empty' option filters out directories that have no files or subdirectories within them. Because there are no empty directories nothing is prinited into the command line. This command can help a user find out what files he still has to work on or what files he has created unnessarily.


**Example 2**
```
  find ./technical -type d -empty -delete
```
This command will search for empty directories inside the ./technical directory and delete them. This is once again useful for memory and file managment because it is not useful to have files that have nothing in them.






  
