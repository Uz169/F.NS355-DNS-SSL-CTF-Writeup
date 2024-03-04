# That's not my name
*** 

## Description
    I think some of my data has been stolen, can you help me?

Юун түрүүнд бидэнд notmyname.pcap file өгөгдсөн ба нээж үзэхэд.

<p align="center">
  <img src="">
</p>

гэсэн маш урт DNS,ARP,HTTP,TCP,UDP гэсэн protocol ууд агуулсан file байсан. Үүн дотроос DNS ээс бусад дийлэнхи нь сэжигтэй биш байсан тул зөвхөн DNS дээр шинжилгээ хийсэн.
Ижил төстэй writeup уншиж байх үед DNS ийн traffic сэжигтэй байсныг анзаарсан ба янз бүрийн site -н нэрний ардаас encoded string залгасан, мессэжний урт нь арай урт, илгээх хурд нь богино
гэх мэт зүйлсээс ажиглахад энэ нь DNS Exfiltration attack болохыг мэдсэн.

Энэхүү халдлага нь 
