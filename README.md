# OVER_THE_WIRE_BANDIT

## LEVEL 0

Objective

Connect to the Bandit server using SSH.

Commands Used

ssh bandit0@bandit.labs.overthewire.org -p 2220

Explanation

SSH (Secure Shell) is used to securely access a remote machine.
The -p 2220 specifies the port number since Bandit does not use the default SSH port (22).

Outcome

Successfully logged into the server.

## LEVEL 0 --> LEVEL 1

Objective

Read the password stored inside a file named readme.

Commands Used

ls
cat readme

Explanation

ls lists all files in the directory.

cat prints the content of the file to the terminal.

Outcome

ZjLjTmM6FvvyRnrb2rfNWOZOTa6ip5If

## LEVEL 1 --> LEVEL 2

Objective

Read a file whose name begins with a hyphen (-).

Commands Used

ls

cat ./-

Explanation

Files beginning with - are treated as command options.

Using ./ tells Linux to treat it as a file path instead.

Outcome

263JGJPfgU6LtdEvgfWU1XP5yac29mFx

## LEVEL 2 --> LEVEL 3

Objective

Read a file containing spaces in its name.

Commands Used

ls

cat ./--spaces\ in\ this\ filename--

Explanation

Spaces must be escaped using \ or enclosed inside quotes.

Outcome

MNk8KNH3Usiio41PRUEoDFPqfxLPlSmx

## LEVEL 3 --> LEVEL 4

Objective

Find a hidden file inside a directory.

Commands Used

cd inhere

ls -la

cat .hidden

Explanation
Hidden files begin with a dot (.).
ls -la shows all files including hidden ones.

Outcome

2WmrDFRmJIq3IPxneAaMGhap0pFhF3NJ

## LEVEL 4 --> LEVEL 5

Objective

Find the only human-readable file.

Commands Used

file ./*

cat ./-file07

Explanation

file identifies file types; only one is ASCII text.

Outcome

4oQYVPkxZOOEOO5pTW81FB8j8lxXGUQw

## LEVEL 5 --> LEVEL 6

Objective

Locate a file that is:

Human readable

Exactly 1033 bytes

Not executable

Commands Used

find . -type f -size 1033c -readable ! -executable
cat ./maybehere07/.file2

Explanation

find filters files using size, permission, and type parameters.

Outcome

HWasnPhtq9AVKe0dmk45nxy20cvUa6EG

## LEVEL 6 --> LEVEL 7

Objective

Find a file owned by a specific user and group.

Commands Used

find / -type f -user bandit7 -group bandit6 -size 33c 2>/dev/null
cat /var/lib/dpkg/info/bandit7.password

Explanation

Ownership-based search helps locate protected files.

Outcome

morbNTDkSW6jIlUc0ymOdMaLnOlFVAaj

## LEVEL 7 --> LEVEL 8

Objective

Extract the line containing the word millionth.

Commands Used

grep millionth data.txt

Explanation

grep searches for patterns inside files.

Outcome

dfwvzFQi4mU0wfNbFOe9RoWskMLg7eEc

## LEVEL 8 --> LEVEL 9

Objective

Find the only unique line.

Commands Used

sort data.txt | uniq -u

Explanation

sort organizes lines; uniq -u shows lines appearing only once.

Outcome

4CKMh1JI91bUIZZPXDqGanal4xvAg0JM

## LEVEL 9 --> LEVEL 10

Objective

Extract readable strings from a binary file.

Commands Used

strings data.txt | grep =

Explanation

strings extracts readable ASCII sequences from binary files.

Outcome

FGUW5ilLVJrxX9kMYMmlN4MgbpfMiqey

## LEVEL 10 --> LEVEL 11

Objective

Decode Base64 encoded content.

Commands Used

base64 -d data.txt

Explanation

Base64 encoding converts binary data to readable text.

Outcome

dtR173fZKb0RRsDFSGsg2RWnpNVj3qRr

## LEVEL 11 --> LEVEL 12

Objective

Decode ROT13 encrypted text.

Commands Used

cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'

Explanation

ROT13 shifts each letter by 13 positions.

Outcome

7x16WNeHIi5YkIhWsfFIqoognUTyj9Q4

## LEVEL 12 --> LEVEL 13

Objective

Extract repeatedly compressed files.

Commands Used

xxd -r data.txt > file
file file
gunzip / bunzip2 / tar -xf

Explanation

File is repeatedly compressed using different formats; identify and extract step-by-step.

Outcome

FO5dwFsc0cbaIiH0h8J2eUks2vdTDwAn

## LEVEL 13 --> LEVEL 14

Objective

Login using a private SSH key.

Commands Used

ssh -i sshkey.private bandit14@bandit.labs.overthewire.org -p 2220
cat /etc/bandit_pass/bandit14

Outcome

MU4VWeTyJk8ROof1qqmcBPaLh7lDCPvS

## LEVEL 14 --> LEVEL 15

Objective

Send password through a TCP service.

Commands Used

telnet localhost 30000

Outcome

8xCjnmgoKbGLhHFAZlGE5Tmu4M2tKJQo

## LEVEL 15 --> LEVEL 16

Objective

Use SSL to securely send password.

Commands Used

openssl s_client -connect localhost:30001 -ign_eof

Outcome

kSkvUpMQ7lBYyCM4GBPvCvT1BfWRy0Dx

## LEVEL 16 --> LEVEL 17

Objective

Scan ports and identify correct SSL service.

Commands Used

nmap -p 31000-32000 localhost
openssl s_client -connect localhost:31790

Outcome

Private key obtained. 

## LEVEL 17 --> LEVEL 18

Objective

Compare two files to find modified content.

Commands Used

diff passwords.old passwords.new

Outcome

x2gLTTjFwMOhQ8oWNbMN362QKxfRqGlO

## LEVEL 18 --> LEVEL 19

Objective

Bypass forced logout.

Commands Used

ssh -T bandit18@bandit.labs.overthewire.org
cat readme

Outcome

cGWpMaKXVwDUNgPAVJbWYuGHVn9zl3j8

## LEVEL 19 --> LEVEL 20

Objective

Use SUID program to read restricted file.

Commands Used

./bandit20-do cat /etc/bandit_pass/bandit20

Outcome

0qXahG8ZjOVMN9Ghs7iOWsCfZyXOUbYO

## LEVEL 20 --> LEVEL 21

Objective

Send password using network socket.

Commands Used

nc -lvnp 12345
./suconnect 12345

Outcome

EeoULMCra2q0dSkYj561DX7s1CpBuOBt

## LEVEL 21 --> LEVEL 22

Objective

Read cron-generated password file.

Commands Used

cat /etc/cron.d/cronjob_bandit22
cat /tmp/<generated_file>

Outcome

tRae0UfB9v0UzbCdn9cY0gQnds9GF58Q

## LEVEL 22 --> LEVEL 23

Objective

Understand cron job logic and extract password.

Commands Used

cat /usr/bin/cronjob_bandit23.sh

Outcome

OZf11i0IjMVN551jX3CmStKLYqjk54Ga

## LEVEL 23 --> LEVEL 24

Objective

Exploit writable cron directory.

Commands Used

echo "cat /etc/bandit_pass/bandit24 > /tmp/pass" > script.sh
chmod 777 script.sh

Outcome

gb8KRRCsshuZXI0tUuR6ypOFjiZbf3G8

## LEVEL 24 --> LEVEL 25

Objective

Brute-force a 4-digit PIN.

Commands Used

for i in {0000..9999}; do echo "password $i"; done | nc localhost 30002

Outcome

iCi86ttT4KSNe1armKiwbQNmB3YJP3q4

## LEVEL 25 --> LEVEL 26

Objective

Escape restricted shell.

Commands Used

ssh -i bandit26.sshkey bandit26@localhost
:set shell=/bin/bash

Outcome

s0773xxkk0MXfdqOfPRVr9L3jJBUOgCZ

## LEVEL 26 --> LEVEL 27

Objective

Run privileged binary.

Commands Used

./bandit27-do cat /etc/bandit_pass/bandit27

Outcome

upsNCc7vzaRDx6oZC6GiR6ERwe1MowGB

## LEVEL 27 --> LEVEL 28

Objective

Read password from Git repository.

Commands Used

git clone ssh://bandit27-git@bandit.labs.overthewire.org/home/bandit27-git/repo
cat README

Outcome

Yz9IpL0sBcCeuG7m9uQFt8ZNpS4HZRcN

## LEVEL 28 --> LEVEL 29

Objective

View Git history to locate password.

Commands Used

git log
git checkout <commit>

Outcome

4pT1t5DENaYuqnqvadYs1oE4QLCdjmJ7

## LEVEL 29 --> LEVEL 30

Objective

Switch Git branch to reveal secret.

Commands Used

git checkout dev

Outcome

qp30ex3VLz5MDG1n91YowTv4Q8l7CDZL

## LEVEL 30 --> LEVEL 31

Objective

Read hidden Git tag.

Commands Used

git tag
git show secret

Outcome

OoffzGDlzhAlerFJ2cAiz1D41JW1Mhmt

## LEVEL 31 --> LEVEL 32

Objective

Push a required file to repository.

Commands Used

echo "May I come in?" > key.txt
git add key.txt
git commit -m "add key"
git push

Outcome

rmCBvG56y58BXzv98yZGd07ATVL5dW8y

## LEVEL 32 --> LEVEL 33

Objective

Escape uppercase-only shell.

Commands Used

$0
cat /etc/bandit_pass/bandit33

Outcome

odHo63fHiFqcWWJG9rLiLDtPm45KzUKy
## LEVEL 33 --> LEVEL 34

Objective

Complete the Bandit wargame.

Outcome

All available Bandit levels successfully completed.
Level 34 does not exist.
