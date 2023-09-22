# Jarkom-Modul-1-D21-2023

# Anggota Kelompok:
+ Akbar Putra Asenti Priyanto (5025211004)
+ Farrela Ranku Mahhissa (5025211138)

## Soal 1
Dalam soal ini diberikan sebuah file .pcap dimana seorang user mengunggah sebuah file, kemudian kita diminta untuk mencari tahu raw sequence number dan raw acknowledge number dari proses tersebut dan response dari proses tersebut.

Langkah pertama adalah kita perlu mencari tahu nilai raw sequence dan raw acknowledge dari setiap packet, pastikan bahwa Wireshark selalu menampilkan kedua hal tersebut dengan cara mengubah settings Wireshark di **Edit** >> **Preferences** >> **Protocols** >> **TCP**. Pastikan setting "Relative sequence numbers" tidak dicentang.

![Wireshark_Preferences](/Assets/1_Preferences.png)

Selanjutnya lakukan follow TCP Stream dan cari stream dimana user mengupload sebuah file. Disini ditemukan proses tersebut dalam TCP Stream ke-4. Hal ini ditandai dengan adanya command **STOR** yang menandakan upload file ke FTP Server.

![1_Stream](/Assets/1_Stream.png)

Kemudian buka detail packet tersebut yaitu packet 147 dan lihat raw sequence dan raw acknowledge number yang ditampilkan.

![1_Request](/Assets/1_Request.png)

Selanjutnya lihat TCP Stream kembali dan buka detail respons di packet 149 dan lakukan hal yang sama dengan sebelumnya.

![1_Response](/Assets/1_Response.png)

Berikut adalah screenshot flag dari soal 1.

![Flag_1](/Assets/Flag_1.png)

## Soal 2

## Soal 3

## Soal 4

## Soal 5

## Soal 6

## Soal 7

## Soal 8

## Soal 9

## Soal 10
