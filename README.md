# Linux_assignemt
## Que 1: Configure smtp in localhos.
Ans :<br>
1st step: First we have to install postfix in our linux machine. To install command is <br>
	```sudo apt install postfix```<br><br>
2nd step: After that the installation will start and the postfix window will open. And we have to select some options on that window as followes<br>
	1. select internet site and enter tab and enter enter.<br>
	2. enter custom mall like ex: host.example.com<br><br>
3rd step: After complition of installation we have to make changes in main.cf file present in path /etc/postfix/main.cf<br>
	```sudo nano /etc/postfix/main.cf ```<br>
     	after this scroll down to bottom of file and change the line <br>
      ```inet_interfaces = all``` to  ```inet_interfaces = loopback-only```<br><br>
4th step: Is to install mailutils.<br>
```sudo apt install mailutils```<br><br>
5th step: Send a mail using the following command<br>
```echo 'Enter a mail body here' | mail -s 'enter a subject' resever@gmail.com```

## Que 2: Create a user in your localhost, which should not be able to execute the sudo command.
Ans: <br>
As we created a new user it dous not have sudo access by defult<br>
and to ensure it we can add that user to nosudo group and than that user not able to execute sudo command<br>
we can add that user to nosudo group by using following command<br>
```sudo usermod -aG nosudo <username>```<br>
