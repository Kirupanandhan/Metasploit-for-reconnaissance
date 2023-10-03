# Metasploit-for-reconnaissance
Metasploit for reconnaissance in pentesting

# AIM:

To get introduced to Metasploit Framework and to  perform reconnaissance  in pentesting .

## DESIGN STEPS:

1) Install kali linux either in partition or virtual box or in live mode
2) Investigate on the various categories of tools as follows
3) Open terminal and try execute some kali linux commands

## EXECUTION STEPS AND ITS OUTPUT:

Find out the ip address of the attackers system

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/97b6f71d-e792-4522-9b83-640ba7d34300)


Invoke msfconsole:

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/f0539e4d-9e07-4bb5-b971-df85b9f39a64)


Type help or a question mark "?" to see the list of all available commands you can use inside msfconsole.

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/5f334b43-2e30-44a4-8103-11a980d8fc81)


Port Scanning:

Following command is executed for scanning the systems on our local area network with a TCP scan (-sT) looking for open ports between 1 and 1000 (-p1-1000). msf > nmap -sT 192.168.1810/24 -p1-1000

## OUTPUT:

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/168d07ee-f2b5-428e-8c62-19dd716a3d2a)


USE the db-nmap command to scan and save the results into Metasploit's postgresql attached database. In that way, you can use those results in the exploitation stage later.

scan the targets with the command db_nmap as follows. msf > db_nmap 192.168.181.0/24


## OUTPUT:

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/c48698a2-1273-4a5c-9b89-2de39dffd5f3)


Metasploit has a multitude of scanning modules built in. If we open another terminal, we can navigate to Metasploit's auxiliary modules and list all the scanner modules. cd /usr/share /metasploit-framework/modules/auxiliary kali > ls -l

## OUTPUT:

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/4205f7d6-0d17-416b-a81b-ca8561715b37)


Search is a powerful command in Metasploit that you can use to find what you want to locate. msf >search name:Microsoft type:exploit

The info command provides information regarding a module or platform,

## OUTPUT

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/e619d937-b7dc-46cd-a8e2-aac096cabd74)


Before beginning, set up the Metasploit database by starting the PostgreSQL server and initialize msfconsole database as follows: systemctl start postgresql msfdb init

## MYSQL ENUMERATION

Find the IP address of the Metasploitable machine first. Then, use the db_nmap command in msfconsole with Nmap flags to scan the MySQL database at 3306 port. db_nmap -sV -sC -p 3306 <metasploitable_ip_address>

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/9d3115ff-c45c-47a6-a546-abe68ce95972)

Use the search option to look for an auxiliary module to scan and enumerate the MySQL database. search type:auxiliary mysql

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/35953259-60d6-4eec-a54d-954d08a8c5bc)


use the auxiliary/scanner/mysql/mysql_version module by typing the module name or associated number to scan MySQL version details. use 11 Or: use auxiliary/scanner/mysql/mysql_version

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/750b6904-5cde-4a0e-a947-af80b9438a29)


Use the set rhosts command to set the parameter and run the module, as follows:

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/b0a04334-6866-48ca-a30e-4329baf7d36d)


After scanning, you can also brute force MySQL root account via Metasploit's auxiliary(scanner/mysql/mysql_login) module.

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/3e0292ce-2c86-4608-8305-77864c90e1d0)


set the PASS_FILE parameter to the wordlist path available inside /usr/share/wordlists: set PASS_FILE /usr/share/wordlistss/rockyou.txt Then, specify the IP address of the target machine with the RHOSTS command. set RHOSTS Set BLANK_PASSWORDS to true in case there is no password set for the root account. set BLANK_PASSWORDS true

![image](https://github.com/Kirupanandhan/Metasploit-for-reconnaissance/assets/94386222/1d49f3e1-fc95-46e3-86b9-14929a38703f)



## RESULT:

The Metasploit framework for reconnaissance is  examined successfully
