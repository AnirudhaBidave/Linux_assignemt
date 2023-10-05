# Linux_assignemt
## Que 1: Configure smtp in localhos.
Ans :<br>
1st step: First we have to install postfix in our linux machine. To install command is <br>
	```sudo apt install postfix```<br><br>
2nd step: After that the installation will start and the postfix window will open. And we have to select some options on that window as follows<br>
	1. select internet site and enter tab and enter enter.<br>
	2. enter custom mall like ex: host.example.com<br><br>
3rd step: After completion of installation we have to make changes in main.cf file present in path /etc/postfix/main.cf<br>
	```sudo nano /etc/postfix/main.cf ```<br>
     	after this scroll down to bottom of file and change the line <br>
      ```inet_interfaces = all``` to ```inet_interfaces = loopback-only```<br><br>
4th step: Is to install mailutils.<br>
```sudo apt install mailutils```<br><br>
5th step: Send a mail using the following command<br>
```echo 'Enter a mail body here' | mail -s 'enter a subject' resever@gmail.com```

## Que 2: Create a user in your localhost, which should not be able to execute the sudo command.
Ans: <br>
As we created a new user it does not have sudo access by default<br>
and to ensure it we can add that user to nosudo group and than that user not able to execute sudo command<br>
we can add that user to nosudo group by using following command<br>
```sudo usermod -aG nosudo <username>```<br>

## Que 3: Configure your system in such a way that when a user type and executes a describe command from anywhere of the system it must list all the files and folders of the user's current directory.
Ans: <br>
There are two ways to achive this :<br>
	1 : In this we can add describe as aliase of ls command in .bashrc file as follows:<br>
 	``` alias describe = 'ls -a'```<br><br>
 	2 : In this we have to create a file named describe in specific path ```usr/local/bin```<br> 
  	    and write a shell script as follows
```bash
#!/bin/bash
ls -a
```

Save this file and chabge the file permition ```chnod a+x describe ``` now describe command will work as desired.

## Que 4: Users can put a compressed file at any path of the linux file system. The name of the file will be research and the extension will be of compression type, 	example for gzip type extension will be .gz. You have to find the file and check the compression type and uncompress it.
Ans: <br>
	In this I write a shell script name uncompressfile.sh and save it on desktop<br>
 	```nano /home/sigmoid/Desktop uncompressfile.sh```
 ```bash
#!/bin/bash

# Find all compressed research files
files=$(find / -name "research.*" -type f 2>/dev/null)

# Uncompress each file
for file in $files; do
    # Determine the compression type
    compression_type=$(file $file | grep -Po "(?:gzip|bzip2|zip|xz)")

    # Uncompress the file
    case $compression_type in
        "gzip")
            gunzip $file
            ;;
        "bzip2")
            bunzip2 $file
            ;;
        "zip")
            unzip $file
            ;;
        "xz")
            unxz $file
            ;;
    esac
done
```
to execute this file first we have change permitions of this file using this command <br>
```chmod a+x uncompressfile.sh```<br>
now we can execute this as  ```./uncompressfile.sh``` after execution of this shell script it will find the fill name research, determine the compression type and uncompress the file.  
