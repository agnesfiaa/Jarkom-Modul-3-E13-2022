# Jarkom-Modul-3-E13-2022
- Rycahaya Sri Hutomo (5025201046)
- Agnesfia Anggraeni (5025201059)


## TOPOLOGI JARINGAN
[GAMBAR TOPOLOGI]

## KONFIGURASI IP
### Ostania

## NOMOR 1
Loid bersama Franky berencana membuat peta tersebut dengan kriteria WISE sebagai DNS Server, Westalis sebagai DHCP Server, Berlint sebagai Proxy Server<br>
1. <code>bash 1.sh</code> di WISE
2. <code>bash 1.sh</code> di Westalis
3. <code>bash 1.sh</code> di Berlint

## NOMOR 2
Ostania sebagai DHCP Relay<br>
<code>bash 2.sh</code> di Ostania

## NOMOR 3
Semua client yang ada HARUS menggunakan konfigurasi IP dari DHCP Server.<br>
Client yang melalui Switch1 mendapatkan range IP dari [prefix IP].1.50 - [prefix IP].1.88 dan [prefix IP].1.120 - [prefix IP].1.155<br>


## NOMOR 4
Client yang melalui Switch3 mendapatkan range IP dari [prefix IP].3.10 - [prefix IP].3.30 dan [prefix IP].3.60 - [prefix IP].3.85<br>
RUN 

## NOMOR 5
Client mendapatkan DNS dari WISE dan client dapat terhubung dengan internet melalui DNS tersebut.

## NOMOR 6
Lama waktu DHCP server meminjamkan alamat IP kepada Client yang melalui Switch1 selama 5 menit sedangkan pada client yang melalui Switch3 selama 10 menit. Dengan waktu maksimal yang dialokasikan untuk peminjaman alamat IP selama 115 menit.

## NOMOR 7
Loid dan Franky berencana menjadikan Eden sebagai server untuk pertukaran informasi dengan alamat IP yang tetap dengan IP [prefix IP].3.13
