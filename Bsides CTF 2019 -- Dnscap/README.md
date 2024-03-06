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
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/Bsides%20CTF%202019%20--%20Dnscap/files/1.png">
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
Үр дүнд нь доорх утгууд гарсан
 
<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/Bsides%20CTF%202019%20--%20Dnscap/files/2.png">
</p>

```
Welcome to dnscap! The flag is below, have fun!!\n
Good luck! That was dnscat2 traffic on a flaky connection with lots of re-transmits. Seriously,
```
гэсэн 2 мөр байсан ба энэ нь DNSCAT2 traffic ашиглаж маш олон дахин илгээлт хийсэн гэсэн hint юм.

DNSCAT2 tool ын хувьд халдагч ба эзлэгдсэн server хооронд command&control (C2) channel үүсгэдэг нэг төрлийн backdoor тэй төсөөтэй гэж хэлж болно. 

мөн өөр сонирхолтой хэсэг байсан нь x00IEND , x00%tEXtdate гэх текстүүд байсан ба энэ IEND гэдэг нь PNG format тай фөйлын 
magicbyte тул DNS ашиглан PNG file явуулсан гэж дүнгээд PNG file -н hex утгуудыг extract хийхэд flag гарч ирнэ.

Үүний тулд PCAP file - аас DNS queries -г салгаж дараагаар нь flag.png гаргадаг script олсон.
```
import binascii
from scapy.all import rdpcap, DNSQR, DNSRR

last_qry = b''
out = b''
q_nb = 0

for p in rdpcap('dnscap.pcap'):

    if p.haslayer(DNSQR) and not p.haslayer(DNSRR):

        qry = p[DNSQR].qname.replace(b'.skullseclabs.org.', b'').split(b'.')
        qry = b''.join(binascii.unhexlify(_.decode()) for _ in qry)[9:]

        if qry == last_qry:
            continue

        last_qry = qry
        q_nb += 1

        if q_nb == 7:  # packet with PNG header
            out += qry[8:]

        if 7 < q_nb < 127:  # All packets up to IEND chunk
            out += qry

open('flag.png', 'wb').write(out)
```

flag.png -- 

<p align="center">
  <img src="https://github.com/Uz169/F.NS355-DNS-SSL-CTF-Writeup/blob/main/Bsides%20CTF%202019%20--%20Dnscap/files/3.png">
</p>
