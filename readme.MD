# linux commands

* steps to login to Linux server

* ssh protocal is used to connect to the servers on port 22
* while authenticating user should send their username and private-key

* generate the public and private keys in our systesm using the following command:

```
ssh-keygen -f <file-name>
 ```

* go to aws console and import key and paste the public key generated and create a security group to allow user to login on port 22

```
ssh -i linux-key ec2-user@54.166.142.211
```


```
ls -ltr (list all the based on time stamp latest on reverese order)
```

**CRUD**

touch devops.txt --> to create a empty file
cat > devops.txt --> to write the content to a file
cat >> devops.txt --> it will append the data to exising content
cat devops.txt

to create directory: mkdir devops

to remove empty directory : rmdir devops

to remove non-empty directory : rm -r devops (will recursevely delete all the files inside the directory)

to move the files or rename the files : mv onee.txt one.txt  , mv one.txt ./aws/one.txt

uname -a

grep sbin users  --> its searches for a word sbin in users file
grep network users
grep -i network users ==> its searches for word network with case-in-sensitive 

**wget is used to download the files**
**curl is used to show the text directly on the terminal . curl is used to run the scripts**

wget https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt
cut -d "/" -f1 https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt
echo "https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt" | cut -d "/" f1
echo "https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt" | cut -d "/" -f1
echo "https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt" | cut -d "/" -f2
echo "https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt" | cut -d "/" -f3
echo "https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt" | cut -d "/" -f7
echo "https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt" | cut -d "/" -f8
echo "https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt" | awk -F "/" '{print $1F}'
echo "https://raw.githubusercontent.com/daws-81s/notes/refs/heads/main/session-02.txt" | awk -F "/" '{print $NF}'
awk -F ":"  '{print $1F}' users
awk -F ":"  '{print $1F}' users
cut -d ":" -f1 users
awk -F ":"  '{print }' users
awk -F ":"  '{print $1F,$3F}' users

head -7 users
head -10 users
tail -10 users
clear
head -n 7 users
head -n 7 users | tail -n 3 users
head -n 7 users | tail -n 3
tail -f log.json
cat users | head -n 7 | tail -n 3

Editor:
-
:q --> quit
:wq --> write and quit
:q! --> dont save the changes and exit
:set nu  --> show the numbers
:set nonu --> doesnt show the numbers

:/<word-to-find> --> search from the top
:?<word-to-find> --> search from the bottom

Pressing n (next) moves to the next occurrence of the word.
Pressing N (Shift + n) moves to the previous occurrence.

:noh --> no highlight
:1d ==> deletes first line
:5d ==> deletes 5th line
:%d ==> delete everything
:s/<which-word>/<replace-word> ==> replaces the where the cursor is and only first occurance
:s/<which-word>/<replace-word>/g ==> all occurances in that line
:3s/<which-word>/<replace-word>/g ==> all occurances in the 3rd line
:%s/<which-word>/<replace-word>/g ==> all occurances in the file

ESC Mode
===

u -> undo

shift + g ==> goes to bottom

gg ==> goes to top

yy --> copy

p --> paste

10p --> 10 times pasted

dd --> delete the line

Permissinons
-----------

-rw-r--r--

"-" ==> denotes it is a file

rw- ==> who is the owner of the file == u

r-- ==> which group he belongs to == g

r-- ==> others == o

chmod o+w 

chmod o+w session-02.txt

chmod u+x session-02.txt

chmod ugo+x session-02.txt

chmod o-w session-02.txt

chmod ugo+rwx session-02.txt

R ==>  4

W  --> 2

X  --> 1

chmod 750 session-02.txt ==> -rwxr-x---

