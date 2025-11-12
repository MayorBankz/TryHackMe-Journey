# TryHackMe - Offensive Security
* Link:  https://tryhackme.com/room/offensivesecurityintro
* Date: 11-11-2025
* Skills Learned: How to use Gobuster to discover hidden web directories or pages



## Summary
 
Offensive security is about testing computer systems by trying to break into them to find weaknesses and fix them before real hackers do.
The goal is to understand hacker tactics and enhance our defences.

 "To outsmart a hacker, you need to think like one". This is the core of offensive security.

 ## Goals
 - Gain access to hidden pages of bank websites
 - Perform unauthorized transactions

## Scenario
Using a command-line application called "Gobuster" to brute-force FakeBank's website to find hidden directories and pages.
Gobuster will take a list of potential page or directory names and try accessing a website with each of them; if the page exists, it tells you.


<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/6d1cc416-04a4-4178-8d50-0bd2b12f1e08" />

* Step 1 - Open a terminal

<img width="600" height="250" alt="image" src="https://github.com/user-attachments/assets/a9bab269-30ac-47bb-9b71-e8bcc938298b" />

* Step 2 - Use Gobuster to find Hidden website pages
<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/b14b38ae-efbd-4e9e-a8a6-92597038c64c" />

In the cmd above, <em>-u</em> is used to state the website you are scanning, <em>-w</em> takes a wordlist to iterate through to find hidden pages.

* Step 3 - Hack The Bank

<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/e06db40e-5398-48a3-8538-078d644fe723" />


<img width="600" height="400" alt="image" src="https://github.com/user-attachments/assets/0b715130-d1f3-4556-aa86-b680634ffcb4" />






