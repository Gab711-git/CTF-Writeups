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

 firefox http://10.113.184.95

 This gave us some clues on what to do,

 -Find 3 'ingredients'
 -Find the Password

 I began enumerating index.html more, I discovered the username of Rick in its comments. 

 