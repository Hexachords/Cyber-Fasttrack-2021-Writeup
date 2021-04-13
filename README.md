# Cyber-Fasttrack-2021-Writeup





##### Binary
* BE01
* BE02
##### Crypto
* CM01

##### Forensics
* FE04
* FM01
* FM02

##### Networking 
* NE01
* NM01

##### Web Applications 
* WE01
* WE02


- - - -
![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/BE01_1.png)
### BE01 - Binary
>Briefing: Download the file and find a way to get the flag.
Contents: chicken.pdf

 ![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/BE01_2.png)
 
In this challenge we are given a file chicken.pdf and we are expected to find a flag in it, off the bat there is nothing really go off. There is no hidden text in white in the pdf . With no idea what to do next I decide to check the chicken.pdf headers in a hex editor

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/BE01_3.png)

While checking this I see something more interesting, there is an "egg.zip" and "chicken.zip" headers hidden in this pdf,  which means that there is files hidden in this file that can be extracted. Just to see if it would work I change the files extension from a pdf to a zip.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/BME1_EggChick.png)

And it works, if we follow the chain of opening files we finally reach egg.pdf which contains the flag.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/BE01_Flag.png)

**Flag:** <code>wh1ch_came_f1rst?</code>

- - - -
![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/BE02_1.png)
### BE02 - Binary
>Briefing: Download the file and find a way to get the flag.
Contents: rot13

 Now we start to get into the real binary challenges, I am also a complete beginner when it comes to these challenges so I was happy to be able to solve at least one of the real binary challenges.
 
In this challenge we are given a file called rot13 and if we run it we get.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/BE02_Input.png)

This input seems to be using a cipher possibly rot13. Now with any binary challenges I like to try to and see what would happen if just input a lot of information into the prompt, this is more or less a buffer overflow and it can reveal information about whats going on behind the scenes.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/BE02_FLAG.png)

And it works! (This probably wasn't the way the challenge was intended to be solve but the flag was still retrieved!)

**Flag:** <code>luckyNumber13</code>



---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### CM01


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### FE04


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### FM01



---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### FM02



---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### NE01



---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### NM01

- - - -

### WE01


- - - -

### WE02
