# WalkThrough - Bandit Game
Bandit is wargame hosted by the OverTheWire organisation. It has 34 levels. You can access the game [here](https://overthewire.org/wargames/bandit/). This game is meant for complete beginners and teaches basics of most linux commands.

## To go to a particular level
- [Level 0](https://overthewire.org/wargames/bandit/bandit0.html)
- [Level 0-1](https://overthewire.org/wargames/bandit/bandit1.html)
- [Level 1-2](https://overthewire.org/wargames/bandit/bandit2.html)
- [Level 2-3](https://overthewire.org/wargames/bandit/bandit3.html)
- [Level 3-4](https://overthewire.org/wargames/bandit/bandit4.html)
- [Level 4-5](https://overthewire.org/wargames/bandit/bandit5.html)
- [Level 5-6](https://overthewire.org/wargames/bandit/bandit6.html)
- [Level 6-7](https://overthewire.org/wargames/bandit/bandit7.html)
- [Level 7-8](https://overthewire.org/wargames/bandit/bandit8.html)
- [Level 8-9](https://overthewire.org/wargames/bandit/bandit9.html)
- [Level 9-10](https://overthewire.org/wargames/bandit/bandit10.html)
- [Level 10-11](https://overthewire.org/wargames/bandit/bandit11.html)
- [Level 11-12](https://overthewire.org/wargames/bandit/bandit12.html)
- [Level 12-13](https://overthewire.org/wargames/bandit/bandit13.html)
- [Level 13-14](https://overthewire.org/wargames/bandit/bandit14.html)
- [Level 14-15](https://overthewire.org/wargames/bandit/bandit15.html)
- [level 15-16](https://overthewire.org/wargames/bandit/bandit16.html)
- [level 16-17](https://overthewire.org/wargames/bandit/bandit17.html)
## Objective of the game
Find the password file. It will give us access to the next level.

First connect to server by using the command
``` 
ssh bandit0@bandit.labs.overthewire.org -p 2220 
```
`Password : bandit0`
### Level 0 -> Level 1
---
The password is stored in a file called readme in the home directory.
```bash
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
```
*ls* is used to list the directories present.\
*cat* command is used to view the contents of a file, here, contents of readme file.


### Level 1 -> Level 2
---
To go the next level use
```
ssh bandit1@localhost
```
The password is stored in a file named **-** in the home directory. We cannot use cat - to directly view the content of the file and so we will use `cat ./-`
```bash
bandit1@bandit:~$ ls
-
bandit1@bandit:~$ cat ./-
CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```
*cat ./-* is used as - (hyphen) is considered as stdin/stout by cat command. We use ./ to refer to file address.

### Level 2 -> Level 3
---
To go the next level use
```
ssh bandit2@localhost
```
The password is stored in a file called spaces in the filemname\
We cannot access files with spaces in their name directly by using cat
```bash
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
We used apostrophe with the file name as terminal considers spaces as null.
Another approach is using backslash before using space in the cat command
```bash
bandit2@bandit:~$ cat spaces\ in\ this\ filename
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

### Level 3 -> Level 4
---
To go the next level use
```
ssh bandit3@localhost
```
The password is stored in a hidden file in the inhere directory
```bash
bandit3@bandit:~$ ls
inhere
bandit3@bandit:~$ cd inhere
bandit3@bandit:~/inhere$ ls -al
total 12
drwxr-xr-x 2 root    root    4096 May  7  2020 .
drwxr-xr-x 3 root    root    4096 May  7  2020 ..
-rw-r----- 1 bandit4 bandit3   33 May  7  2020 .hidden
bandit3@bandit:~/inhere$ cat ./'.hidden'
pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```
We run ls command with -al parameter. It lists all files including the hidden one and we found the .hidden file. In Linux, the file with a dot(.) in front of the name of the file makes it hidden.


### Level 4 -> Level 5
---
To go the next level use
```
ssh bandit3@localhost
```
The password is stored in a only human-readable file in the inhere directory
```bash
bandit4@bandit:~$ ls
inhere
bandit4@bandit:~$ cd inhere
bandit4@bandit:~/inhere$ file ./*
./-file00: data
./-file01: data
./-file02: data
./-file03: data
./-file04: data
./-file05: data
./-file06: data
./-file07: ASCII text
./-file08: data
./-file09: data
bandit4@bandit:~/inhere$ cat ./-file07
koReBOKuIDDepwhWk7jZC0RTdopnAYKh

```

Resources: [Geeksforgeeks - file command in linux](https://www.geeksforgeeks.org/file-command-in-linux-with-examples/)
