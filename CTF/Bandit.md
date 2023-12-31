# BANDIT - OVER THE WIRE


## [Bandit Level 0](https://overthewire.org/wargames/bandit/bandit0.html)

```
ssh -p 2220 bandit0@bandit.labs.overthewire.org
```

> ### Key : bandit0


## [Bandit Level 0 -> 1](https://overthewire.org/wargames/bandit/bandit1.html)

```
ssh bandit0@bandit.labs.overthewire.org -p 2220
ls
cat readme
logout
```

> ### Key : NH2SXQwcBdpmTEzi3bvBHMM9H66vVXjL


## [Bandit Level 1 -> 2](https://overthewire.org/wargames/bandit/bandit2.html)

```
ssh -p 2220 bandit1@bandit.labs.overthewire.org
ls
cat ./-
logout

```
Note: If you have a file named - in your directory, you can display its content using the cat command with a specific syntax to prevent the hyphen from being interpreted as an option.  In Unix-like operating systems, including Linux and macOS, the prefix ./ specifies that a file or directory is in the current directory. This is particularly useful for distinguishing between built-in or system commands and files that happen to have similar or identical names.ls ano
> ### Key : rRGizSaX8Mk1RTb1CNQoXTcYZWU6lgzi


## [Bandit Level 2 -> 3](https://overthewire.org/wargames/bandit/bandit3.html)

```
ssh -p 2220 bandit2@bandit.labs.overthewire.org
ls
cat "spaces in this filename"
logout

```
Note: spaces are used to separate different command-line arguments. When you have a file name with spaces, the shell would interpret each word separated by a space as a different argument unless you explicitly tell it not to. You can wrap the file name in quotes (" or ') to tell the shell to treat it as a single argument. you can also use use a backslash (\) to escape the spaces so it would look like cat spaces\in\this\file. quotes are normally used and less prone to error, but you may use back slashes if you preffer!!c
> ### Key : aBZ0W5EmUfAf7kHTQeOwd8bauFJ2lAiG


## [Bandit Level 3 -> 4](https://overthewire.org/wargames/bandit/bandit4.html)

```
ssh -p 2220 bandit3@bandit.labs.overthewire.org
ls
cd inhere
ls -a
cat .hidden
logout
```
Note: Use ls -a to list all files, even the hidden ones! Hidden files in Unix-like operating systems start with a dot (.) . 
> ### Key : 2EW7BBsr6aMMoJ2HjW067dm8EgX26xNe


## [Bandit Level 4 -> 5](https://overthewire.org/wargames/bandit/bandit5.html)

```
ssh bandit4@bandit.labs.overthewire.org -p 2220
ls
cd inhere
ls
find . -type f -exec file {} \; | grep 'ASCI text'
cat ./-file07
logout
```
Notes
**find .** -type f -exec file {} \;: find .: The find command starts looking for files and directories from the current directory, represented by ..

**-type f:** This flag specifies to only find items that are regular files.

**-exec file {} \;:** For every file that find identifies, it executes the file command. The {} serves as a placeholder that gets replaced by the name of each file found. The \; at the end signifies the end of the -exec command.

**|:** This is a pipe. It takes the output of the command on its left (the find command in this case) and uses it as input for the command on its right.

**grep** 'ASCII text': grep is a command-line utility for searching plain-text data for lines matching a regular expression. Here it's looking for lines containing the phrase 'ASCII text'.

after you run the command ./-file07 will be identified as the ASCII text file. you could also just cat every file until you find the correct file ;) in this case that is not a big deal, but in a directory of 100s of files it might take awhile 

> ### Key : lrIWWI6bB37kxfiCQZqUdOIYfr6eEeqR


## [Bandit Level 5 -> 6](https://overthewire.org/wargames/bandit/bandit6.html)

```
ssh bandit5@bandit.labs.overthewire.org -p 2220
ls
cd inhere
find -size 1033c
cat ./maybehere07/.file2
logout
```
Note

**find -size 1033c**: This command uses the find utility to search for files in the current directory (and subdirectories) that have a size of exactly 1033 bytes. The c after the number signifies that the size is specified in bytes. This is how I solved this level, but there is more than one way I will list other options below: 

  Option 1: Using file command on each file
  You can manually check the file type of each file in the directory using the file    command: " ./* " This should output the type of each file, allowing you to      
  identify the human-readable one manually.
  
  Option 2: Use find with -exec and cat: find . -type f -exec cat {} + You can try to cat (concatenate and display) the content of each file. If the content is human-readable, it will display normally; otherwise, it will display  gibberish or escape sequences.

> ### Key : P4L4vucdmLnm8I7Vl7jG1ApGSfjYKqJU


## [Bandit Level 6 -> 7](https://overthewire.org/wargames/bandit/bandit7.html)

```
ssh bandit6@bandit.labs.overthewire.org -p 2220
ls
cd /
find -size 33c -user bandit7 -group bandit6
cat /var/lib/dpkg/info/bandit7\.passwordin
logout
```
Note: I tired to use the find command once I first entered the box it did not find anything. you can only look in the current directory. either way you are given the variables in this box if you do not understand how to use the find commnad it is always useful to use --help or just chat GPT...

> ### Key : z7WtoNQU2XfjmMtWA8u5rN4vzqu4v99S

## [Bandit Level 7 -> 8](https://overthewire.org/wargames/bandit/bandit8.html)

```
ssh bandit7@bandit.labs.overthewire.org -p 2220
ls
cat data.txt
grep -i millionth data.txt or grep -a 
logout
```
Note: Grep -i or grep -a will  work, why not try both!  grep is employed for searching plain-text data sets for lines that match a regular expression. By default, it prints the matching lines to the standard output, which is usually the terminal window. For more information you can use man grep or grep --help 

> ### Key : TESKZC0XvTetK0S9xNwm25STk5iWrBvP


## [Bandit Level 8 -> 9](https://overthewire.org/wargames/bandit/bandit9.html)

```
ssh bandit8@bandit.labs.overthewire.org -p 2220
ls
sort data.txt | uniq -u
logout
```
Note: sort data.txt: This sorts all lines in the file data.txt.
|: The pipe operator redirects the sorted output as input to the next command.
uniq -u: This removes adjacent duplicate lines from the sorted input and only outputs lines that appear exactly once. Basisically what is happening here is we are going to sort the information and use pipe to input this sorted information into uniq -u which will remove duplicated only leaving the password for the next level. 

> ### Key : EN632PlfYiZbn3PhVK3XOGSlNInNE00t


## [Bandit Level 9 -> 10](https://overthewire.org/wargames/bandit/bandit10.html)

```
ssh bandit9@bandit.labs.overthewire.org -p 2220
ls
strings data.txt | grep ==
logout
```
Note:strings data.txt: The strings command extracts printable strings from files, in this case, data.txt. This is particularly useful for binary files where text strings are embedded amongst non-printable characters. For purely text files, strings would essentially just read the file line by line.

|: The pipe (|) takes the output of strings data.txt and uses it as input for the next command.

grep '==': The grep command then searches through this input to find and display lines that contain the sequence ==.
You could also just go through the file and find the lines if you wanted to 

> ### Key : G7w8LIi6J3kTb8A7j9LgrywtEUlyyp6s


## [Bandit Level 10 -> 11](https://overthewire.org/wargames/bandit/bandit11.html)

```
ssh bandit10@bandit.labs.overthewire.org -p 2220
ls
base64 -d data.txt
logout
```
Note: Basically all we are doing on this level is useing base64 -d for decode to decode the file and it will return the password. again if you need to learn more man base64 or base64 --help to see options and information on this command.
cat 
> ### Key : 6zPeziLdR2RKNdNYFNb6nVCKzphlXHBM


## [Bandit Level 11 -> 12](https://overthewire.org/wargames/bandit/bandit12.html)

```
ssh bandit11@bandit.labs.overthewire.org -p 2220
ls
cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
logout
```
The sets 'A-Za-z' and 'N-ZA-Mn-za-m' are used for character translation in the tr command. They define the mapping of characters from the input to the output. Let's break down what these sets mean:

The Input Set: 'A-Za-z'
A-Z: This represents all uppercase alphabets from A to Z.
a-z: This represents all lowercase alphabets from a to z.
Together, A-Za-z represents all alphabets, both uppercase and lowercase. The tr command will look for these characters in the input.

The Output Set: 'N-ZA-Mn-za-m'
N-Z: This represents all uppercase alphabets from N to Z.
A-M: This represents all uppercase alphabets from A to M.
n-z: This represents all lowercase alphabets from n to z.
a-m: This represents all lowercase alphabets from a to m.
Notice that N-ZA-M is just A-Z rearranged, and n-za-m is a-z rearranged. This is the essence of the ROT13 cipher, which shifts each letter 13 positions down the alphabet.

> ### Key : JVNBBFSmZwKKOP0XbFXOoW8chDz5yVRv


## [Bandit Level 12 -> 13](https://overthewire.org/wargames/bandit/bandit13.html)

```
ssh bandit12@bandit.labs.overthewire.org -p 2220
ls
file data.txt
mkdir /tmp/[your_name]
cp data.txt /tmp/[your_name]/data.txt
cd /tmp/amrit
xxd -r data.txt | mv new
mv new new.gz
gzip -d new.gz
file new
bzip2 -d new
file new.out
mv new.out new.gz
gzip -d new.gz
file new
mv new new.tar
tar xvf new.tar
file data5.bin
tar xvf data5.bin
file data6.bin
mv data6.bin data6.bz2
bzip2 -d data6.bz2
tar xvf data6
file data8.bin
mv data8.bin data8.gz
file data8
cat data8
logout
```

> ### Key : wbWdlBxEir4CaE8LaPhauuOo6pwRmrDw


## [Bandit Level 13 -> 14](https://overthewire.org/wargames/bandit/bandit14.html)

```
ssh bandit13@bandit.labs.overthewire.org -p 2220
ls
ssh -i sshkey.private bandit14@bandit.labs.overthewire.org
cat /etc/bandit_pass/bandit14
logout
```

> ### Key : fGrHPx402xGC7U7rXKDaxiWFTOiF0ENq


## [Bandit Level 14 -> 15](https://overthewire.org/wargames/bandit/bandit15.html)

```
ssh bandit14@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit14 | nc localhost 30000
logout
```

> ### Key : jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt


## [Bandit Level 15 -> 16](https://overthewire.org/wargames/bandit/bandit16.html)

```
ssh bandit15@bandit.labs.overthewire.org -p 2220
openssl s_client -connect localhost:30001
jN2kgmIXJ6fShzhT2avhotn4Zcka6tnt
logout
```

> ### Key : JQttfApK4SeyHwDlI9SXGR50qclOAil1


## [Bandit Level 16 -> 17](https://overthewire.org/wargames/bandit/bandit17.html)

```
ssh bandit16@bandit.labs.overthewire.org -p 2220
nmap -v -p 31000-32000 localhost
openssl s_client localhost:31790
JQttfApK4SeyHwDlI9SXGR50qclOAil1
logout
```

Copied the output manually to /Documents/rsa_key

> ### Key : _ Check level)17_rsa_key _


## [Bandit Level 17 -> 18](https://overthewire.org/wargames/bandit/bandit18.html)

```
sudo chmod 600 ~/Documents/rsa_key
ssh -i ~/Documents/rsa_key bandit17@bandit.labs.overthewire.org -p 2220
diff -a passwords.old passwords.new
logout
```

> ### Key : hga5tuuCLF6fFzUpnagiMN8ssu9LFrdg

## [Bandit Level 18 -> 19](https://overthewire.org/wargames/bandit/bandit19.html)

```
ssh bandit18@bandit.labs.overthewire.org -p 2220 cat readme
```

> ### Key : awhqfNnAbc1naukrpqDYcF95h7HoMTrC


## [Bandit Level 19 -> 20](https://overthewire.org/wargames/bandit/bandit20.html)

```
ssh bandit19@bandit.labs.overthewire.org -p 2220
ls
./bandit20-do cat /etc/bandit_pass/bandit20
logout
```

> ### Key : VxCazJaVykI6W36BkBU0mJTCM8rR95XT


## [Bandit Level 20 -> 21](https://overthewire.org/wargames/bandit/bandit21.html)

```
ssh bandit20@bandit.labs.overthewire.org -p 2220
tmux
nc -Nl localhost 32001 < /etc/bandit_pass/bandit20
Ctrl+b "
./suconnect 32001
logout
```

> ### Key : NvEJF7oVjkddltPSrdKEFOllh9V1IBcq


## [Bandit Level 21 -> 22](https://overthewire.org/wargames/bandit/bandit22.html)

```
ssh bandit21@bandit.labs.overthewire.org -p 2220
cd /etc/cron.d
ls
cat cronjob_bandit22
cat /usr/bin/cronjob_bandit22.sh
cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
logout
```

> ### Key : WdDozAdTM2z9DiFEQ2mGlwngMfj4EZff


## [Bandit Level 22 -> 23](https://overthewire.org/wargames/bandit/bandit23.html)

```
ssh bandit22@bandit.labs.overthewire.org -p 2220
cat /etc/cron.d/cronjob_bandit23
cat /usr/bin/cronjob_bandit23.sh
myname=bandit23
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)
cat /tmp/$mytarget
logout
```

> ### Key : QYw0Y2aiA672PsMmh9puTQuhoz8SyR2G


## [Bandit Level 23 -> 24](https://overthewire.org/wargames/bandit/bandit24.html)

```
ssh bandit23@bandit.labs.overthewire.org -p 2220
cat /usr/bin/cronjob_bandit24.sh
logout
```

> ### Key : 
