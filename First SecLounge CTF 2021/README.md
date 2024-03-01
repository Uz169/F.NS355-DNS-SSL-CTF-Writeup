The Golden DNS Part 1
*** 
#Point - 250

## Description

mutaloitepammo.xyz What is the key (mykey)?

## Solve
Энэхүү даалгаварт mutaloitepammo.xyz гэсэн DNS Server домайн нэр л зөвхөн өгөгдсөн байсан.
Энгийн dig коммандаар flag шууд гарж ирэхгүй байсан тул хэсэг судласны эцэст доорх CHAOS Class ашиглан TXT record 
уудыг унших хүсэлт явуулж болдог гэж мэдсэн

```
dig @ns1.mutaloitepammo.xyz CH TXT version.bind
```

гэсэн комманд оруулахад буцаад

```
version.bind.0CHTXT"mykey:sFWxPdcc5rCKrSiGaXaVHnxs/D25+mbc7GxQOqpUvZ8="
```
гэсэн утга ирсэн ба flag нь буюу mykey - sFWxPdcc5rCKrSiGaXaVHnxs/D25+mbc7GxQOqpUvZ8=
