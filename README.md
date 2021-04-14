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

## BE01 - Binary
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

## BE02 - Binary
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
## CM01 - Crypto
>Briefing: Download the file and find a way to get the flag.
Contents: code.png, frame.png

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/CM01_2.png)

In this challenge we are given a QR Code that is broken along with a another QR code called frame. If you scan the frame it tells you 
<code>"Hey , I've put the flag into the other file using the same trick we always use. You know what to do :)"</code>

I have no idea what this means or even what to do, my first guess is that I have to repair this QR code manually , so I open up GIMP and get to recoloring the broken parts using the frame as a guide.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/CM01_3.png)

That is  when I realize, I am just tracing frame over the original broken QR code and it overlaps with the messed up parts in the code.png . So If i were to subtract the frame from the code I might get something that I can use.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/CM01_4.png)
![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/CM01_5.png)

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/CM01_6.png)

After a few mistakes I am able to produce a readable QR code, only issue though is when you scan it it give you no input. 
After a bit of googling I am able to find a site that can repair QR codes(https://merricx.github.io/qrazybox/)
 It is unable to decode the string but I am able to get the bits
 <code>["01110001","10100101","00010111","01000110","01001100","00000001","01000111","00111010","00100000","01000001","01011111","01000011","01101111","01100100","01100101","01011111","01000110","01101111","01110010","01011111","01001001","01011111","01000011","01101111","01101100","01100101","00000000","11101100","00110001","11101100","00011001","11101100","00010001","11101100","00011011","10011111","11010101","00100011","00101111","11111000","01110000","01011000","10111101","10101110"]</code>
 
 I put the bits into a binary to text translator and get
 
 ![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/CM01_7.png)
 
 However this flag is not accepted, after a small bit of trial and error , I am able to get the real flag
 
**Flag:** <code>A_Code_For_A_Code</code>

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## FE04 - Forensics 
>Briefing: Download the file and filter down to the username according to criteria below.

>The username you are looking for has x as the 3rd character, followed immediately by a number from 2 to 6, it has a Z character in it and the last character is S.

>When you have the username, submit it as the flag.Contents: 50k-users.txt

In this challenge we are given a massive list of user names (50 thousand) and we are to find the specific username that matches up with the requirements above. 

For this one I went straight to cyberchef, cyberchef has an easy to use reg ex command that makes it easy to sort through tons of information.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/FE04.png)

I used the recipe <code>..x[2-6].....*S$</code>
Afterwords I exported the rest of the usernames into a text document and used a "Ctrl+F" to search for the letter "Z" to find my flag. 

**Flag:** <code>YXx52hsi3ZQ5b9rS</code>


---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## FM01
>Briefing: Download the file and find a way to get the flag.

>Contents: fm01.jpg
![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/FM01_1.png)

In this section we are given a jpg, when opened has some crazy colors in it. My first idea was that this was definitively a stenography challenge, so i booted up stegsolve on and started messing around with different color pallets, 

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/FM01_2.png)

The closest I was able to get was with the blue overlay, I switched over to my windows OS since I had some more stegtools already downloaded on there. But when I look over at the file preview in the folder I notice something.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/FM01_4.png)

I don't know how but the picture is showing more readable parts, I quickly take a screen shot and then blow it up in paint.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/FM01_5.png)

If you tilt your head back or stand away from the computer you can kinda make out enough of the flag to decode it. After a trying a few different answers I obtain the real flag.

**Flag:** <code>tr4il3r_p4rk</code>

---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
### FM02



---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## NE01 - Networking 
>Briefing: There is a TCP network service running on cfta-ne01.allyourbases.co. Find it to get the flag after you connect.

>Note: The target has many open ports - only one is the correct one. The correct port will identify itself with ID: ne01 after you connect.

This is a simple challenge, we just need to scan all the ports on this host and find the ones that are up.

The command I used was <code>nmap -sT -Pn -p- cfta-ne01.allyourbases.co</code>
this will scan all the possible ports and report back after its done.
Then all thats left to do is to nc into the host at the correct port.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/ne01_1.png)




**Flag:** <code>Nmap_0f_the_W0rld!</code>



---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------
## NE01 - Networking 
>Briefing: There is a TCP network service running on cfta-ne01.allyourbases.co. Find it to get the flag after you connect.

>Note: The target has many open ports - only one is the correct one. The correct port will identify itself with ID: ne01 after you connect.

Once we connect we are greeted with this message, 

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/NM01_1.png)

It seems like it wants the hex value input to be sent back to it , after trying a few times it seems like the hex values also change each time and can be mapped to letters


My first though is to create a python script that will spit out the input back to the command line, after a bit of googling and failing alot I create godwhy.py. 

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/NM01_2.png)

This script should strip the input of the \x and only leave the hex values behind.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/NM01_3.png)

It works but it has one major issue, I can't see any input after I pipe the input to the python script. I have no idea if its actually working and sending the information back or just failing.

I came back to this one later on in the competition and out of sheer desperation I try running another pipe that will connect back into the host. 

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/NM01_4.png)

And it works! for some reason! (I honestly am still confused on to why this works)



**Flag:** <code>o[hex]=>i[ascii]=:)</code>

- - - -

## WE01 - Web Applications
>Briefing: View the page at https://cfta-we01.allyourbases.co and try to get the flag.
>
![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/WE01_1.png)

When you first connect you are greeted with a giant glowing wall of text that is made of up random shapes.
Right off the bat, I go to see if the site has a robots.txt file, no luck. I then head over to inspect the elements.

If you google the language you end up being linked to a twitter post of the creator who made this.

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/WE01_2.png)

That lead to a website where the creator of the this script explained the funtionality of it, unforuntantely it still wasn't making much sense to me. I understood it was javascript but other than that I was drawing blanks. 
I tried manually decoding it using a Aurebesh alphabet but the translation was making no sense.

Eventually we got a hint released to use 

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/WE01_3.png)

And then it all clicked, I opened up the dev console, copied the weird code and ran it

![picture alt](https://github.com/Hexachords/Cyber-Fasttrack-2021-Writeup/blob/main/WE01_FLAG.png)

Flag found!


**Flag:** <code>unicode+obfuscation=js*fun</code>



- - - -

### WE02
