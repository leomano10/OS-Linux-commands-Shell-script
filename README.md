## 1. FILE CREATION AND COMPARISON

### 1.1 Create `file1` and `file2`

**Commands:**

```bash
cat > file1 << 'EOF'
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

### 1.2 Compare files using `cmp`, `diff` and `comm`

**Commands:**

```bash
cmp file1 file2
diff file1 file2

sort file1 -o file1
sort file2 -o file2
comm file1 file2
```

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![File Creation and Comparison Output](images/exp1-output-1.png)

---

## 2. FILTER COMMANDS

### 2.1 Create files and use `cut`

**Commands:**

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

### 2.2 Use `grep` commands

**Commands:**

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

### OUTPUT

<!-- Upload one complete terminal screenshot for this section -->

![Filter Commands Output](images/exp1-output-2.png)

---

## 3. EXTENDED GREP (EGREP)

**Commands:**

```bash
egrep -w 'Hello|hello' newfile
egrep -w '(H|h)ello' newfile
egrep -w '(H|h)ell[a-z]' newfile
egrep '(^hello)' newfile
egrep '(world$)' newfile
egrep '((W|w)orld$)' newfile
egrep '[1-9]' newfile
egrep 'Linux.*world' newfile
egrep 'l{2}' newfile
egrep 's{1,2}' newfile
```

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![EGREP Output](images/exp1-output-3.png)

---

## 4. SED – STREAM EDITOR

**Commands:**

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

seq 10
seq 10 | sed -n '4,6p'
seq 3 | sed '2a hello'
seq 2 | sed '2i hello'
seq 10 | sed '2,9c hello'
```

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![SED Output](images/exp1-output-4.png)

---

## 5. SORTING AND TR COMMANDS

**Commands:**

```bash
sort file21
uniq file22

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

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![Sorting and TR Output](images/exp1-output-5.png)

---

## 6. BACKUP COMMANDS

**Commands:**

```bash
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

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![Backup Commands Output](images/exp1-output-6.png)

---

## 7. BASIC SHELL SCRIPTING

**Commands:**

```bash
cat > my-script.sh << 'EOF'
#!/bin/bash
echo "Hello World"
echo "Messi Mano Dhoni"
exit 0
EOF

chmod 755 my-script.sh
./my-script.sh

cat << 'stop' > herecheck.txt
hello in this world
Messi never stops
Mano keeps learning
Dhoni is a cricket legend
stop

cat herecheck.txt
```

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![Shell Scripting Output](images/exp1-output-7.png)

---

## 8. CONDITIONAL STATEMENTS

**Commands:**

```bash
chmod 755 strcomp.sh psswdperm.sh ifnested.sh iftest.sh
chmod 755 elifcheck.sh ifcompound.sh casecheck.sh

./strcomp.sh
./psswdperm.sh
./ifnested.sh
./iftest.sh
./elifcheck.sh
./ifcompound.sh
./casecheck.sh
```

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![Conditional Statements Output](images/exp1-output-8.png)

---

## 9. LOOPING STATEMENTS

**Commands:**

```bash
chmod 755 whiletest.sh untiltest.sh
chmod 755 forin1.sh forin2.sh forin3.sh
chmod 755 forinfile.sh forctype.sh forctype1.sh
chmod 755 fornested1.sh forbreak.sh forcontinue.sh

./whiletest.sh
./untiltest.sh
./forin1.sh
./forin2.sh
./forin3.sh
./forinfile.sh
./forctype.sh
./forctype1.sh
./fornested1.sh
./forbreak.sh
./forcontinue.sh
```

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![Looping Statements Output](images/exp1-output-9.png)

---

## 10. READ COMMAND, FUNCTIONS AND ARGUMENTS

**Commands:**

```bash
chmod 755 exread.sh exread1.sh
chmod 755 funcex.sh argshift.sh
chmod 755 argshift1.sh argshift2.sh

./exread.sh
./exread1.sh
./funcex.sh 5 10
./argshift.sh Messi Mano Dhoni
./argshift1.sh Messi Mano Dhoni
./argshift2.sh Messi Mano Dhoni
```

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![Read and Functions Output](images/exp1-output-10.png)

---

## 11. AWK PROGRAMMING AND PALINDROME

**Commands:**

```bash
awk -f nc.awk data.dat

chmod 755 palindrome.sh
./palindrome.sh
```

### OUTPUT

<!-- Upload your complete terminal screenshot here -->

![AWK and Palindrome Output](images/exp1-output-11.png)

---

## RESULT

Thus, various Linux commands, file comparison commands, filters, sorting commands, backup commands, AWK programming and Shell Scripting concepts were practiced and executed successfully using Ubuntu Linux on WSL2.
