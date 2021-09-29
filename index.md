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
- [Level 15-16](https://overthewire.org/wargames/bandit/bandit16.html)
- [Level 16-17](https://overthewire.org/wargames/bandit/bandit17.html)
- [Level 17-18](https://overthewire.org/wargames/bandit/bandit18.html)
- [Level 18-19](https://overthewire.org/wargames/bandit/bandit19.html)
- [Level 19-20](https://overthewire.org/wargames/bandit/bandit20.html)
- [Level 20-21](https://overthewire.org/wargames/bandit/bandit21.html)
- [Level 21-22](https://overthewire.org/wargames/bandit/bandit22.html)

## Objective of the game
Find the password file. It will give us access to the next level.
___
##### First connect to server by using the command
``` 
ssh bandit0@bandit.labs.overthewire.org -p 2220 
```
`Password : bandit0`
### Level 0 -> Level 1
---
The password is stored in a file called readme in the home directory.
```
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
```
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
```
bandit2@bandit:~$ ls
spaces in this filename
bandit2@bandit:~$ cat "spaces in this filename"
UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```
We used apostrophe with the file name as terminal considers spaces as null.
Another approach is using backslash before using space in the cat command
```
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
```
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
ssh bandit4@localhost
```
The password is stored in a only human-readable file in the inhere directory
```
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

### Level 5 -> Level 6
---
To go the next level use
```
ssh bandit5@localhost
```
The password is stroed in the inhere directory which human readable, 1033 bytes in size and not executable
```
bandit5@bandit:~$ ls
inhere
bandit5@bandit:~$ cd inhere
bandit5@bandit:~/inhere$ ls
maybehere00  maybehere03  maybehere06  maybehere09  maybehere12  maybehere15  maybehere18
maybehere01  maybehere04  maybehere07  maybehere10  maybehere13  maybehere16  maybehere19
maybehere02  maybehere05  maybehere08  maybehere11  maybehere14  maybehere17
bandit5@bandit:~/inhere$ find -size 1033c
./maybehere07/.file2
bandit5@bandit:~/inhere$ cat ./maybehere07/.file2
DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```
Resources: [find command in linux](https://www.ducea.com/2008/02/12/linux-tips-find-all-files-of-a-particular-size/) to find file of particular size.

### Level 6 -> Level 7
---
To go the next level use
```
ssh bandit6@localhost
```
The password is stored somewhere on the server having properties:
- owned by user bandit7
- owned y group bandit6
- 33 bytes in size

```
bandit6@bandit:~$ find / -user bandit7 -size 33c
find: ‘/root’: Permission denied
find: ‘/home/bandit28-git’: Permission denied
find: ‘/home/bandit30-git’: Permission denied
find: ‘/home/bandit5/inhere’: Permission denied
find: ‘/home/bandit27-git’: Permission denied
find: ‘/home/bandit29-git’: Permission denied
find: ‘/home/bandit31-git’: Permission denied
find: ‘/lost+found’: Permission denied
/etc/bandit_pass/bandit7
find: ‘/etc/ssl/private’: Permission denied
find: ‘/etc/polkit-1/localauthority’: Permission denied
find: ‘/etc/lvm/archive’: Permission denied
find: ‘/etc/lvm/backup’: Permission denied
find: ‘/sys/fs/pstore’: Permission denied
find: ‘/proc/tty/driver’: Permission denied
find: ‘/proc/30446/task/30446/fd/6’: No such file or directory
find: ‘/proc/30446/task/30446/fdinfo/6’: No such file or directory
find: ‘/proc/30446/fd/5’: No such file or directory
find: ‘/proc/30446/fdinfo/5’: No such file or directory
find: ‘/cgroup2/csessions’: Permission denied
find: ‘/boot/lost+found’: Permission denied
find: ‘/tmp’: Permission denied
find: ‘/run/lvm’: Permission denied
find: ‘/run/screen/S-bandit26’: Permission denied
find: ‘/run/screen/S-bandit5’: Permission denied
find: ‘/run/screen/S-bandit19’: Permission denied
find: ‘/run/screen/S-bandit0’: Permission denied
find: ‘/run/screen/S-bandit12’: Permission denied
find: ‘/run/screen/S-bandit1’: Permission denied
find: ‘/run/screen/S-bandit22’: Permission denied
find: ‘/run/screen/S-bandit21’: Permission denied
find: ‘/run/screen/S-bandit4’: Permission denied
find: ‘/run/screen/S-bandit18’: Permission denied
find: ‘/run/screen/S-bandit3’: Permission denied
find: ‘/run/screen/S-bandit31’: Permission denied
find: ‘/run/screen/S-bandit23’: Permission denied
find: ‘/run/screen/S-bandit24’: Permission denied
find: ‘/run/screen/S-bandit25’: Permission denied
find: ‘/run/screen/S-bandit20’: Permission denied
find: ‘/run/shm’: Permission denied
find: ‘/run/lock/lvm’: Permission denied
find: ‘/var/spool/bandit24’: Permission denied
find: ‘/var/spool/cron/crontabs’: Permission denied
find: ‘/var/spool/rsyslog’: Permission denied
find: ‘/var/tmp’: Permission denied
find: ‘/var/lib/apt/lists/partial’: Permission denied
find: ‘/var/lib/polkit-1’: Permission denied
/var/lib/dpkg/info/bandit7.password
find: ‘/var/log’: Permission denied
find: ‘/var/cache/apt/archives/partial’: Permission denied
find: ‘/var/cache/ldconfig’: Permission denied
bandit6@bandit:~$ cat /var/lib/dpkg/info/bandit7.password
HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```
To use find on the entire server we use `find /`

### Level 7 -> Lever 8
---
To go to the next level
```
ssh bandit7@localhost
```
The password is stored in a file named data.txt next to the word millionth.
```
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep -w millionth ./data.txt
millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
We are using grep command. Grep is a Linux / Unix command-line tool used to search for a string of characters in a specified file. Although we only searched for the word milllionth, we got the whole line as output as grep gives the whole line where the match is found as output.
```
bandit7@bandit:~$ cat data.txt | grep millionth
millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
Here we are using Unix pipe (|). The Pipe connects the standard output from the first command and feeds it as standard input to the second command.

### Level 8 -> Level 9
To go to the next level
```
ssh bandit8@localhost
```
The password is stored in the file data.txt and is the only line that occurs only once
```
bandit8@bandit:~$ ls
data.txt
bandit8@bandit:~$ sort data.txt | uniq -c
     10 07KC3ukwX7kswl8Le9ebb3H3sOoNTsR2
     10 0efnqHY1ZTNRu4LsDX4D73DsxIQq7RuJ
     10 0N65ZPpNGkUJePzFxctCRZRXVrCbUGfm
     10 0Xo6DLyK5izRqEtBA7sW2SRmlAixWYSg
     10 10XitczY5Dz7UMoseKIeFWSzzwQrylfw
     10 1ETSsKgjfQj1cJeFzXLJWzKzza3iWcJa
     10 1T6qw9I32d71cS3TTvwmVp1WsxPFDJ9I
     10 2bFz9F0yRwxGzVCZ4Er04bk00qfUrzWb
     10 2CxmtCkpNL5ZjuoNzAtShkPXf5T43W7s
     10 337o85y4OymIh99WPUtotkb114evfAkC
     10 33xpPQhjt4Q2mqtX4sCVRwH2Zyh82E8R
     10 4SMqyZZztep75cte6xxKpVL49pKUkV8N
     10 5AdqWjoJOEdx5tJmZVBMo0K2e4arD3ZW
     10 5cO8XuoQWrzsyeOWDht8zgUIVWSRDaeC
     10 6PF22p6O8TphCTZot9ApZx8VfGuo8rd5
     10 7KaMzgnYMUeMISP9vuT3Dvsc06qfqa9u
     10 7uhj3nhe4AS0esnnEZHBAZN67fJ8BFjM
     10 8jtZmvqp9PTi8tp1oybBM663NQH3fhII
     10 8NtHZnWzCA8HswoJSCU7Ojg8nP3eKpsA
     10 aR2QhaBoDMncvJqPWkvLXMzEx9meBIbX
     10 BccauS9LeE8NUz4HVLXUwE8M1LWisPlG
     10 bRnktwNdxFy2RPZIshXJikswwEzJGvJ9
     10 cIPbot7oYveUPNxDMhv1hiri50CqpkTG
     10 cR6riSWC0ST7ALZ2i1e47r3gc0QxShGo
     10 CUqLkjIo0Jz9fNgrjPxiPa7PGGC1wpTQ
     10 dGnfD2LoqTiO1MBf2vmqw1KKEWSHfMKJ
     10 dqd5wTVO1cVPJoEY7GGkCdGxG6ZYqW98
     10 dqnvnNxL4QR3ALq95ckhZwEpl77cRgF4
     10 DqPqVp8YCjZ1vFsclwRTg13EuSc2D52X
     10 dV0aGGhk6mB4ZJX1aTTluAUIvLWToTYr
     10 DxxLvJl6cGHXLT7OW4xqS7Qrfny1K01l
     10 e5HFl4ur1rAxPPv2mHzg1uYKMuos4fwp
     10 Ef509iQpb5gQJsjz5dMXLxpeAfkbLOrw
     10 eTHlmI3pFZ4FQASs32Dm0ETVZWHlP0I1
     10 f0tri5KLH5eiTU0zQOqWvXTsrl1ekqnU
     10 f6ZuiZizTliaMOkVYXZMudtaReSYMnkP
     10 flyKxCbHB8uLTaIB5LXqQNuJj3yj00eh
     10 g1VkH2pk3cmr6aY4np1Dcpm0HF7G9IDT
     10 g9xRXSlVNiV4EhUAl1p6uPUWcyEewDK6
     10 gqyF9CW3NNIiGW27AtWVNPqp3i1fxTMY
     10 h2IsJoN6fe0ne0qrTQxeiu0P44hMWWbk
     10 hA6Ofhj75FPgqnCKEJ9g6pLSKapxxmGC
     10 Hq6uxRAkKPNLnH6eRSFDzXtvVt0CSsee
     10 I3fc578VLa7mOQ1t9zArPPOPY7aDVBcJ
     10 iIaOHQG7ZLdimomwMQaGIF7vib1RmXBh
     10 IkAAyqo1rCrxdY8qH0FfxXkRTTO2GNSf
     10 iKiMcQpNMn2ImOASX39XBUR8XfApdmsj
     10 InU7h0xhZh4SMMOMvlnsq03pz0k9J5FX
     10 iwE0KTeKQ8PWihqvjUnpu52YZeIO8Pqb
     10 J6Lzp6ZqTJsOuJRTXcvhwKfM0KK3Xtbl
     10 K9D1CLsVCdkodgvJJIt1oHIaiOY1h8hg
     10 KASHOxc1NxaM8caXUw5MHCkddANXOkCu
     10 khecG2RClunkhrgmq4UNB26N5F1yiUwL
     10 kJTBMD8k9OHyXwZ2aJMQkV23u0gyuoIO
     10 KLu6irnqFwhOKnVoTwuoT9e5t6oxYQwv
     10 KrDVVORXLPfRhfnRmmuP3OnVHWKDMSM8
     10 kUbOkhsIw6GSp0WI2YUo1Q3hDxFU0iQn
     10 l1I3Red7uSH9n30OylHP2hQDbOU0qGaq
     10 l2lECnJkQk8EBl6IO3gHUlnjoCTF1has
     10 LfrBHfAh0pP9bgGAZP4QrVkut3pysAYC
     10 Lg4vWWvEY7s0bG6BRiA35AHzo2gM6lHg
     10 mpgNGRH628hTQxajScbagkxaPKklUhjn
     10 mzOW32HQZi14kwrdeiquO1LCbyaOtbiT
     10 nJRb4MipHMdTmFylFc1NlqmywgxDSdoI
     10 NLWvtQvL7EaqBNx2x4eznRlQONULlCYZ
     10 NOdH1kFWibx4XnNaJoLFmghBn7oIs5hb
     10 ojGabNG5NJ9ppKUBXGr8lwMRRS5GuiA5
     10 OZ1wgx8bDI0vFOFxDQH32eMMcIPiIuPE
     10 PfbMe4Xb3mw5mJmabIbKAXKCU7zynDHl
     10 PQKOeIQwTw490Y8yobuxZAOL4cNmVo1D
     10 PSdVQSeUUBPRZD58WWP0OXLKxSgU3RxX
     10 ptb5ZW8TcgD3U6gOGCcN31xCDGIoQSEa
     10 qaWWAOOquC3yHnfJI4zvPWzCBdfHQ8wa
     10 RMiSPoAvF7WhgIcOdSQR2r6Zx0DNS5UW
     10 s1603Q2r4RPKqyoA8cspIRk0VdgEmFC3
     10 SA05uWMVCao2rzS8YRqUXh19SvnDpuOl
     10 SHMAMUEzQe4mV7SJpETTZFsyNRJsZE2k
     10 si952kS1y6pt4AFenmm0oIp8n7W5d3bd
     10 sYSokIATVvFUKU4sAHTtMarfjlZWWj5i
     10 SzwgS2ADSjP6ypOzp2bIvdqNyusRtrHj
     10 TKUtQbeYnEzzYIne7BinoBx2bHFLBXzG
     10 TThRArdF2ZEXMO47TIYkyPPLtvzzLcDf
     10 tVW9iY1Ml0uHPK4usZnN8oZXbjRt2ATY
     10 U0NYdD3wHZKpfEg9qGQOLJimAJy6qxhS
     10 UASW6CQwD6MRzftu6FAfyXBK0cVvnBLP
     10 UJiCNvDNfgb3fcCj8PjjnAXHqUM63Uyj
     10 UjsVbcqKeJqdCZQCDMkzv6A9X7hLbNE4
      1 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
     10 UVnZvhiVQECraz5jl8U14sMVZQhjuXia
     10 V2d9umHiuPLYLIDsuHj0frOEmreCZMaA
     10 v9zaxkVAOdIOlITZY2uoCtB1fX2gmly9
     10 VkBAEWyIibVkeURZV5mowiGg6i3m7Be0
     10 w4zUWFGTUrAAh8lNkS8gH3WK2zowBEkA
     10 WBqr9xvf6mYTT5kLcTGCG6jb3ex94xWr
     10 wjNwumEX58RUQTrufHMciWz5Yx10GtTC
     10 X1JHOUkrb4KgugMXIzMWWIWvRkeZleTI
     10 XyeJdbrUJyGtdGx8cXLQST0pwu5cvpcA
     10 yo0HbSe2GM0jJNhRQLxwoPp7ayYEmRKY
     10 ySvsTwlMgnUF0n86Fgmn2TNjkSOlrV72
     10 Z9OC6DQpppreChPhwRJJV9YYTtrxNVcO
     10 zdd2ctVveROGeiS2WE3TeLZMeL5jL7iM
```
So, the password is `UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR`.\
We used two command here that are connected unix pipe. 

### Level 9 -> Level 10
To go to the next level
```
ssh bandit9@localhost
```
The password is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.
```
bandit9@bandit:~$ ls
data.txt
bandit9@bandit:~$ cat data.txt | strings | grep ==
========== the*2i"4
========== password
Z)========== is
&========== truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
```
First we use cat to view the contents of the file data.txt and serve as input for the strings command. We use the unix pipe (|) as it sends output of one command as input of the other. Then we use strings command.
- String: Display printable strings in [file(s)] (stdin by default)

This converts the text in the file in strings format. Then we use grep to find the line with more than 1 '=' character as it is given that the password is preceeded by several '=' characters.\

### Level 10 -> Level 11
To go to the next level
```
ssh bandit10@localhost
```
The password is stored in the file data.txt, which contains base64 encoded data
```
bandit10@bandit:~$ cat data.txt | base64 -d
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```
Using cat to view the content of the file and use it as input for the base64 command using unix pipe (|). `base64 -d` is the command to decode data

### level 11 -> Level 12
To go to the next level 
```
ssh bandit11@localhost
```
The password is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions (ROT 13 cipher)
```
bandit11@bandit:~$ cat data.txt | tr ‘n-za-mN-ZA-M’ ‘a-zA-Z’
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```
the command `tr` means translate. Here we view the file using `cat` which serves as an input for the tr command. Using `man tr` we get the description of `tr` as Translate, squeeze, and/or delete characters from standard input, writing to standard output. The command `tr ‘n-za-mN-ZA-M’ ‘a-zA-Z’` is basically saying translate/transform the range of characters  n->m to a->z   but since n-m is a bit vague so it is written as n-za-m (which is the english alphabets if 13th letter becomes 1st letter) and it also it is done for both small and capital letters.\
Resource: https://www.chmag.in/articles/momsguide/decoding-rot-using-the-echo-and-tr-commands-in-your-linux-terminal/

### Level 12 -> Level 13
To go to the next level
```
ssh bandit12@localhost
```
The password is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.
```
bandit12@bandit:~$ ls
data.txt
bandit12@bandit:~$ mkdir /tmp/huehue
bandit12@bandit:~$ cp data.txt /tmp/huehue
bandit12@bandit:~$ cd /tmp/huehue
bandit12@bandit:/tmp/huehue$ xxd -r data.txt data1
bandit12@bandit:/tmp/huehue$ ls
data1  data.txt
bandit12@bandit:/tmp/huehue$ file data1
data1: gzip compressed data, was "data2.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/huehue$ mv data1 data2.gz
bandit12@bandit:/tmp/huehue$ gzip -d data2.gz
bandit12@bandit:/tmp/huehue$ ls
data2  data.txt
bandit12@bandit:/tmp/huehue$ file data2
data2: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/huehue$ mv data2 data3.bz2
bandit12@bandit:/tmp/huehue$ bzip2 -d data3.bz2
bandit12@bandit:/tmp/huehue$ file data3
data3: gzip compressed data, was "data4.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/huehue$ mv data3 data4.gz
bandit12@bandit:/tmp/huehue$ gzip -d data4.gz
bandit12@bandit:/tmp/huehue$ ls
data4  data.txt
bandit12@bandit:/tmp/huehue$ file data4
data4: POSIX tar archive (GNU)
bandit12@bandit:/tmp/huehue$ mv data4 data5.tar
bandit12@bandit:/tmp/huehue$ tar -xvf data5.tar
data5.bin
bandit12@bandit:/tmp/huehue$ file data5.bin
data5.bin: POSIX tar archive (GNU)
bandit12@bandit:/tmp/huehue$ mv data5.bin data6.tar
bandit12@bandit:/tmp/huehue$ tar -xvf data6.tar
data6.bin
bandit12@bandit:/tmp/huehue$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
bandit12@bandit:/tmp/huehue$ mv data6.bin data7.bz2
bandit12@bandit:/tmp/huehue$ bzip2 -d data7.bz2
bandit12@bandit:/tmp/huehue$ ls
data5.tar  data6.tar  data7  data.txt
bandit12@bandit:/tmp/huehue$ file data7
data7: POSIX tar archive (GNU)
bandit12@bandit:/tmp/huehue$ mv data7 data8.tar
bandit12@bandit:/tmp/huehue$ tar -xvf data8.tar
data8.bin
bandit12@bandit:/tmp/huehue$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu May  7 18:14:30 2020, max compression, from Unix
bandit12@bandit:/tmp/huehue$ mv data8.bin data9.gz
bandit12@bandit:/tmp/huehue$ gzip -d data9.gz
bandit12@bandit:/tmp/huehue$ file data9
data9: ASCII text
bandit12@bandit:/tmp/huehue$ cat data9
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```
Looking at a hex dump of data is usually done in the context of reverse engineering. This level needs to reverse hex dump and then decompress the file to find out the password. Above you will find use of `tar` commmand. GNU 'tar' saves many files together into a single tape or disk archive, and can restore individual files from the archive. In the `tar -xvf` command, -x extracts files from a archive, -v gives verbose output and -f use the particular file mentioned after the command. `xxd` command creates a hex dump of a given file or standard input. It can also convert a hex dump back to its original binary form (`xxd -r`). `cp` command is used to copy files and directories. Whne we use the command `cp data.txt /tmp/huehue` we copy the file data.txt to the directory `/tmp/huehue`. When you do a `cat` command on data.txt, you will see a hex dump as output. To reverse the hex dump and save the result in another file we use the command `xxd -r data.txt data1`. `mv` stands for move. `mv` command is used to move one or more files or directories from one place to another in a file system.
Next Level:
`The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL`

### Level 13 -> Level 14
To go to the next level
```
ssh bandit13@localhost
```
The password is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. 
```
bandit13@bandit:~$ ssh bandit14@localhost -i sshkey.private
Could not create directory '/home/bandit13/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes
```
`-i` is used to identify files\
We use the ssh command to go the next level.

### Level 14 -> Level 15
To go to the next level
```
ssh bandit14@localhost
```
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.
```
bandit14@bandit:~$ cat /etc/bandit_pass/bandit14
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
bandit14@bandit:~$ telnet localhost 30000
Trying 127.0.0.1...
Connected to localhost.
Escape character is '^]'.
4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr

Connection closed by foreign host.
```
To find the flag, we first need to find the password for the current level. The password is stored in the /etc directory since it is the directory where the configuration files are saved.\
To read more about directory structure in linux refer [this](https://www.howtogeek.com/117435/htg-explains-the-linux-directory-structure-explained/)\
Next we use telnet to connect to the localhost at the port 30000 using the command `telnet localhost 30000`\
To understand the basics of telnet, refer [this](https://www.youtube.com/watch?v=tZop-zjYkrU) or [Linux telnel command](https://www.javatpoint.com/linux-telnet-command)\

### Level 15 -> Level 16
To go to the next level
```
ssh bandit15@localhost
```
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.
```
bandit15@bandit:~$ openssl s_client -connect localhost:30001
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
---
Certificate chain
 0 s:/CN=localhost
   i:/CN=localhost
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICBjCCAW+gAwIBAgIEHxhZ+zANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjEwODA1MjEyMjEzWhcNMjIwODA1MjEyMjEzWjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBALqNmx6R
csRsPgzRcRsq5oQ4BC9AT/Yu473WbK4SRjHOWwuA4Oqk9w8SLKYZ39FrDEnXSZJw
xqKPR0AH72+l7Itv7X1H07VbeMTQoJVm6NsJm3cuyyxjRwfaIOUFsRtQQyvQlmw7
3CgTbd3wEk1CD+6jlksJj801Vd0uvZh1VVERAgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBADjhbe3bTnDWsS4xt8FFg7PJIqNAxF6QjP+7xzJ4yMvWtPP6tVXo
F7SNI52juwH0nFDyM9KOrM/AknWqCYF+yfz6bLD7MaKZ+Kg3DiLaoVJOrVg6Y02+
0vq1rLsqGko5wamCFamx7X9CtFsV0WQjZdA53Na/VwehtlFpf/p20VAi
-----END CERTIFICATE-----
subject=/CN=localhost
issuer=/CN=localhost
---
No client certificate CA names sent
Peer signing digest: SHA512
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1019 bytes and written 269 bytes
Verification error: self signed certificate
---
New, TLSv1.2, Cipher is ECDHE-RSA-AES256-GCM-SHA384
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES256-GCM-SHA384
    Session-ID: 8C9B89A58FB05A841FC0BA4D42024567FCAFABECC36A28FC9887C285274845BE
    Session-ID-ctx: 
    Master-Key: 1BB7EF11284E6DDD69427BA9535DE954EA6F929082166C5A8CF679DCE9772B15BF2B09873675B23CBDBBE20251BDD200
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 3a a9 fe 3b 12 a1 ed 2b-8d a6 cf aa 23 c9 12 88   :..;...+....#...
    0010 - 0c 2f 32 07 e4 e6 75 34-3e 85 40 8a 32 cd 5c b1   ./2...u4>.@.2.\.
    0020 - 31 c6 74 04 e5 3e cd 64-55 2d 9b f6 4c 2d f3 9e   1.t..>.dU-..L-..
    0030 - db 1c fc 28 3f 7d 4c 0f-c5 15 01 44 69 b7 b0 ae   ...(?}L....Di...
    0040 - 5f 3d 1e 9e 04 d0 2c 36-5b 34 75 77 dc 89 db 70   _=....,6[4uw...p
    0050 - 02 b7 53 b5 6e 15 3b de-a5 e9 46 b7 50 1e e1 f0   ..S.n.;...F.P...
    0060 - 88 0e ec 75 45 51 d8 72-de 6f 94 33 6a 83 38 91   ...uEQ.r.o.3j.8.
    0070 - fe c8 c5 c7 7a 7b 01 7a-be d0 bf 26 0f b2 ec 47   ....z{.z...&...G
    0080 - ab 3b f4 28 31 71 58 61-2e f8 78 7f d1 7f c3 1e   .;.(1qXa..x.....
    0090 - a9 11 e5 77 21 60 67 2f-ed 89 0c 71 54 20 5d a3   ...w!`g/...qT ].

    Start Time: 1632766903
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
BfMYroe26WYalil77FoDi9qh59eK5xNr         
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed
```
We will use the `openssl` command to connect as we have to connect using ssl encryption. 

### Level 16 -> Level 17
To go to the next level
```
ssh bandit16@localhost
```
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.
```
bandit16@bandit:~$ nmap -A localhost -p 31000-32000

Starting Nmap 7.40 ( https://nmap.org ) at 2021-09-27 20:27 CEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00022s latency).
Not shown: 996 closed ports
PORT      STATE SERVICE     VERSION
31046/tcp open  echo
31518/tcp open  ssl/echo
| ssl-cert: Subject: commonName=localhost
| Subject Alternative Name: DNS:localhost
| Not valid before: 2021-08-05T21:23:01
|_Not valid after:  2022-08-05T21:23:01
|_ssl-date: TLS randomness does not represent time
31691/tcp open  echo
31790/tcp open  ssl/unknown
| fingerprint-strings: 
|   FourOhFourRequest, GenericLines, GetRequest, HTTPOptions, Help, Kerberos, LDAPSearchReq, LPDString, RTSPRequest, SIPOptions, SSLSessionReq, TLSSessionReq: 
|_    Wrong! Please enter the correct current password
| ssl-cert: Subject: commonName=localhost
| Subject Alternative Name: DNS:localhost
| Not valid before: 2021-08-05T21:23:01
|_Not valid after:  2022-08-05T21:23:01
|_ssl-date: TLS randomness does not represent time
31960/tcp open  echo
1 service unrecognized despite returning data. If you know the service/version, please submit the following fingerprint at https://nmap.org/cgi-bin/submit.cgi?new-service :
SF-Port31790-TCP:V=7.40%T=SSL%I=7%D=9/27%Time=61520D11%P=x86_64-pc-linux-g
SF:nu%r(GenericLines,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20cu
SF:rrent\x20password\n")%r(GetRequest,31,"Wrong!\x20Please\x20enter\x20the
SF:\x20correct\x20current\x20password\n")%r(HTTPOptions,31,"Wrong!\x20Plea
SF:se\x20enter\x20the\x20correct\x20current\x20password\n")%r(RTSPRequest,
SF:31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\
SF:n")%r(Help,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x
SF:20password\n")%r(SSLSessionReq,31,"Wrong!\x20Please\x20enter\x20the\x20
SF:correct\x20current\x20password\n")%r(TLSSessionReq,31,"Wrong!\x20Please
SF:\x20enter\x20the\x20correct\x20current\x20password\n")%r(Kerberos,31,"W
SF:rong!\x20Please\x20enter\x20the\x20correct\x20current\x20password\n")%r
SF:(FourOhFourRequest,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20c
SF:urrent\x20password\n")%r(LPDString,31,"Wrong!\x20Please\x20enter\x20the
SF:\x20correct\x20current\x20password\n")%r(LDAPSearchReq,31,"Wrong!\x20Pl
SF:ease\x20enter\x20the\x20correct\x20current\x20password\n")%r(SIPOptions
SF:,31,"Wrong!\x20Please\x20enter\x20the\x20correct\x20current\x20password
SF:\n");

Service detection performed. Please report any incorrect results at https://nmap.org/submit/ .
Nmap done: 1 IP address (1 host up) scanned in 90.01 seconds
bandit16@bandit:~$ openssl s_client -connect localhost:31790
CONNECTED(00000003)
depth=0 CN = localhost
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = localhost
verify return:1
---
Certificate chain
 0 s:/CN=localhost
   i:/CN=localhost
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICBjCCAW+gAwIBAgIEatsK7TANBgkqhkiG9w0BAQUFADAUMRIwEAYDVQQDDAls
b2NhbGhvc3QwHhcNMjEwODA1MjEyMzAxWhcNMjIwODA1MjEyMzAxWjAUMRIwEAYD
VQQDDAlsb2NhbGhvc3QwgZ8wDQYJKoZIhvcNAQEBBQADgY0AMIGJAoGBALbshxNY
mdJ/7RpASCHk+XULoBymcRoKY9tPU25zhhPmrFAyv0HNXG/GqPjOxI4MHG627HOf
b00a/ikeDUTVdCiDXhungyUx6W07H3uiHHbfNLs1QGl2GPdBVA+z5DZcNsWJ1QB5
888HEzp8YNWyeHnP+5gy5LqlX5hUkF1eu6C1AgMBAAGjZTBjMBQGA1UdEQQNMAuC
CWxvY2FsaG9zdDBLBglghkgBhvhCAQ0EPhY8QXV0b21hdGljYWxseSBnZW5lcmF0
ZWQgYnkgTmNhdC4gU2VlIGh0dHBzOi8vbm1hcC5vcmcvbmNhdC8uMA0GCSqGSIb3
DQEBBQUAA4GBABVCD/dhWpgN9KC5Eb6hd9ToreRhof44OQaHalJtsayPBBMTK3Lp
KC88rNVJW+cX0z+eUe6en0RIvU56dLNT+zm9cbDvCV1cumz4++nauWes/11eA5aG
2NNgKQHYvT+bOfo3lhOQNwtzpO4MX1sGMjO4dlS4AmxTdjz0UVUPLamk
-----END CERTIFICATE-----
subject=/CN=localhost
issuer=/CN=localhost
---
No client certificate CA names sent
Peer signing digest: SHA512
Server Temp Key: X25519, 253 bits
---
SSL handshake has read 1019 bytes and written 269 bytes
Verification error: self signed certificate
---
New, TLSv1.2, Cipher is ECDHE-RSA-AES256-GCM-SHA384
Server public key is 1024 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1.2
    Cipher    : ECDHE-RSA-AES256-GCM-SHA384
    Session-ID: B0400E1CBE2CA57B65DD3FBE1749A7BE18B8A10B6E9DC28A4DD535EA67B1E141
    Session-ID-ctx: 
    Master-Key: C4F0F55E60F05F5DE1A552A3D7B91A7C38E85A19279186BCAC4A83CDAF17C7493A3BAC1A93831AD7F8050647746FE8B7
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 30 d5 a9 3d 7d a2 f1 16-f5 b3 32 79 c1 92 42 1a   0..=}.....2y..B.
    0010 - b8 74 ce 70 01 f2 1b 3c-f8 17 06 8c 31 ec f3 10   .t.p...<....1...
    0020 - 6b 44 91 bb 44 4e 70 40-2a ff 4c 3e 3d 49 ac 17   kD..DNp@*.L>=I..
    0030 - c6 29 5f 92 d7 0b fb 10-21 22 3a 6d ce 7b 30 9f   .)_.....!":m.{0.
    0040 - a5 82 b3 6c 4a 21 72 7f-c8 20 0c 6a 5d cc c2 4a   ...lJ!r.. .j]..J
    0050 - 38 13 ae 4d 6a 08 5f 7d-9f df 6a 32 31 3c 63 1f   8..Mj._}..j21<c.
    0060 - 4f bf 38 e7 e4 b2 6b d6-cf 9c 01 a3 3e 2a 9c e0   O.8...k.....>*..
    0070 - a6 05 96 d1 ae ec f8 95-b7 8f 74 ec 46 90 03 90   ..........t.F...
    0080 - 66 9c 72 d9 76 f8 b1 9e-b5 d3 d9 6f 33 11 44 fd   f.r.v......o3.D.
    0090 - 4c d0 80 e4 cc 61 0c ca-80 c9 dc 45 9f 03 de 95   L....a.....E....

    Start Time: 1632767468
    Timeout   : 7200 (sec)
    Verify return code: 18 (self signed certificate)
    Extended master secret: yes
---
cluFn7wTiGryunymYOu4RcffSxQluehd
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

closed
```
We get a RSA private key. We need to use this to go to the next level.\
Read about RSA encryption to understand this better. Resources:
- https://en.m.wikipedia.org/wiki/RSA_(cryptosystem)
- https://docs.rackspace.com/support/how-to/logging-in-with-an-ssh-private-key-on-linuxmac

```
bandit16@bandit:~$ mkdir /tmp/coolkey
bandit16@bandit:~$ cd /tmp/coolkey
bandit16@bandit:/tmp/coolkey$ nano coolkey
Unable to create directory /home/bandit16/.nano: Permission denied
It is required for saving/loading search history or cursor positions.

Press Enter to continue


bandit16@bandit:/tmp/coolkey$ chmod 600 coolkey
bandit16@bandit:/tmp/coolkey$ ssh bandit17@localhost -i coolkey
Could not create directory '/home/bandit16/.ssh'.
The authenticity of host 'localhost (127.0.0.1)' can't be established.
ECDSA key fingerprint is SHA256:98UL0ZWr85496EtCRkKlo20X3OPnyPSB5tB5RPbhczc.
Are you sure you want to continue connecting (yes/no)? yes

```
Save the private key in the same as given below in the coolkey using nano
```
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----
```

### Level 17 -> Level 18
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

```
bandit17@bandit:~$ diff passwords.new passwords.old
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
> w0Yfolrc5bwjS4qw5mq1nnQi6mF03bii
```
(use `kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd` as password)
To read about how to use `diff` command - (https://www.geeksforgeeks.org/diff-command-linux-examples/)

### Level 18 -> Level 19
To go to the next level
NOTE: We use `ssh -T` here as the .bashrc file has been modified by to log us out of ssh. We use -T parameter to disable pseudo -tty allocation, as this is making our session vulnerable. To read more about it, go to https://stackoverflow.com/questions/42505339/why-use-t-with-ssh
```
ssh -T bandit18@localhost
```
