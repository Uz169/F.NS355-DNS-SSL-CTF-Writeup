# DNSCAP
*** 
Author@???
## 500 points

## Description
    Found this packet capture. Pretty sure there's a flag in here. Can you find it!?
    /dnscap.cap

## Solve
Энэхүү даалгаврын хувьд dnscap.cap гэдэг файл өгөгдсөн бөгөөд задлаад харахад

<p align="center">
  <img src="">
</p>
      
<p> гэж гарах ба DNS protocol ашигласан их хэмжээний traffic байх ба MX (message exchange) TXT record ууд байсан ба subdomain уудыг hex ээр encode хийсэн
байсныг доорх коммандаар decode хийсэн. </p>


```
tshark -r dnscap.pcap -Tfields -e dns.qry.name > names.txt
```
ASCII hex ээс raw руу хөрвүүлэх код
```
import re
import binascii

with open('names.txt', 'r') as f:
    for name in f:
        m = re.findall('([a-z0-9\.]+)\.skull', name)
        if m:
            try:
                ascii_string = binascii.unhexlify(m[0].replace('.', '')).decode('utf-8')
                print(ascii_string)
            except UnicodeDecodeError:
                # If decoding as UTF-8 fails, print the raw bytes
                print(binascii.unhexlify(m[0].replace('.', '')))

```

 
<p align="center">
  <img src="">
</p>
