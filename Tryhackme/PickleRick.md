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
