# Lab Report 3: Researching Commands
## More on Find Commands (Source: ChatGPT for all commands)

**Command -size:** The "-size" option allows you to search for files based on their size 

**Example 1**

```
  $ find ./technical -type f -size +10k
  ./technical/biomed/1471-2334-2-27.txt
  ./technical/biomed/1471-2334-2-29.txt
  ./technical/biomed/1471-2334-2-5.txt
  ...
```
This command searches for files larger than 10 kilobytes inside the './technical' directory.

**Example 2**
```
   find ./technical -type f -size -100000G
   ./technical/biomed/1471-2350-3-1.txt
   ./technical/biomed/1471-2350-3-12.txt
   ./technical/biomed/1471-2350-3-7.txt
   ...
```

This command searches for files smaller than 100000 kilobytes inside the './technical' directory.

**Command -mtime:** The '-mtime' option allows you to search for files based on their modification time. 

**Example 1**

```
  $ find ./technical -type f -mtime -13
  ./technical/biomed/1471-2350-3-1.txt
  ./technical/biomed/1471-2350-3-12.txt
  ./technical/biomed/1471-2350-3-7.txt
  ...
```
 This command searches for files modified within the last 13 days inside the './technical' directory.
 
**Example 2**
```
  $ find ./technical -type f -mtime +10
  ./technical/plos/pmed.0020275.txt
  ./technical/plos/pmed.0020278.txt
  ./technical/plos/pmed.0020281.txt
  ...
```
This command searches for files modified more than 10 days ago inside the './technical' directory.

**Command -exec:** The "-exec" option allows you to execute a command on the files or directories found by 'find'.

**Example 1**
```
  $ find ./technical -type f -name "*.txt" -exec cp {} ./backup \;
```
![Image](backup.png)

This command finds all files with the extension '.txt' inside the './technical' directory and copies them to the './backup' directory. There is no output displayed (files are copied to './backup' directory).

**Example 2**
```
  $ find ./technical -type f -name "*.log" -exec rm {} \;
```
This command finds all files with the extension '.log' inside the './technical' directory and deletes them. Since there are no .log files in "/technical" this command doesn't do anything, however, if I were to use the ".txt" extension every file would be deleated. 

**Command -empty with -deleat:** The "-empty" option allows you to search for empty files or directories. The "-deleat" option allows you to deleat any file you search for

**Example 1**
```
  $ find ./technical -type d -empty
```
This command searches for empty directories inside the './technical' directory. The "-type d" command ensures that only directories are considered. The '-empty' option filters out directories that have no files or subdirectories within them. Because there are no empty directories nothing is prinited into the command line.  

**Example 2**
```
  find ./technical -type d -empty -delete
```
This command will search for empty directories inside the ./technical directory and delete them.





  
