# Cheatsheet 

## Sending And Receiving Files With Netcat

##gobuster
sudo gobuster -w /usr/share/wordlist/dirbuster/directory-list-lowercase-2.3-medium.txt http://<ip> -x html,php,txt,git -s 200,204,301,302,307,403,401

##nmap
#all scan`sudo nmap -p- -sV -T5 -sC -v <ip>`
#ping sweep `sudo nmap -pn <ip>`

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
