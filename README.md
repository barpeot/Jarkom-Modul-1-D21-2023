# Jarkom-Modul-1-D21-2023

# Anggota Kelompok:
+ Akbar Putra Asenti Priyanto (5025211004)
+ Farrela Ranku Mahhissa (5025211129)

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
Kita diminta mencari jenis web server pada portal praktikum jaringan komputer, cara paling mudah adalah dengan melakukan inspect element dan melihat pada bagian 'Network', kemudian buka bagian 'Header'

![2_Addressing](/Assets/2_Addressing.jpg)


Berikut adalah screenshot flag dari soal 2.

![2_Addressing](/Assets/Flag_2.png)



## Soal 3
Dalam soal ini diberikan file .pcap dan diminta untuk mencari banyak packet yang tercapture dengan IP source maupun destintation address 239.255.255.250 port 3702 dan Protokol layer transport proses tersebut.

Pertama-tama buka display filter dan masukkan kueri ip.src == 239.255.255.250 or ip.dst == 239.255.255.250, maka akan ditemukan hasil seperti berikut:

![3_Filter](/Assets/3_Filter.png)

Selanjutnya sort berdasar protocol dan cari sebuah packet yang menggunakan port 3702, disini ditemukan packet 1758 kebawah menggunakan protocol UDP dan menggunakan port 3702.

![3_UDP](/Assets/3_UDP.png)

Untuk menghitung banyak packet yang menggunakan protocol tersebut dapat dicek di Protocol Hierarchy yang dapat diakses di **Statistics** >> **Protocol Hierarchy**. Kemudian hitung jumlah packet yang menggunakan protocol UDP, yaitu 21.

![3_Hierarchy](/Assets/3_Hierarchy_Stats.png)

Berikut adalah screenshot flag dari soal 3.

![Flag_3](/Assets/Flag_3.png)

## Soal 4
Untuk soal no 4. Kita hanya perlu melihat package nomor 130, kemudian klik 2x pada packagenya dan melihat ke bagian User Data Protocol. Dari sini kita akan dapat langsung melihat checksumnya.

![4_Addressing](/Assets/4_Addressing.jpg)

Berikut adalah screenshot flag dari soal 4.

![Flag_4](/Assets/Flag_4.png)


## Soal 5
Dalam soal diberikan sebuah file .zip dan file .pcap tetapi tidak ada data netcat untuk submit file. Oleh karena itu, hal yang dilakukan adalah melakukan analisis pada file .pcap dan melakukan follow TCP Stream. Lalu ditemukan pesan sebagai berikut dalam stream.

![5_TCP](/Assets/5_TCP.png)

Setelah kode didecode di https://www.base64decode.org/, maka password zip adalah = 5implePas5word. 

![5_Decode](/Assets/5_Decode.png)

File connect.txt di dalam .zip berisi command netcat.

![5_Connect](/Assets/5_Connect.png)

Selanjutnya kita perlu menjawab soal dari nc tersebut, untuk soal a, "Berapa banyak packet yang berhasil di capture dari file pcap tersebut?" jawabannya adalah 60.

![5_60](/Assets/5_60.png)

Untuk soal b, "Port berapakah pada server yang digunakan untuk service SMTP?" dapat dilihat di detail src packet yang menggunakan protocol SMTP

![5_SMTP](/Assets/5_SMTP.png)

Untuk soal c, "Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?" terdapat 2 buah IP dalam file tersebut karena ip yang melakukan komunikasi ada dua, 10.10.1.4 dan 74.53.140.153, dan ip yang berawalan 10 adalah ip private, maka jawabannya **74.53.140.153**.

Berikut adalah screenshot flag dari soal 4:

![Flag_5](/Assets/Flag_5.png)
 
## Soal 6
Dalam soal kita diminta untuk membantu Slamet dalam menyelesaikan permasalahannya. Sesuai dengan soal, maka pertama kita pergi ke package nomor 7812, kemudian kita lihat source address nya.

![6_Source](/Assets/6_Source.jpg)

Kita dapatkan source addressnya adalah

```104.18.14.101```

Selanjutnya, kita bisa lihat bahwa pembuat soal menuliskan soal dengan membuat ada beberapa huruf yang tidak sesuai EYD, yakni dibuat kapital pada beberapa tempat yang tidak seharusnya
```
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.
```
Bila kita urutkan, maka akan kita dapatkan
```
SUBSTITUSI
```
Kemudian, dengan menggabungkan clue dari hasil pencarian google yang hanya menampilkan a1 e5 u21 yang menunjukkan bahwa ini merupakan kode chiper a1z26, maka kita ubah
```
104.18.14.101
menjadi
10 4 18 14 10 1
```
lalu kita decode menggunakan website tersendiri.

![6_Decode](/Assets/6_Decode.jpg)

Hasil jawabannya adalah 
```
JDRNJA
```

Berikut adalah screenshot flag dari soal 6:

![Flag_6](/Assets/Flag_6.jpeg)

## Soal 7
Dalam soal kita diminta untuk mencari tahu berapa jumlah packet yang menuju IP 184.87.193.88 di dalam file .pcap yang diberikan. Maka kita hanya perlu memberi display filter "ip.dst == 184.87.193.88".

![7_Filter](/Assets/7_Filter.png)

Berikut adalah screenshot flag dari soal 7:

![Flag_7](/Assets/Flag_7.png)

## Soal 8
Kita bisa melihat pada file .pcap nya, bahwa da 3 protokol yang tercapture, yakni ARP, TCP, dan UDP. Karena ARP tidak menggunakan port, maka yang menggunakan port 80 kemungkinan adalah TCP dan UDP. Sehingga kita masukkan kueri di bawah
```
tcp.dstport == 80 || udp.dstport == 80
```
![8_Filter](/Assets/8_Filter.jpg)

Berikut adalah screenshot flag dari soal 8:

![Flag_8](/Assets/Flag_8.png)

## Soal 9
Kita diminta mencari paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34. Dengan menggunakan kueri ip.src digabungkan dengan ip.dst menggunakan operator '&&', maka kita bisa menemukannya.
```
ip.src == 10.51.40.1 && ip.dst != 10.39.55.34
```

![9_Filter](/Assets/9_Filter.jpg)

Berikut adalah screenshot flag dari soal 9:

![Flag_9](/Assets/Flag_9.png)

## Soal 10
Dalam soal ini kita diminta untuk mencari kredensial login yang benar ketika user login menggunakan telnet. Untuk mengetahui hal tersebut perlu dilakukan follow TCP Stream pada packet TELNET.

![10_TCP](/Assets/10_TCP.png)

Kemudian ditemukan attempt login yang berhasil pada stream ke-15. Disini kita dapat melihat password yang benar adalah **kesayangannyak0k0**, maka kita perlu mencari attempt login yang sesuai dengan password tersebut.

![10_Kredensial](/Assets/10_Kredensial.png)

Pada stream ke-2 ditemukan attempt sedemikian dimana passwordnya telah sesuai dengan attempt login yang benar. Maka jawaban dari soal ini adalah **dhafin:kesayangannyak0k0**

Berikut adalah screenshot flag dari soal 10:

![Flag_7](/Assets/Flag_10.png)
