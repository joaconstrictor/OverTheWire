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
