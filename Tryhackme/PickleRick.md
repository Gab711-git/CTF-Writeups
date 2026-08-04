# Room Profile
Room Name: Pickle Rick

Difficulty: Easy / Beginner-friendly

Type: Standalone Walkthrough / Practice CTF Machine (Free & Premium accessible)

Category: Web Exploitation & Linux Privilege Escalation

Completed in: 20 minutes

![alt text](../Screenshots/picklerickcomplete.png)

# Room Description:

This Rick and Morty-themed challenge requires you to exploit a web server 
and find three ingredients to help Rick make his potion and transform himself back into a human from a pickle.

Deploy the lab machine on this task and explore the web application: 10.113.184.95

# Basic Enumeration

I began the room by enumerating, I performed an nmap scan to identify the services and ports used by the machine.

 #nmap -sV -p- 10.113.147.255

 Output:

![alt text](../Screenshots/nmapscan.png)

 We identified the services and ports used by the machine, it is running ssh and http services on ports '80' and '443'. Running on versions OpenSSH 8.2p1 and Apache httpd 2.4.21

 # Checking the website

 ![alt text](../Screenshots/index.png)

 We opened the website with firefox browser from the CLI.

 #firefox http://10.113.184.95

 This gave us some clues on what to do,

 -Find 3 'ingredients'
 -Find the Password

 I began enumerating index.html more, I then discovered Rick's username from the comments, which is Username : R1ckRul3s. 

![alt text](../Screenshots/username.png)

I enumerated the website's hidden directories by using a tool called 'gobuster', and found the following directories:

 #gobuster dir -u http://10.113.184.95 -w /usr/share/wordlists/dirb/common.txt -x php,txt,html
 This command uses the tool gobuster, on http://10.113.184.95 to bruteforce directories using a wordlist from /usr/share/wordlists/dirb/common.txt and checks every php,txt and html files.

![alt text](../Screenshots/gobuster.png)

 We opened /robots.txt and found: Wubbalubbadubdub, which I assume the password of Rick?
 Another thing I found interesting is /login.php, so i navigated there and found a credentials input fields.

 ![alt text](../Screenshots/login.png)

 Username : R1ckRul3s (obtained from index.html's comment field)
 Password : Wubbalubbadubdub (obtained from /robots.txt)

# Initial Access

![alt text](../Screenshots/cmdpanel.png)

We got inside Rick's computer after exploiting it, and we also got a command line input field, which blocks the 'cat' command, so I used another command instead, which is 'less'.

I then ran the command 'ls -la' to find Rick's directories, I then found 'Sup3rS3cretPickl3Ingred.txt', we cant perform the 'cat' command so we used an alternative, which is 'less' command.

#ls -la 
#less 'Sup3rS3cretPickl3Ingred.txt'

![alt text](../Screenshots/ingredient1.png)

Output: 'mr. meeseek hair' (The first ingredient)

We then enumerated Rick's home directories

#ls -la /home/rick

and we found a file called 'second ingredients'

#less "/home/rick/second ingredients"

![alt text](../Screenshots/ingredient2.png)

Output: 1 jerry tear (The second ingredient)

I then checked out privileges

#sudo -l

![alt text](../Screenshots/privilege.png)

Discovered www-data has full (ALL : ALL) ALL NOPASSWD privileges. I then inspected the /root directory using elevated privileges to retrieve the final ingredient.


