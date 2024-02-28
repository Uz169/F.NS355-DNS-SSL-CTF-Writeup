# DNSCAP
*** 
Author@???
## 500 points

## Description
    Found this packet capture. Pretty sure there's a flag in here. Can you find it!?
    /dnscap.cap

## Solve
Энэхүү даалгаврын хувьд dnscap.cap гэдэг файл өгөгдсөн бөгөөд задлаад харахад  яачваа сда
      
<p> гэж гарах ба DNS protocol ашигласан их хэмжээний traffic байх ба MX (message exchange) TXT record ууд байсан ба subdomain уудыг hex ээр encode хийсэн
байсныг доорх коммандаар decode хийсэн. </p>


```
tshark -r dnscap.pcap -Tfields -e dns.qry.name > names.txt
```

<p align="center">
  <img src="">
</p>
