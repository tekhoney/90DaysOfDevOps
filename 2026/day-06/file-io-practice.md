# Day 06 – Linux Fundamentals: Read and Write Text Files

i have tried commands for read and write in the text file

*** System restart required ***

Last login: Sat Mar  7 07:19:54 2026 from 49.36.187.56

ubuntu@ip-172-31-1-38:~$ touch notes.txt

ubuntu@ip-172-31-1-38:~$ cat "this is my first file" > notes.txt 

cat: 'this is my first file': No such file or directory

ubuntu@ip-172-31-1-38:~$ echo "this is my first file" > notes.txt 

ubuntu@ip-172-31-1-38:~$ cat notes.txt 

this is my first file

ubuntu@ip-172-31-1-38:~$ echo "this is my second line in first file" >> notes.txt 

ubuntu@ip-172-31-1-38:~$ echo "this is my third line after second line in first file" >> notes.txt 

ubuntu@ip-172-31-1-38:~$ cat notes.txt 

this is my first file

this is my second line in first file

this is my third line after second line in first file

ubuntu@ip-172-31-1-38:~$ head -2 notes.txt 

this is my first file

this is my second line in first file

ubuntu@ip-172-31-1-38:~$ tail -2 notes.txt 

this is my second line in first file

this is my third line after second line in first file

ubuntu@ip-172-31-1-38:~$ echo "this is my fourth line after second line in first file" | tee -a  notes.txt 

this is my fourth line after second line in first file

ubuntu@ip-172-31-1-38:~$ cat notes.txt 

this is my first file

this is my second line in first file

this is my third line after second line in first file

this is my fourth line after second line in first file

1-1-38:~$ 

