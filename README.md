# Jarkom-Modul-3-E13-2022
- Rycahaya Sri Hutomo (5025201046)
- Agnesfia Anggraeni (5025201059)


## TOPOLOGI JARINGAN
![image](https://user-images.githubusercontent.com/94664966/201513484-6d79db59-5c83-4f5a-8a83-e4f7a2bb579d.png)

## KONFIGURASI IP
### Ostania
```
auto eth0
iface eth0 inet dhcp

auto eth1
iface eth1 inet static
	address 10.28.1.1
	netmask 255.255.255.0

auto eth2
iface eth2 inet static
	address 10.28.2.1
	netmask 255.255.255.0

auto eth3
iface eth3 inet static
	address 10.28.3.1
	netmask 255.255.255.0
```
### SSS
```
auto eth0
iface eth0 inet static
  address 10.28.1.2
  netmask 255.255.255.0
  gateway 10.28.1.1
```
### Garden
```
auto eth0
iface eth0 inet static
  address 10.28.1.3
  netmask 255.255.255.0
  gateway 10.28.1.1
```
### WISE
```
auto eth0
iface eth0 inet static
	address 10.28.2.2
	netmask 255.255.255.0
	gateway 10.28.2.1
```
### Berlint
```
auto eth0
iface eth0 inet static
	address 10.28.2.3
	netmask 255.255.255.0
	gateway 10.28.2.1
```
### Westalis
```
auto eth0
iface eth0 inet static
	address 10.28.2.4
	netmask 255.255.255.0
	gateway 10.28.2.1
```
### KemonoPark
```
auto eth0
iface eth0 inet static
  address 10.28.3.2
  netmask 255.255.255.0
  gateway 10.28.3.1
 ```
 ### NewstoneCastle
 ```
auto eth0
iface eth0 inet static
  address 10.28.3.3
  netmask 255.255.255.0
  gateway 10.28.3.1
```
## NOMOR 1
Loid bersama Franky berencana membuat peta tersebut dengan kriteria WISE sebagai DNS Server, Westalis sebagai DHCP Server, Berlint sebagai Proxy Server<br>

### <code>1.sh</code> di WISE
WISE akan dijadikan sebagai DNS Server, maka di Install bind9, lalu start.<br>
![image](https://user-images.githubusercontent.com/94664966/201514334-2476fead-4039-4fc0-b2d3-8416c0c0f0ce.png)<br>

### <code>1.sh</code> di Westalis
Westalis akan dijadikan sebagai DHCP Server, maka install <code>isc-dhcp-server</code>, lalu cek versinya.<br>
![image](https://user-images.githubusercontent.com/94664966/201514515-c3c7e4f1-de29-4097-9949-7d94396d6622.png)<br>

### <code>1.sh</code> di Berlint
Berlint akan dijadikan sebagai Proxy Server, maka install squid, lalu start.<br>
![image](https://user-images.githubusercontent.com/94664966/201514586-7717b9b5-edc2-4166-8387-f541fa2f890e.png)<br>

## NOMOR 2
Ostania sebagai DHCP Relay<br>

### <code>2.sh</code> di Ostania
Install <code>isc-dhcp-relay</code>, kemudian atur server dan interfacenya seperti gambar berikut<br>
![image](https://user-images.githubusercontent.com/94664966/201514654-2056b181-cdb6-4ed0-a2ab-bd706e1b67f5.png)<br>

## NOMOR 3
Semua client yang ada HARUS menggunakan konfigurasi IP dari DHCP Server.<br>
Client yang melalui Switch1 mendapatkan range IP dari [prefix IP].1.50 - [prefix IP].1.88 dan [prefix IP].1.120 - [prefix IP].1.155<br>

### Westalis
Karena Switch1, maka subnet <code>10.28.1.0</code>.<br>
Kemudian masukkan range IP sesuai soal.<br>
Option routers diisi <code>10.28.1.1</code>.<br>
Restart dhcp server, lalu cek status.<br><br>
![image](https://user-images.githubusercontent.com/94664966/201514815-b5d78420-f22e-4b29-8304-dcfd36686882.png)<br>

### SSS
![image](https://user-images.githubusercontent.com/94664966/201514885-5e41bfa4-b098-40bc-aa32-ec6dfdcae3ea.png)

### Garden
![image](https://user-images.githubusercontent.com/94664966/201514929-98f2bb86-edbe-4a72-9848-7654d942e596.png)

## NOMOR 4
Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.10 - [prefix IP].3.30 dan [prefix IP].3.60 - [prefix IP].3.85<br><br>

### Westalis
Karena Switch3, maka subnet <code>10.28.3.0</code>.<br>
Kemudian masukkan range IP sesuai soal.<br>
Option routers diisi <code>10.28.3.1</code>.<br>
Restart dhcp server, lalu cek status.<br><br>
![image](https://user-images.githubusercontent.com/94664966/201515332-78af5089-4bf3-4dd0-9ae5-f1d4310c7cc7.png)
![image](https://user-images.githubusercontent.com/94664966/201515369-d9c60a43-3cad-4393-9753-352426c01676.png)

### Eden
![image](https://user-images.githubusercontent.com/94664966/201515416-1c4e0068-3120-4bd5-b38f-cf113bb403c5.png)

### NewstoneCastle
![image](https://user-images.githubusercontent.com/94664966/201515442-29e07b60-0449-4a14-aab7-957083d301e9.png)

### KemonoPark
![image](https://user-images.githubusercontent.com/94664966/201515517-f75bc6b5-4451-4a76-ad1b-5f921351380d.png)

## NOMOR 5
Client mendapatkan DNS dari WISE dan client dapat terhubung dengan internet melalui DNS tersebut.<br>

### WISE
Tulis directory `/var/cache/bind`<br>
Atur forwarders ke nameserver, yaitu `192.168.122.1`<br>
![image](https://user-images.githubusercontent.com/94664966/201515567-77dead54-b4c9-46c3-856f-aedca021d418.png)

### Westalis

![image](https://user-images.githubusercontent.com/94664966/201515620-d57462b1-cd2d-4af4-9017-46a6b36b17cc.png)

### Ostania

![image](https://user-images.githubusercontent.com/94664966/201515672-736bc2a9-2cef-4468-b35d-304a7c56b980.png)

### SSS, Garden, Eden, Newstone, KemonoPrak

![image](https://user-images.githubusercontent.com/94664966/201515759-9eb964bc-0644-4048-9d1a-1d1878438c72.png)

hasil bash

![image](https://user-images.githubusercontent.com/94664966/201515789-520a7fba-f19f-4b1d-8bdb-c654ada9ccc1.png)

## NOMOR 6
Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch1 selama 5 menit sedangkan pada client yang melalui Switch3 selama 10 menit. Dengan waktu maksimal yang dialokasikan untuk peminjaman alamat IP selama 115 menit.

### Westalis

![image](https://user-images.githubusercontent.com/94664966/201515968-a8b0f118-8395-47f0-9e26-17cccdb23ccb.png)
![image](https://user-images.githubusercontent.com/94664966/201515993-8565bed2-7470-4164-ab77-ea019758879c.png)

## NOMOR 7
Loid dan Franky berencana menjadikan Eden sebagai server untuk pertukaran informasi dengan alamat IP yang tetap dengan IP [prefix IP].3.13

### Eden

![image](https://user-images.githubusercontent.com/94664966/201516050-88bbb142-a7a7-455e-b468-cdcaba6503cc.png)

hasil bash

![image](https://user-images.githubusercontent.com/94664966/201516119-d01c9444-5792-4527-ace8-7b5a8f70973e.png)

### Westalis

![image](https://user-images.githubusercontent.com/94664966/201516239-317a788a-5b74-4fe2-ab3c-73abf1f23932.png)
![image](https://user-images.githubusercontent.com/94664966/201516273-b35cdceb-1963-4ee3-a41c-0cc75b77ec12.png)

### Ostania

![image](https://user-images.githubusercontent.com/94664966/201516316-f053e818-09a3-41e9-8073-522dce2c6896.png)

### Eden

![image](https://user-images.githubusercontent.com/94664966/201516365-e2f81ad0-f2eb-41b2-9659-16cca1f797f5.png)

  Restart Node Eden untuk melihat IP terbaru 
  ![image](https://user-images.githubusercontent.com/94664966/201516417-ef64cd4c-aa99-4682-b29a-b96b7a41327c.png)

## NOMOR 8a (Proxy)
Client hanya dapat mengakses internet diluar (selain) hari & jam kerja (senin-jumat 08.00 - 17.00) dan hari libur (dapat mengakses 24 jam penuh)

### Berlint
```
echo '
acl WORKING time MTWHF 08:00-17:00

' > /etc/squid/acl.conf 

echo '
include /etc/squid/acl.conf

http_port 8080
http_access deny WORKING
http_access allow all 
visible_hostname Berlint

' > /etc/squid/squid.conf

service squid restart
```

### SSS
```
apt-get update
apt-get install lynx -y

export http_proxy="http://10.28.2.3:8080"

date -s "7 NOV 2022 13:30:00"
lynx google.com
```

### Garden
```
apt-get update
apt-get install lynx -y

export http_proxy="http://10.28.2.3:8080"

date -s "7 NOV 2022 13:30:00"
lynx google.com
```

## NOMOR 8b (Proxy)
Adapun pada hari dan jam kerja sesuai nomor (1), client hanya dapat mengakses domain loid-work.com dan franky-work.com (IP tujuan domain dibebaskan)

### WISE
```
echo '
zone "loid-work.com" {
        type master;
        file "/etc/bind/jarkom/loid-work.com";
};
zone "franky-work.com" {
        type master;
        file "/etc/bind/jarkom/franky-work.com";
};
' > /etc/bind/named.conf.local

mkdir /etc/bind/jarkom

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     loid-work.com. root.loid-work.com. (
                     2022110901         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      loid-work.com.
@       IN      A       10.28.2.2
' > /etc/bind/jarkom/loid-work.com

echo '
;
; BIND data file for local loopback interface
;
$TTL    604800
@       IN      SOA     franky-work.com. root.franky-work.com. (
                     2022110902         ; Serial
                         604800         ; Refresh
                          86400         ; Retry
                        2419200         ; Expire
                         604800 )       ; Negative Cache TTL
;
@       IN      NS      franky-work.com.
@       IN      A       10.28.2.2
' > /etc/bind/jarkom/franky-work.com

service bind9 restart
```

### Berlint
```
echo '
loid-work.com
franky-work.com
' > /etc/squid/work-sites.acl

echo '
include /etc/squid/acl.conf

http_port 8080
visible_hostname Berlint

acl WORKSITES dstdomain "/etc/squid/work-sites.acl"
http_access allow WORKSITES
http_access deny WORKING
http_access allow all

' > /etc/squid/squid.conf

service squid restart
```

### SSS
```
export http_proxy="http://10.28.2.3:8080"

date -s "7 NOV 2022 13:30:00"

lynx franky-work.com
lynx loid-work.com
lynx google.com
```

## NOMOR 8C (Proxy)
Saat akses internet dibuka, client dilarang untuk mengakses web tanpa HTTPS. (Contoh web HTTP: http://example.com)

### Berlint
```
echo '
include /etc/squid/acl.conf

http_port 8080
visible_hostname Berlint

acl WORKSITES dstdomain "/etc/squid/work-sites.acl"
http_access allow WORKSITES
http_access deny WORKING
http_access deny all


' > /etc/squid/squid.conf

service squid restart
```

### SSS
```
export http_proxy="http://10.28.2.3:8080"

date -s "7 NOV 2022 18:30:00"

lynx http://www.example.com
lynx https://www.example.com
```

## NOMOR 8d (Proxy)
Agar menghemat penggunaan, akses internet dibatasi dengan kecepatan maksimum 128 Kbps pada setiap host (Kbps = kilobit per second; lakukan pengecekan pada tiap host, ketika 2 host akses internet pada saat bersamaan, keduanya mendapatkan speed maksimal yaitu 128 Kbps)

### Berlint
```
echo '
include /etc/squid/acl.conf

http_port 8080
visible_hostname Berlint

acl WORKSITES dstdomain "/etc/squid/work-sites.acl"
http_access allow WORKSITES
http_access deny WORKING
http_access allow all

delay_pools 1
delay_class 1 2 
delay_access 1 allow all
delay_parameters 1 none 16000/32000
' > /etc/squid/squid.conf

service squid restart
```

### SSS
```
unset http_proxy

apt-get install speedtest-cli -y

export PYTHONHTTPSVERIFY=0
export http_proxy="http://10.28.2.3:8080"

date -s "7 NOV 2022 18:30:00"
speedtest
```

### Garden
```
unset http_proxy

apt-get install speedtest-cli -y

export PYTHONHTTPSVERIFY=0
export http_proxy="http://10.28.2.3:8080"

date -s "7 NOV 2022 18:30:00"
speedtest
```

## NOMOR 8E (Proxy)

### Berlint
```
echo '
include /etc/squid/acl.conf

http_port 8080
visible_hostname Berlint

acl WORKSITES dstdomain "/etc/squid/work-sites.acl"
http_access allow WORKSITES
http_access deny WORKING
http_access allow all

acl OPEN_TIME time MTWHF
delay_pools 1
delay_class 1 2
delay_access 1 allow !OPEN_TIME
delay_parameters 1 none 16000/32000
' > /etc/squid/squid.conf

service squid restart
```

### SSS
```
unset http_proxy

export PYTHONHTTPSVERIFY=0
export http_proxy="http://10.28.2.3:8080"

date -s "6 NOV 2022 18:30:00"
speedtest
```

### Garden
```
unset http_proxy

export PYTHONHTTPSVERIFY=0
export http_proxy="http://10.28.2.3:8080"

date -s "7 NOV 2022 13:30:00"
speedtest
```
