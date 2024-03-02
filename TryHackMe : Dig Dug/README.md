# Dig Dug THM Machine
*** 

## Description
    Turns out this machine is a DNS server - it's time to get your shovels out!

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/TryHackMe%20%3A%20Dig%20Dug/files/5.png">
</p>

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/TryHackMe%20%3A%20Dig%20Dug/files/6.png">
</p>

## Solve

<p> TryHackMe дээр DNS тэй холбоотой room гүйцэтгэсэн ба DNS Server -лүү givemetheflag.com domain ашиглан flag аа авах хялбар даалгавар өгөгдсөн. </p>
<p> Энэхүү даалгаврыг гүйцэтгэхийн тулд "Passive Reconnaissance" гэх өөр нэг ижил төстэй room ээс доорх коммандыг олсон </p>

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/TryHackMe%20%3A%20Dig%20Dug/files/8.png">
</p>

Уг Форматын дагуу өгөгдсөн утгуудаа орлуулан хийхэд

```
$ dig @10.10.221.82 givemetheflag.com
```
гэж илгээхэд доорх flagыг буцаан илгээнэ.

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/TryHackMe%20%3A%20Dig%20Dug/files/7.png">
</p>

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/TryHackMe%20%3A%20Dig%20Dug/files/4.png">
</p>

flag - flag{0767ccd06e79853318f25aeb08ff83e2}











