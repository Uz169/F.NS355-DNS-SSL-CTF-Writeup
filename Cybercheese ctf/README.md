# DNS Zone Transfer (Recon)
*** 
Author@???

## Description
 cybercheese.io @40.115.53.104

## Solve
Энэхүү даалгаврын хувьд зөвхөн  cybercheese.io @40.115.53.104 гэсэн domain мөн ip хаяг өгөгдсөн ба DNS server-н лүү хэн ч zone transfer -р хандах 
боломжтой алдаатай тохиргоо хийсэн.

Zone transfer буюу AXFR нь DNS replicate (хуулбарлах) боломжийг олгодог DNS query төрөл юм: query-н үр дүнд нь DNS Zone -ы одоогийн тохиргооны
хуулбар гарна.

```
$ dig -t AXFR cybercheese.io @40.115.53.104
```
гэсэн коммандыг ажиллуулахад 

```
cybercheese.io. 600 IN SOA ns.cybercheese.io. root.cybercheese.io. 2015101901 10800 600 604800 600
cybercheese.io. 600 IN NS ns.cybercheese.io.
cybercheese.io. 600 IN A 40.115.53.104
file.cybercheese.io. 600 IN TXT "02b4520388c01f012c8a52bfa9f9140cfe4c6fdd1884ada7ef849a4e533b3451055325a4 ...
file.cybercheese.io. 600 IN TXT "068d19000340000000006d434c868c9a321a34f534c9a6441a0d003200d1a0000064c800 ...
file.cybercheese.io. 600 IN TXT "0c80034d00680001ea000003434d1a1a00d00000000680000000007a4d00f95c1193209a ...
file.cybercheese.io. 600 IN TXT "0e51541ce1c3d2aeaf5dea313f0c1d217c3d488a73ac4450a4b9406532e27f90b205c238 ...
file.cybercheese.io. 600 IN TXT "425a6839314159265359880751450000917fffffffddff75fd3f3ff7e57fb7ef8fff7dff ...
file.cybercheese.io. 600 IN TXT "7dbaa2229614a6192320713c5098d5c3fc590a70b546f281733c1e7577a7a070914168eb ...
file.cybercheese.io. 600 IN TXT "f2ea3bd4c344aafa3264860f358822dcd7459cc7573eb07c01fa58d5c2abe0d1785d5435 ...
file.cybercheese.io. 600 IN TXT "f519e37ac851700ee8c4260ad95fb864742f42724d4f7c2309424a31ea48cae1070e1148 ...
**flag1.cybercheese.io. 600 IN TXT "CCC1{Thr33_R1ngs_f0r_th3_3lv3n-k1ngs_und3r_th3_sky}"**
hint.cybercheese.io. 600 IN TXT "Unshuffle_and_decompress_me"
ns.cybercheese.io. 600 IN A 40.115.53.104
```
гэсэн үр дүнг буцаана 

flag -- CCC1{Thr33_R1ngs_f0r_th3_3lv3n-k1ngs_und3r_th3_sky}
