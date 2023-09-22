# Jarkom-Modul-1-E10-2023

## Identitas Kelompok E10 (Jaringan Komputer E)
| Name                 | NRP        |
| ---                  | ---        |
| Mavaldi Rizqy Hazdi  | 5025211086 |
| Mashita Dewi         | 5025211036 |

## Soal Nomor 1
User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.
- Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut?
- Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut?
- Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
- Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

### Jawaban Nomor 1
`a : 258040667` `b : 1044861039` `c : 1044861039` `d : 258040696`

### Screenshot Pengerjaan Nomor 1
- Langkah pertama dalam pengerjaan soal ini adalah melakukan sort pada packet-packet dalam wireshark sehingga yang memiliki protokol `FTP` akan lebih mudah untuk dicari.
- Command mengunggah file pada `FTP` adalah `STOR` sehingga, packet yang memiliki kata STOR pada infonya akan dicari dan didapatkan pada packet ke-147. Lalu cari bagian Sequence Number (raw) dan Acknowledgement number (raw) pada bagian info Transmission Control Protocol.
![1](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no1/Screenshot%20(70).png?raw=true)
- Untuk packet yang menunjukkan response terdapat pada packet ke-149 dan untuk mendapatkan Sequence Number (raw) dan Acknowledgement number (raw) dari packet ini dapat dilakukan seperti langkah diatas.
![2](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no1/Screenshot%20(71).png?raw=true)
![3](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no1/Screenshot%202023-09-18%20213233.png?raw=true)

## Soal Nomor 2
Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

### Jawaban Nomor 2
`gunicorn`

### Screenshot Pengerjaan Nomor 2
- Langkah pengerjaan soal ini adalah dengan mencari packet yang memiliki IP source atau IP destination `10.21.78.111`. Lalu lakukan Follow TCP Stream pada salah satu packet yang ditemukan. Nantinya akan ada bagian yang menyebutkan nama server.
![1](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no2/Screenshot%20(65).png?raw=true)
![2](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no2/Screenshot%202023-09-18%20212751.png?raw=true)

## Soal Nomor 3
Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:
- Berapa banyak paket yang tercapture dengan IP source maupun destination address 	adalah 239.255.255.250 dengan port 3702?
- Protokol layer transport apa yang digunakan?

### Jawaban Nomor 3
`a : 21` `b : UDP`

### Screenshot Pengerjaan Nomor 3
- Untuk menemukan banyaknya paket yang tercapture dengan IP source dan destination address 239.255.255.250 dengan port 3702 adalah dengan melakukan filter dengan query sebagai berikut : `(ip.src == 239.255.255.250 && udp.port == 3702) || (ip.dst == 239.255.255.250 && udp.port == 3702)`. Bagian `ip.src` akan melakukan pencarian pada paket yang memiliki source IP 239.255.255.250, pada bagian `ip.dst` akan melakukan pencarian pada paket yang destination IP nya adalah 239.255.255.250, dan bagian `udp.port` melakukan pencarian paket yang memiliki port 3702. Setelah melakukan filter hitung banyaknya paket yang masih tersisa setelah dilakukannya filter.
![1](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no3/Screenshot%20(66).png?raw=true)
- Untuk mencari protokol layer transport yang digunakan dapat dilihat pada info Internet Protocol Version dan terdapat pada bagian protocol.
![2](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no3/Screenshot%20(67).png?raw=true)
![3](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no3/Screenshot%202023-09-18%20212905.png?raw=true)

## Soal Nomor 4
Berapa nilai checksum yang didapat dari header pada paket nomor 130?

### Jawaban Nomor 4
`0x18e5`

### Screenshot Pengerjaan Nomor 4
- Untuk menemukan nilai checkcum pada paket no 130 adalah dengan mencari pada bagian info User Datagram Protocol, nanti akan ada bagian yang bernama checksum dan nilai checksum-nya akan berbentuk heksadesimal.
![1](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no4/Screenshot%20(69).png?raw=true)
![2](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no4/Screenshot%202023-09-18%20213129.png?raw=true)

## Soal Nomor 5
Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.
- Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
- Port berapakah pada server yang digunakan untuk service SMTP?
- Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

### Jawaban Nomor 5
`a : 60` `b : 25` `c : 74.53.140.153`

### Screenshot Pengerjaan Nomor 5
- Langkah pertama untuk mengerjakan soal no 5 adalah dengan mencari password untuk membuka file connect agar kita bisa mengumpulkan jawaban untuk no 5. Password untuk file connect akan ditemukan pada paket yang memiliki Follow TCP Stream tetapi file harus didecode menggunakan Base64. Bentuk awal password adalah seperti berikut `NWltcGxlUGFzNXdvcmQ=`.
![1](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no5/Screenshot%20(72).png?raw=true)
Untuk melakukan decode, masukkan command seperti berikut kedalam bash linux : `echo 'NWltcGxlUGFzNXdvcmQ=' | base64 --decode`. Setelah dijalankan, password nantinya akan menjadi `5implePas5word`.
- Banyak paket yang berhasil dicapture dari file pcap tersebut dapat dihitung dari total paket yang terdapat dalam file.
![2](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no5/Screenshot%20(74).png?raw=true)
- Untuk menemukan port pada server yang digunakan untuk service SMTP dapat dilihat pada salah satu paket yang memiliki protokol SMTP, lalu lihat pada bagian info Transmission Control Protocol dan akan ada bagian source port.
![3](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no5/Screenshot%20(73).png?raw=true)
- Untuk menemukan IP yang merupakan public IP dapat diseleksi masing-masing ip yang tercapture pada file. IP yang merupakan public IP adalah `74.53.140.153` karena `74.53.140.153` tidak termasuk dalam range IP private.
![4](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no5/Screenshot%202023-09-18%20213433.png?raw=true)

## Soal Nomor 6
Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

### Jawaban Nomor 6
`JDRNJA`

### Screenshot Pengerjaan Nomor 6
- Langkah pertama dalam proses ini adalah melakukan analisis awal pada soal. Perhatikan bahwa ada penggunaan huruf besar "S," "U," "B," "S," "T," "I," "T," "U," "S," "I," yang mengindikasikan bahwa kami akan melakukan operasi penggantian huruf. Penting untuk dicatat bahwa kita memiliki petunjuk a1, e5, dan u21. Dalam konteks ini, "a" mewakili huruf pertama, "e" adalah huruf kelima, dan "u" adalah huruf ke-21. Semua ini merupakan petunjuk penting dalam mengurai soal ini.
- Langkah kedua, kami akan mencari paket dengan urutan "7812". Dalam paket tersebut, kami dapat mengidentifikasi alamat IP sumber, yaitu 104.18.13.101. Gambar berikut ini memperlihatkan detail paket tersebut:
  
  ![Screenshot (73)](https://github.com/mashitaad/Jarkom-Modul-1-E10-2023/assets/87978863/12c0b4e0-3434-4611-a777-2cbaea79fe92)
- Dari informasi yang telah kami peroleh, alamat IP sumber adalah 104.18.13.101. Jika kita menghubungkan hal ini dengan operasi substitusi yang kami sebutkan sebelumnya, maka angka-angka dalam alamat sumber tersebut akan menghasilkan kata berikut: 10 4 18 13 10 1, yang dapat diartikan sebagai J D R N J A (10 adalah urutan untuk huruf J, 4 adalah urutan untuk huruf D, 18 adalah urutan untuk huruf R, 13 adalah urutan untuk huruf N, 1 adalah urutan untuk huruf A).
  
![Screenshot (74)](https://github.com/mashitaad/Jarkom-Modul-1-E10-2023/assets/87978863/73899346-f7fa-4a87-9f9f-2a80eec047f1)

## Soal Nomor 7
Berapa jumlah packet yang menuju IP 184.87.193.88?

### Jawaban Nomor 7
`6`

### Screenshot Pengerjaan Nomor 7
- Untuk mencari jumlah paket yang menuju IP 184.87.193.88 adalah dengan melakukan pencarian dengan filter `ip.dst == 184.87.193.88` yang akan hanya menangkap paket dengan destination IP 184.87.193.88.
- 
![1](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no7/Screenshot%20(68).png?raw=true)
![2](https://github.com/mavaldi/Image-Jarkom/blob/main/Praktikum%201/no7/Screenshot%202023-09-18%20213006.png?raw=true)

## Soal Nomor 8
Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

### Jawaban Nomor 8
`tcp.dstport == 80 || udp.dstport == 80`
- tcp.dstport == 80: Bagian pertama dari ekspresi ini mengacu pada protokol TCP dan nomor port tujuan (destination port number) yang sama dengan 80. 
- ||: Operator || digunakan untuk menghubungkan dua kondisi dengan operator "atau" (OR).
- udp.dstport == 80: Bagian kedua dari ekspresi ini mengacu pada protokol UDP dan nomor port tujuan yang sama dengan 80.

### Screenshot Pengumpulan Nomor 8
![image 1](https://github.com/mashitaad/Jarkom-Modul-1-E10-2023/assets/87978863/3b49729d-ca63-49e4-9605-4c0b8e0d1458)

## Soal Nomor 9
Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

### Jawaban Nomor 9
`ip.src == 10.51.40.1 && ip.dst != 10.39.55.34`
Ekspresi `ip.src == 10.51.40.1 && ip.dst != 10.39.55.34` dapat diuraikan sebagai berikut:
- `ip.src == 10.51.40.1`: Bagian pertama dari ekspresi ini merujuk pada alamat IP sumber (source IP address). Ini berarti ekspresi ini akan mengidentifikasi paket-paket yang berasal dari alamat IP 10.51.40.1.
- `ip.dst != 10.39.55.34`: Bagian kedua dari ekspresi ini merujuk pada alamat IP tujuan (destination IP address). Namun, dalam konteks ini, operator != digunakan, yang berarti "tidak sama dengan." Dengan kata lain, ekspresi ini akan memilih paket-paket yang memiliki alamat IP tujuan yang bukan 10.39.55.34. Jadi, ini akan mengkecualikan paket-paket yang menuju ke alamat tersebut dari seleksi.

### Screenshot Pengumpulan Nomor 9
![image 1](https://github.com/mashitaad/Jarkom-Modul-1-E10-2023/assets/87978863/3b49729d-ca63-49e4-9605-4c0b8e0d1458)

## Soal Nomor 10
Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet

### Jawaban Nomor 10
`dhafin:kesayangannyak0k0`

### Screenshot Pengerjaan Nomor 10
- Saat ini, langkah awal kami dalam proses penyaringan adalah mencari kata kunci telnet pada filter tampilan (display filter), yang akan menghasilkan tampilan seperti yang ditunjukkan pada gambar berikut:
  
  ![Screenshot (69)](https://github.com/mashitaad/Jarkom-Modul-1-E10-2023/assets/87978863/0a04b314-ab97-41da-9c31-1308ba59a983)

- Kemudian, kami melakukan penyortiran pada setiap paket satu per satu untuk mengidentifikasi username dan passwordnya. Kami fokus pada bagian dropdown yang berkaitan dengan telnet, seperti yang terlihat dalam gambar berikut:
  
  ![Screenshot (69)](https://github.com/mashitaad/Jarkom-Modul-1-E10-2023/assets/87978863/9ca28711-7a8a-4df2-99ec-342da610d088)

- Selanjutnya, kami berhasil menemukan username dan password yang relevan, seperti yang terlihat di bawah ini:
  
  ![Screenshot (67)](https://github.com/mashitaad/Jarkom-Modul-1-E10-2023/assets/87978863/0abf25a4-b4a9-4775-81f4-164a570b8a8f)

![image 221](https://github.com/mashitaad/Jarkom-Modul-1-E10-2023/assets/87978863/55c81b73-d622-4fe9-8219-47b99ebc2018)

## Kendala
- Pada saat praktikum berlangsung, kami menghadapi kesulitan dalam menyelesaikan nomor 6. Namun, kami berhasil menyelesaikannya dengan sukses saat sesi revisi berlangsung.
