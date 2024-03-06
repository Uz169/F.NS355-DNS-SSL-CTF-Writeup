# That's not my name
*** 

## Description
    I think some of my data has been stolen, can you help me?

Юун түрүүнд бидэнд notmyname.pcap file өгөгдсөн ба нээж үзэхэд.

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/Bsides%20CTF%202019%20--%20Dnscap/files/9.png">
</p>

гэсэн маш урт DNS,ARP,HTTP,TCP,UDP гэсэн protocol ууд агуулсан file байсан ба дийлэнхи нь нэг их онцын юм агуулаагүй байсан.

Ижил төстэй writeup уншиж байх үед DNS ийн traffic сэжигтэй байсныг анзаарсан ба янз бүрийн site -н нэрний ардаас encoded string залгасан, мессэжний урт нь энгийнээсээ илүү урт, илгээх хурд нь богино гэх мэт зүйлсээс ажиглахад энэ нь DNS tunneling ашиглан DNS Exfiltration attack болохыг мэдсэн.

Энэхүү халдлага нь системээс зөвшөөрөлгүйгээр дата дамжуулах боломж үүсгэдэг ба хялбархан тайлбарлахад жирийн сайтуудын ардаас хортой encoded string үүдийг залгаснаар DNS server уг string үүдийг хувиргах үед комманд гэх мэт зүйлсийг ажлуулах боломжтой болгодог.

DNS tunnel -н хувьд DNS protocol UDP ашигладаг учир илгээсэн мессэжүүдийн дараалал алдагдах, зарим нь очихгүй ч байх магадлалтай тул энэхүү эрсдлээс сэргийлж DNSCAT гэх мэт tools байдаг ба энэ бодлого дээр ашигласан.

Доорх коммандаар ерөнхийдөө notmyname.pcap file аас 3.24.188.205 гэсэн ip хаягруу илгээгдсэн ба зөвхөн response төрлийн DNS query нүүдийг гарган авсан ба

```
tshark -r notmyname.pcapng -T fields -e dns.qry.name -Y "dns.flags.response eq 0 && ip.dst==3.24.188.205" > res.txt
```
Үр дүнд нь 

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/Bsides%20CTF%202019%20--%20Dnscap/files/10.png">
</p>

гэсэн маш урт текстүүд гарсан энэ дунд .qawesrdtfgyhuj.xyz гэсэн хэсэг байх ба үүнийг нь доорх кодоор устгасан. 

```
sed 's/\.qawesrdtfgyhuj\.xyz//' res.txt > new_res.txt
```
үүний дараагаар бидэнд зөвхөн encoded string үүд үлдэх ба

```
xxd -r -p new_res.txt > decoded_res.txt
```
гэсэн коммандаар decode хийхэд 1 png file, lorem ipsum text мөн бодлогын flag гарсан

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/Bsides%20CTF%202019%20--%20Dnscap/files/11.png">
</p>

flag - DUCTF{c4t_g07_y0ur_n4m3}


