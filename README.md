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
Dalam soal diberikan sebuah file .zip dan file .pcap tetapi tidak ada data netcat untuk submit file. Oleh karena itu, hal yang dilakukan adalah melakukan analisis pada file .pcap dan melakukan follow TCP Stream. Lalu ditemukan pesan sebagai berikut dalam stream.

![4_TCP](/Assets/4_TCP.png)

Setelah kode didecode di https://www.base64decode.org/, maka password zip adalah = 5implePas5word. 

![4_Decode](/Assets/4_Decode.png)

File connect.txt di dalam .zip berisi command netcat.

![4_Connect](/Assets/4_Connect.png)

Selanjutnya kita perlu menjawab soal dari nc tersebut, untuk soal a, "Berapa banyak packet yang berhasil di capture dari file pcap tersebut?" jawabannya adalah 60.

![4_60](/Assets/4_60.png)

Untuk soal b, "Port berapakah pada server yang digunakan untuk service SMTP?" dapat dilihat di detail src packet yang menggunakan protocol SMTP

![4_SMTP](/Assets/4_SMTP.png)

Untuk soal c, "Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?" terdapat 2 buah IP dalam file tersebut karena ip yang melakukan komunikasi ada dua, 10.10.1.4 dan 74.53.140.153, dan ip yang berawalan 10 adalah ip private, maka jawabannya **74.53.140.153**.

Berikut adalah screenshot flag dari soal 4:

![Flag_4](/Assets/Flag_4.png)
 
## Soal 5

## Soal 6

## Soal 7

## Soal 8

## Soal 9

## Soal 10
