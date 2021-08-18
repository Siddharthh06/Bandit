# WalkThrough - Bandit Game

Step by step method to solve the Bandit wargame.

First connect to server by using the command
``` 
ssh bandit0@bandit.labs.overthewire.org -p 2220 
```
> Password : bandit0
### Level 0 -> Level 1
---
The password is stored in a file called readme in the home directory.
```bash
bandit0@bandit:~$ ls
readme
bandit0@bandit:~$ cat readme
boJ9jbbUNNfktd78OOpsqOltutMc3MY1
bandit0@bandit:~$
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
