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
ssh bandit4@localhost
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

### Level 5 -> Level 6
---
To go the next level use
```
ssh bandit5@localhost
```
The password is stroed in the inhere directory which human readable, 1033 bytes in size and not executable
```bash
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

```bash
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
```bash
bandit7@bandit:~$ ls
data.txt
bandit7@bandit:~$ grep -w millionth ./data.txt
millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```
We are using grep command. Grep is a Linux / Unix command-line tool used to search for a string of characters in a specified file. Although we only searched for the word milllionth, we got the whole line as output as grep gives the whole line where the match is found as output.
```bash
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
```bash
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
```bash
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
```bash
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
```bash
bandit11@bandit:~$ cat data.txt | tr ‘n-za-mN-ZA-M’ ‘a-zA-Z’
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```
the command `tr` means translate. Here we view the file using `cat` which serves as an input for the tr command. Using `man tr` we get the description of `tr` as Translate, squeeze, and/or delete characters from standard input, writing to standard output. The command `tr ‘n-za-mN-ZA-M’ ‘a-zA-Z’` is basically saying translate/transform the range of characters  n->m to a->z   but since n-m is a bit vague so it is written as n-za-m (which is the english alphabets if 13th letter becomes 1st letter) and it also it is done for both small and capital letters.\
Resource: https://www.chmag.in/articles/momsguide/decoding-rot-using-the-echo-and-tr-commands-in-your-linux-terminal/

## Level 12 -> Level 13
To go to the next level
```
ssh bandit12@localhost
```
The password is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed.
```bash
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
Looking at a hex dump of data is usually done in the context of reverse engineering. This level needs to reverse hex dump and then decompress the file to find out the password. Above you will find use of `tar` commmand. GNU 'tar' saves many files together into a single tape or disk archive, and can restore individual files from the archive. In the `tar -xvf` command, -x extracts files from a archive, -v gives verbose output and -f use the particular file mentioned after the command. `xxd` command creates a hex dump of a given file or standard input. It can also convert a hex dump back to its original binary form (`xxd -r`). `cp` command is used to copy files and directories. Whne we use the command `cp data.txt /tmp/huehue` we copy the file data.txt to the directory `/tmp/huehue`. When you do a `cat` command on data.txt, you will see a hex dump as output. To reverse the hex dump and save the result in another file we use the command `xxd -r data.txt data1`. `mv` command 
Next Level:
`The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL`
