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
    echo "Sorry, the object does not exist"
fi
EOF

chmod 755 ifnested.sh
./ifnested.sh
```

### 8.4 Numeric comparisons

```bash
cat > iftest.sh << 'EOF'
#!/bin/bash
val1=10
val2=11

if [ $val1 -gt 5 ]
then
    echo "The test value $val1 is greater than 5"
fi

if [ $val1 -eq $val2 ]
then
    echo "The values are equal"
else
    echo "The values are different"
fi
EOF

chmod 755 iftest.sh
./iftest.sh
```

### 8.5 elif condition

```bash
cat > elifcheck.sh << 'EOF'
#!/bin/bash
if [ "$USER" = "Messi" ]
then
    echo "Welcome $USER"
    echo "Please enjoy your visit"
elif [ "$USER" = "Mano" ]
then
    echo "Welcome $USER"
    echo "Please enjoy your visit"
elif [ "$USER" = "Dhoni" ]
then
    echo "Special testing account"
elif [ "$USER" = "Ronaldo" ]
then
    echo "$USER, Do not forget to logout"
else
    echo "Sorry, you are not allowed here"
fi
EOF

chmod 755 elifcheck.sh
./elifcheck.sh
```

### 8.6 Compound comparison

```bash
cat > ifcompound.sh << 'EOF'
#!/bin/bash
if [ -d "$HOME" ] && [ -w "$HOME" ]
then
    echo "The directory exists and you can write to it"
else
    echo "I cannot write to the directory"
fi
EOF

chmod 755 ifcompound.sh
./ifcompound.sh
```

### 8.7 Case statement

```bash
cat > casecheck.sh << 'EOF'
#!/bin/bash
case $USER in
    Messi | Mano)
        echo "Welcome, $USER"
        echo "Please enjoy your visit";;
    Dhoni)
        echo "Special testing account";;
    Ronaldo)
        echo "$USER, Do not forget to log off";;
    *)
        echo "Sorry, you are not allowed here";;
esac
EOF

chmod 755 casecheck.sh
./casecheck.sh
```

### OUTPUT – SECTION 8

<img width="948" height="1012" alt="image" src="https://github.com/user-attachments/assets/bfe85fa9-be87-4172-ae29-249b9bbf7d29" />
<img width="956" height="1012" alt="image" src="https://github.com/user-attachments/assets/a5986389-d389-43ac-be7c-327284399cb3" />
<img width="913" height="967" alt="image" src="https://github.com/user-attachments/assets/507a880f-c404-4ec3-8f80-96dbf06ffc52" />




---

## 9. LOOPING STATEMENTS

### 9.1 While loop

```bash
cat > whiletest.sh << 'EOF'
#!/bin/bash
var1=10
while [ $var1 -gt 0 ]
do
    echo $var1
    var1=$((var1 - 1))
done
EOF

chmod 755 whiletest.sh
./whiletest.sh
```

### 9.2 Until loop

```bash
cat > untiltest.sh << 'EOF'
#!/bin/bash
var1=100
until [ $var1 -eq 0 ]
do
    echo $var1
    var1=$((var1 - 25))
done
EOF

chmod 755 untiltest.sh
./untiltest.sh
```

### 9.3 Basic for loop – places

```bash
cat > forin1.sh << 'EOF'
#!/bin/bash
for place in Chennai Mumbai Barcelona Madrid Delhi Hyderabad
do
    echo "The next place is $place"
done
EOF

chmod 755 forin1.sh
./forin1.sh
```

### 9.4 For loop with words

```bash
cat > forin2.sh << 'EOF'
#!/bin/bash
for word in Messi Mano Dhoni "don't stop" "keep moving"
do
    echo "Word: $word"
done
EOF

chmod 755 forin2.sh
./forin2.sh
```

### 9.5 For loop with apostrophes

```bash
cat > forin3.sh << 'EOF'
#!/bin/bash
for word in I don\'t know if "this'll" work
do
    echo "Word: $word"
done
EOF

chmod 755 forin3.sh
./forin3.sh
```

### 9.6 Read values from a file

```bash
cat > cities << 'EOF'
Chennai
Mumbai
Barcelona
Madrid
Delhi
Hyderabad
Coimbatore
EOF

cat > forinfile.sh << 'EOF'
#!/bin/bash
file="cities"
while IFS= read -r place
do
    echo "Visit beautiful $place"
done < "$file"
EOF

chmod 755 forinfile.sh
./forinfile.sh
```

### 9.7 C-style for loop

```bash
cat > forctype.sh << 'EOF'
#!/bin/bash
for (( i=1; i<=5; i++ ))
do
    echo "The value of i is $i"
done
EOF

chmod 755 forctype.sh
./forctype.sh
```

### 9.8 Multiple variables

```bash
cat > forctype1.sh << 'EOF'
#!/bin/bash
for (( a=1, b=5; a<=5; a++, b-- ))
do
    echo "$a - $b"
done
EOF

chmod 755 forctype1.sh
./forctype1.sh
```

### 9.9 Nested for loop

```bash
cat > fornested1.sh << 'EOF'
#!/bin/bash
for (( a=1; a<=3; a++ ))
do
    echo "Starting loop $a:"
    for (( b=1; b<=3; b++ ))
    do
        echo "Inside loop: $b"
    done
done
EOF

chmod 755 fornested1.sh
./fornested1.sh
```

### 9.10 Break statement

```bash
cat > forbreak.sh << 'EOF'
#!/bin/bash
for var1 in 1 2 3 4 5
do
    if [ $var1 -eq 3 ]
    then
        break
    fi
    echo "Iteration number: $var1"
done
echo "The for loop is completed"
EOF

chmod 755 forbreak.sh
./forbreak.sh
```

### 9.11 Continue statement

```bash
cat > forcontinue.sh << 'EOF'
#!/bin/bash
for var1 in 1 2 3 4 5
do
    if [ $var1 -eq 3 ]
    then
        continue
    fi
    echo "Iteration number: $var1"
done
echo "The for loop is completed"
EOF

chmod 755 forcontinue.sh
./forcontinue.sh
```

### OUTPUT – SECTION 9

<img width="935" height="1003" alt="image" src="https://github.com/user-attachments/assets/835c028f-bdd2-446e-a3e3-cf83ccd2782d" />
<img width="917" height="1005" alt="image" src="https://github.com/user-attachments/assets/767a7115-7229-4e9d-a609-4f3a01257b81" />
<img width="920" height="992" alt="image" src="https://github.com/user-attachments/assets/84cd312d-f609-4d3e-94ff-03f34e11b550" />
<img width="950" height="1010" alt="image" src="https://github.com/user-attachments/assets/1061d7e3-8153-4074-a232-69af603c4fe1" />
<img width="695" height="526" alt="image" src="https://github.com/user-attachments/assets/c92764ef-5573-4c94-81c1-9fca55059777" />





---

## 10. READ COMMAND, FUNCTIONS AND ARGUMENTS

### 10.1 Read command

```bash
cat > exread.sh << 'EOF'
#!/bin/bash
echo -n "Enter your name: "
read name
echo "Hello $name, welcome to my program."
EOF

chmod 755 exread.sh
./exread.sh
```

### 10.2 Read command with prompt

```bash
cat > exread1.sh << 'EOF'
#!/bin/bash
read -p "Enter your name: " name
echo "Hello $name, welcome to my program."
EOF

chmod 755 exread1.sh
./exread1.sh
```

### 10.3 Function with two arguments

```bash
cat > funcex.sh << 'EOF'
#!/bin/bash
function func {
    echo $(( $1 * $2 ))
}

if [ $# -eq 2 ]
then
    value=$(func "$1" "$2")
    echo "The result is $value"
else
    echo "Usage: ./funcex.sh number1 number2"
fi
EOF

chmod 755 funcex.sh
./funcex.sh 5 10
```

### 10.4 Shift command

```bash
cat > argshift.sh << 'EOF'
#!/bin/bash
while (( "$#" ))
do
    echo "$1"
    shift
done
EOF

chmod 755 argshift.sh
./argshift.sh Messi Mano Dhoni
```

### 10.5 Store arguments in an array

```bash
cat > argshift1.sh << 'EOF'
#!/bin/bash
args=("$@")
ELEMENTS=${#args[@]}

for (( i=0; i<ELEMENTS; i++ ))
do
    echo "${args[$i]}"
done
EOF

chmod 755 argshift1.sh
./argshift1.sh Messi Mano Dhoni
```

### 10.6 Debugging with set -x

```bash
cat > argshift2.sh << 'EOF'
#!/bin/bash
set -x
while (( "$#" ))
do
    echo "$1"
    shift
done
set +x
EOF

chmod 755 argshift2.sh
./argshift2.sh Messi Mano Dhoni
```
### OUTPUT – SECTION 10
<img width="945" height="997" alt="image" src="https://github.com/user-attachments/assets/1e195f5e-d138-4663-9d6f-6e109cc90b20" />
<img width="943" height="671" alt="image" src="https://github.com/user-attachments/assets/9f26ee94-cdcb-4df2-bb94-af357705bf54" />


---

## 11. AWK PROGRAMMING AND PALINDROME

### 11.1 AWK – count characters, lines and words

```bash
cat > nc.awk << 'EOF'
BEGIN {}
{
    len=length($0)
    print len, "\t", $0
    wordcount+=NF
    chrcnt+=len
}
END {
    print "Total characters:", chrcnt
    print "Number of lines:", NR
    print "Number of words:", wordcount
}
EOF

cat > data.dat << 'EOF'
Messi
Mano
Dhoni
Barcelona
Chennai
Mumbai
Football
Cricket
EOF

awk -f nc.awk data.dat
```

### 11.2 Palindrome number

```bash
cat > palindrome.sh << 'EOF'
#!/bin/bash
echo "Enter the number:"
read num

s=0
rev=""
temp=$num

while [ $num -gt 0 ]
do
    s=$((num % 10))
    num=$((num / 10))
    rev="${rev}${s}"
done

if [ "$temp" -eq "$rev" ]
then
    echo "Number is palindrome"
else
    echo "Number is NOT palindrome"
fi
EOF

chmod 755 palindrome.sh
./palindrome.sh
```

### OUTPUT – SECTION 11
<img width="917" height="793" alt="image" src="https://github.com/user-attachments/assets/a015d86d-9148-496f-ae64-15c95e153794" />

<img width="916" height="782" alt="image" src="https://github.com/user-attachments/assets/683e35f7-8ce2-4880-82fb-5174c4defd04" />


---

## 12. FINAL VERIFICATION

```bash
pwd
ls
ls *.sh
ls -l *.sh
find . -maxdepth 1 -type f | wc -l
```

### OUTPUT – SECTION 12

<img width="878" height="792" alt="image" src="https://github.com/user-attachments/assets/c8b2ae7d-f295-449d-8fed-743190951687" />


---

## RESULT

Thus, various Linux commands, file comparison commands, filters, sorting commands, backup commands, AWK programming and Shell Scripting concepts were practiced and executed successfully using Ubuntu Linux on WSL2.
