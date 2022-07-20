**Level 0**

The goal of this level is for you to log into the game using SSH. The host to which you need to connect is bandit.labs.overthewire.org, on port 2220. The username is bandit0 and the password is bandit0. Once logged in, go to the Level 1 page to find out how to beat Level 1.

#### command: ####

    ssh bandit0@bandit.labs.overthewire.org -p 2220

password: bandit0

**Level 0 - 1**

The password for the next level is stored in a file called readme located in the home directory. Use this password to log into bandit1 using SSH. Whenever you find a password for a level, use SSH (on port 2220) to log into that level and continue the game.

#### command: ####

    cat readme 

password: boJ9jbbUNNfktd78OOpsqOltutMc3MY1

**Level 1 - 2**

The password for the next level is stored in a file called - located in the home directory

#### command: ####

    cat ./-

password: CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9

(to cat a file that starts with "-" use the above command)

**Level 2 - 3**

The password for the next level is stored in a file called spaces in this filename located in the home directory

#### command: ####

    cat spaces\ in\ this\ filename 

password: UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK

**Level 3 - 4**

The password for the next level is stored in a hidden file in the inhere directory.

#### commands: ####

    ls -a inhere
    ls -a inhere/.hidden

password: pIwrPrtPN36QITSp3EQaw936yaFoFgAB

**Level 4 - 5**

The password for the next level is stored in the only human-readable file in the inhere directory. Tip: if your terminal is messed up, try the “reset” command. 

#### commands: ####

    cd inhere
    cat ./-file07

password: koReBOKuIDDepwhWk7jZC0RTdopnAYKh

(I had to look into each file to find the password)

**Level 5 - 6**

The password for the next level is stored in a file somewhere under the inhere directory and has all of the following properties:

human-readable / 1033 bytes in size / not executable

#### commands: ####

    find . -type f -size 1033c
    cat maybehere07/.file2

password: DXjZPULLxYr17uwoI01bNLQbtFemEgo7

see this article for help with this task: [find command](https://linuxconfig.org/how-to-use-find-command-to-search-for-files-based-on-file-size)

**Level 6 - 7**

The password for the next level is stored somewhere on the server and has all of the following properties:

owned by user bandit7 / owned by group bandit6 / 33 bytes in size

#### commands: ####

    find / -group bandit6 -user bandit7 -type f -size 33c
    cat /var/lib/dpkg/info/bandit7.password

password: HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs

**Level 7 - 8**

The password for the next level is stored in the file data.txt next to the word millionth

#### command: ####

    cat data.txt | grep "millionth"

password: cvX2JJa4CFALtqS87jk27qwqGhBM9plV

**Level 8 - 9**

The password for the next level is stored in the file data.txt and is the only line of text that occurs only once

#### command: ####

    cat data.txt | sort | uniq -c

password: UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR

**Level 9 - 10**

The password for the next level is stored in the file data.txt in one of the few human-readable strings, preceded by several ‘=’ characters.

#### command: ####

    strings data.txt

password: truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk

**Level 10 - 11**

The password for the next level is stored in the file data.txt, which contains base64 encoded data

#### commands: ####

    strings data.txt
    cat data.txt | base64 -d

password: IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR

**Level 11 - 12**
The password for the next level is stored in the file data.txt, where all lowercase (a-z) and uppercase (A-Z) letters have been rotated by 13 positions

cat data.txt

Gur cnffjbeq vf 5Gr8L4qetPEsPk8htqjhRK8XSP6x2RHh

Copy data in file and paste into cyberchef. Decode with ROT13

The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu

**Level 12 - 13**
The password for the next level is stored in the file data.txt, which is a hexdump of a file that has been repeatedly compressed. For this level it may be useful to create a directory under /tmp in which you can work using mkdir. For example: mkdir /tmp/myname123. Then copy the datafile using cp, and rename it using mv (read the manpages!)

cat data.txt | xxd -r > data2

cp data2 data3.gz
gzip -d data3.gz

cp data3 data4.bz
bzip2 -d data4.bz

cp data4 data5.gz
gzip -d data5.gz

cp data5 data6.tar
tar -xf data6.tar

cp data5.bin data7.tar
tar -xf data7.tar

cp data6.bin data8.bz
bzip2 -d data8.bz

cp data8 data9.tar
tar -xf data9.tar

cp data8.bin data10.gz
gzip -d data10.gz

cat data10

The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL

**Level 13 - 14**
The password for the next level is stored in /etc/bandit_pass/bandit14 and can only be read by user bandit14. For this level, you don’t get the next password, but you get a private SSH key that can be used to log into the next level. Note: localhost is a hostname that refers to the machine you are working on

bandit13 has a file called sshkey.private, this is the id_rsa key for bandit14. ssh into bandit14 using this key.

### commands: ###

	ssh -i sshkey.private bandit14@localhost

	cat /etc/bandit_pass/bandit14

Password: 4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e

**Level 14 - 15**
The password for the next level can be retrieved by submitting the password of the current level to port 30000 on localhost.

### commands: ###
	
	echo "4wcYUJFw0k0XLShlDzztnTBHiqxU3b3e" | nc localhost 30000 localhost.

**Level 15 - 16**
The password for the next level can be retrieved by submitting the password of the current level to port 30001 on localhost using SSL encryption.

Helpful note: Getting “HEARTBEATING” and “Read R BLOCK”? Use -ign_eof and read the “CONNECTED COMMANDS” section in the manpage. Next to ‘R’ and ‘Q’, the ‘B’ command also works in this version of that command…

### commands ###

	openssl s_client -connect localhost:30001

enter password for task 14 and press enter.

Password: cluFn7wTiGryunymYOu4RcffSxQluehd

**Level 16 - 17**
The credentials for the next level can be retrieved by submitting the password of the current level to a port on localhost in the range 31000 to 32000. 

First find out which of these ports have a server listening on them. Then find out which of those speak SSL and which don’t. There is only 1 server that will give the next credentials, the others will simply send back to you whatever you send to it.

![Screen Shot 2022-07-19 at 21.53.44.png](:/8b8b9637059c49bcb940b2ac9e2e492e)

### commands ###

	openssl s_client -connect localhost:31790

enter password for task 16 and press enter.
	
![Screen Shot 2022-07-19 at 21.55.41.png](:/54f6710a551246f3ba6aab9afa6b2b53)

I then exited and saved the id_rsa into a file. Changed its permission and logged in to bandit17

### commands ###

	ssh -i id_rsa_bandit17 bandit17@bandit.labs.overthewire.org -p 2220


**Level 17 - 18**
There are 2 files in the homedirectory: passwords.old and passwords.new. The password for the next level is in passwords.new and is the only line that has been changed between passwords.old and passwords.new

NOTE: if you have solved this level and see ‘Byebye!’ when trying to log into bandit18, this is related to the next level, bandit19

### commands ###

	diff passwords.old passwords.new 

Password: kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
