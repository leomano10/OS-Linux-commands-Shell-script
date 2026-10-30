# EXPERIMENT 1 – PRACTICE LINUX COMMANDS AND SHELL SCRIPTING

**Name:** MANORAJAPRIYAN.L.E  
**Register Number:** 212225040227  
**Environment:** Ubuntu 26.04 LTS on WSL2

## AIM
To practice Linux commands and Shell Scripting.

## SOFTWARE REQUIRED
- Windows operating system
- Ubuntu Linux through WSL2
- Terminal

## 1. FILE CREATION AND COMPARISON

### 1.1 Create `file1` and `file2`

```bash
cat > file1 << 'EOF'
chanchal singhvi
Messi
Mano
Dhoni
Barcelona
Chennai
EOF

cat > file2 << 'EOF'
Messi
Dhoni
Mano
Mumbai
Chennai
EOF

cat file1
cat file2
```

### 1.2 Compare files using `cmp`, `comm` and `diff`

```bash
cmp file1 file2

sort file1 -o file1
sort file2 -o file2
comm file1 file2

diff file1 file2
```

### OUTPUT – SECTION 1

<img width="683" height="868" alt="image" src="https://github.com/user-attachments/assets/9fe4ea58-519a-41d2-ad34-c2dd9f795ad6" />


![Section 1 Output](images/exp1-output-1.png)

---

## 2. FILTER COMMANDS

### 2.1 Create files and use `cut`

```bash
cat > file11 << 'EOF'
Hello Messi
This is my world
Mano is my friend
Dhoni is a legend
EOF

cat > file22 << 'EOF'
1001 | Messi | 10000 | Football
1002 | Mano | 5000 | CSE
1003 | Dhoni | 7000 | Cricket
EOF

cut -c1-3 file11
cut -d '|' -f 1 file22
cut -d '|' -f 2 file22
```

### 2.2 Create `newfile` and use `grep`

```bash
cat > newfile << 'EOF'
Hello world
hello world
Linux is world number 1
Unix is predecessor
Linux is best in this World
Messi loves football
Mano supports Messi
Dhoni is a legend
EOF

cat newfile
grep Hello newfile
grep hello newfile
grep -v hello newfile
cat newfile | grep -i "hello"
cat newfile | grep -i -c "hello"
grep -R ubuntu /etc 2>/dev/null
grep -w -n world newfile
```

### OUTPUT – SECTION 2

<img width="951" height="987" alt="image" src="https://github.com/user-attachments/assets/3e5c7822-9ad3-4146-9ac6-92167161876f" />

<img width="942" height="945" alt="image" src="https://github.com/user-attachments/assets/388a059e-11cd-4556-9011-087a684587df" />





![Section 2 Output](images/exp1-output-2.png)

---

## 3. EXTENDED GREP (EGREP)

```bash
egrep -w 'Hello|hello' newfile
egrep -w '(H|h)ello' newfile
egrep -w '(H|h)ell[a-z]' newfile
egrep '(^hello)' newfile
egrep '(world$)' newfile
egrep '(World$)' newfile
egrep '((W|w)orld$)' newfile
egrep '[1-9]' newfile
egrep 'Linux.*world' newfile
egrep 'Linux.*World' newfile
egrep 'l{2}' newfile
egrep 's{1,2}' newfile
```

### OUTPUT – SECTION 3

<img width="938" height="835" alt="image" src="https://github.com/user-attachments/assets/c4a9b8fc-6150-457a-b39b-1aae2ec745d7" />


![Section 3 Output](images/exp1-output-3.png)

---

## 4. SED – STREAM EDITOR

### 4.1 Create `file23` and perform SED operations

```bash
cat > file23 << 'EOF'
1001 | Messi | 10000 | Football
1001 | Messi | 10000 | Football
1002 | Mano | 5000 | CSE
1003 | Dhoni | 7000 | Cricket
1005 | Ronaldo | 5000 | Football
1004 | Kohli | 7000 | Cricket
1003 | Dhoni | 7000 | Cricket
1001 | Messi | 10000 | Football
EOF

sed -n -e '3p' file23
sed -n -e '$p' file23
sed -e 's/Messi/Sita/' file23
sed -e '2s/Messi/Dhoni/' file23
sed '/Mano/s/5000/6000/' file23
sed -n -e '1,5p' file23
sed -n -e '2,/Dhoni/p' file23
sed -n -e '/Mano/,/Dhoni/p' file23
```

### 4.2 SED with `seq`

```bash
seq 10
seq 10 | sed -n '4,6p'
seq 10 | sed -n '2,~4p'
seq 3 | sed '2a hello'
seq 2 | sed '2i hello'
seq 10 | sed '2,9c hello'
sed -n '2,4{s/^/$/;p}' file23
sed -n '2,4{s/$/*/;p}' file23
```

### OUTPUT – SECTION 4

<img width="945" height="976" alt="image" src="https://github.com/user-attachments/assets/e31d2e93-1295-48c3-b9c9-00529ee1afe4" />

<img width="565" height="597" alt="image" src="https://github.com/user-attachments/assets/9e5e9790-ce3a-4037-be3b-5f5e257106aa" />



![Section 4 Output](images/exp1-output-4.png)

---

## 5. SORTING AND TR COMMANDS

### 5.1 Sorting and removing duplicate lines

```bash
cat > file21 << 'EOF'
1001 | Messi | 10000 | Football
1002 | Mano | 5000 | CSE
1003 | Dhoni | 7000 | Cricket
1005 | Ronaldo | 5000 | Football
1004 | Kohli | 7000 | Cricket
EOF

sort file21

cat > file22 << 'EOF'
1001 | Messi | 10000 | Football
1001 | Messi | 10000 | Football
1002 | Mano | 5000 | CSE
1003 | Dhoni | 7000 | Cricket
1005 | Ronaldo | 5000 | Football
1004 | Kohli | 7000 | Cricket
EOF

uniq file22
```

### 5.2 Translate and delete characters using `tr`

```bash
cat file23 | tr '[:lower:]' '[:upper:]'

cat > urllist.txt << 'EOF'
www. chennai. com
www. barcelona. com
www. madrid.... com
EOF

cat urllist.txt
cat urllist.txt | tr -d ' '
cat urllist.txt | tr -d ' ' | tr -s '.'
```

### OUTPUT – SECTION 5

<img width="900" height="972" alt="image" src="https://github.com/user-attachments/assets/6f7f376c-56d4-487b-9b92-f02387d94ca0" />


![Section 5 Output](images/exp1-output-5.png)

---

## 6. BACKUP COMMANDS

```bash
# Run this once from the EXP1 directory
tar -cvf backup.tar *

mkdir -p backupdir
mv backup.tar backupdir/

tar -tvf backupdir/backup.tar

mkdir -p restore
tar -xvf backupdir/backup.tar -C restore

gzip backupdir/backup.tar
gunzip backupdir/backup.tar.gz

ls -l backupdir
```

### OUTPUT – SECTION 6

<img width="916" height="930" alt="image" src="https://github.com/user-attachments/assets/48b258d4-3396-4057-b937-a4b5280b599a" />


![Section 6 Output](images/exp1-output-6.png)

---

## 7. BASIC SHELL SCRIPTING

### 7.1 Hello World script

```bash
cat > my-script.sh << 'EOF'
#!/bin/bash
echo "Hello World"
echo "Messi Mano Dhoni"
exit 0
EOF

chmod 755 my-script.sh
./my-script.sh
```

### 7.2 Here document

```bash
cat << 'stop' > herecheck.txt
hello in this world
Messi never stops
Mano keeps learning
Dhoni is a cricket legend
stop

cat herecheck.txt
```

### 7.3 Script arguments

```bash
cat > scriptest.sh << 'EOF'
#!/bin/bash
echo "File name is $0"
echo "File name is $(basename "$0")"
echo "First argument is $1"
echo "Second argument is $2"
echo "Third argument is $3"
echo "Fourth argument is $4"
echo 'The $@ is' "$@"
echo 'The $# is' "$#"
echo 'The $$ is' "$$"
ps
EOF

chmod 777 scriptest.sh
./scriptest.sh Messi Mano Dhoni Chennai
```

### 7.4 Check exit status

```bash
ls file1
echo $?

abcd
echo $?
```

### OUTPUT – SECTION 7

<img width="917" height="963" alt="image" src="https://github.com/user-attachments/assets/ec404bef-50c5-467c-9f52-214e908d92ef" />


![Section 7 Output](images/exp1-output-7.png)

---

## 8. CONDITIONAL STATEMENTS

### 8.1 String comparison

```bash
cat > strcomp.sh << 'EOF'
#!/bin/bash
val1=Messi
val2=Dhoni

if [[ $val1 > $val2 ]]
then
    echo "$val1 is greater than $val2"
else
    echo "$val1 is less than or equal to $val2"
fi
EOF

chmod 755 strcomp.sh
./strcomp.sh
```

### 8.2 Check file ownership

```bash
cat > psswdperm.sh << 'EOF'
#!/bin/bash
if [ -O /etc/passwd ]
then
    echo "You are the owner of the /etc/passwd file"
else
    echo "Sorry, you are not the owner of the /etc/passwd file"
fi
EOF

chmod 755 psswdperm.sh
./psswdperm.sh
```

### 8.3 Nested if statement

```bash
cat > ifnested.sh << 'EOF'
#!/bin/bash
if [ -e "$HOME" ]
then
    echo "$HOME The object exists, is it a file?"
    if [ -f "$HOME" ]
    then
        echo "Yes, $HOME it is a file!"
    else
        echo "No, $HOME it is not a file!"
        if [ -f "$HOME/.bash_history" ]
        then
            echo "But $HOME/.bash_history is a file!"
        fi
    fi
else
    echo "Sorry, the object
