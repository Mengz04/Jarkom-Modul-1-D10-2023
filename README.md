# Jarkom-Modul-1-D10-2023
### Muhammad Rafi Insan Fillah (5025211169)
### Ken Anargya Alkausar (5025211168)

## 1. User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.

### a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 

Langkah pertama yang perlu dilakukan untuk mendapat paket yang dimaksud adalah dengan display filter `ftp.request.command == STOR`. Syntax tersebut akan memfilter protokol FTP yang mungkin digunakan untuk upload file. Command yang difilter adalah command STOR yang digunakan untuk upload file ke FTP server.
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/22ad9d41-94db-4cdd-8f95-76d612275375)

Hasil menunjukkan sebuah paket dengan info request: STOR. Pada paket tersebut dapat dilihat raw sequence numbernya adalah **258040667**.
### b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/f884158e-3392-4a36-a6d4-b97bddb425cd)

Langkah menemukan paket bersangkutan sama persis dengan poin a namun yang dilihat adalah raw acknowledge number paket tersebut adalah **1044861039**.
### c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

Untuk mendapatkan paket yang menunjukkan response dari aktivitas bersangkutan adalah dengan filter `ftp.response.arg contains "zip"`. Filter tersebut akan menunjukkan paket yang mengandung string `zip` di informasi paketnya.
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/065f1f81-c295-49a7-82cd-06f57c8c9542)

Hasil menunjukkan satu paket dan jika dilihat raw sequence numbernya adalah **1044861039**.

### d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/4a68f483-2e1f-4b40-837b-a678f01d81b8)

Langkah menemukan paket bersangkutan sama persis dengan poin c namun yang dilihat adalah raw acknowledge number paket tersebut adalah **258040696***.

### Dokumentasi Terminal
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/72e7d060-a5b1-480d-86a5-16cc8c398e94)

## 2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

Untuk mendapatkan informasi web server dari portal praktikum jarkom langkah pertama adalah dengan filter display paket dengan protokol http karena http adalah protokol yang menghubungkan perangkat dengan web. Setelah itu dapat kita pilih salah satu paket dengan http protokol dan follow http stream paket tersebut.
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/c7723bf3-b903-4ce4-9393-7744fcdfdf42)

![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/f79e9bea-8ba7-4f31-8dd5-1a7dbac90e0f)

Hasil menunjukkan salah satu baris pada http stream tersebut terdapat nama web servernya adalah **gunicorn**.
### Dokumentasi terminal

![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/abe4b807-9049-4a51-be5d-1f28a900802b)

## 3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

### a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

Untuk mendapatkan paket-paket dengan port 3702 maka kita cek terlebih dahulu protokol-protokol yang ada pada capture tersebut. Setelah difilter protokol UDP lah yang terdapat paket dengan port 3702. Lalu difilter berdasarkan ip.src dan ip.dst, sehingga didapat syntax filter `(ip.src == 239.255.255.250 or ip.dst == 239.255.255.250) and udp.port==3702`.
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/0cb941b8-d2c3-4ddb-952f-83146da1f0ec)

Hasil menunjukkan terdapat **21 paket** dengan filter tersebut.

### b. Protokol layer transport apa yang digunakan?
Untuk mendapatkan paket-paket dengan ketentuan soal, syntax filter yang digunakan sama dengan poin b.
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/fde546b4-5a14-43c9-9f29-cb831f2b0f58)

Hasil menunjukkan terdapat protokol yang digunakan adalah **UDP**.

### Dokumentasi terminal
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/eba08237-1511-4c9c-93d2-74186328fd88)


## 4. Berapa nilai checksum yang didapat dari header pada paket nomor 130?

Untuk mendapat paket dengan nomor 130 kita dapat scroll down hingga ke paket 130 atau dengan filter `frame.number == 130`.
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/47c3f0be-bc0a-41f9-9f59-b791e8ae7bb9)

Hasil menunjukkan 1 paket dengan informasi UDP checksum **0x18e5**.

### Dokumentasi terminal
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/d556b1f2-10fb-4473-a6ce-0742e2c14e35)

## 5. Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.

Langkah pertama yang dilakukan adalah analisa capture file agar mendapat password zip file yang tertera. Oleh karena itu kita coba filter by string "zip" dengan `tcp contains "zip"`.
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/2e1da85e-8a76-438b-8ba3-6ab7f4a516fb)

![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/73bdb6a4-5939-4151-bf79-dbb416729a8c)

Hasil menunjukkan 1 paket dan jika kita follwo TCP stream ditemukan sebuah bagian yang menunjukkan password zip file yang terencode Base64 **"NWltcGxlUGFzNXdvcmQ="**. Jika kita decode akan menghasilkan **"5implePas5word"** sehingga kita mendapat kode nc untuk soal nomor 5 ini.
### a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/bd0817f7-03fd-4ac4-aafb-3041b797a295)

Untuk mendapat banyak paket yang tercapture sederhananya dapat kita scroll down sehingga muncul nomor paket terakhir yaitu **60**.
### b. Port berapakah pada server yang digunakan untuk service SMTP?
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/8acd1d8c-f943-4809-b43b-df029387da69)

Protokol SMTP by default menggunakan port **25**, sebagai bukti contoh 1 paket terdapat detail portnya adalah 25.

### c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

Ciri dari IP private adalah dengan awalan "10.", oleh karena itu jika kita ingin mendapat IP public maka kita ambil contoh dengan filter IP dst dengan `!(ip.dst_host == "10.")`.

![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/2d8485c5-bb34-47e9-a1c3-d5317715c2f0)

Hasil menunjukkan 1 jenis IP dest yaitu **74.53.140.153**

### Dokumentasi terminal
![image](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/78022264/fb9ff7f0-16c5-4c67-b3d8-51540c59c4ba)

## 6. Seorang anak bernama Udin Berteman dengan SlameT yang merupakan seorang penggemar film detektif. sebagai teman yang baik, Ia selalu mengajak slamet untuk bermain valoranT bersama. suatu malam, terjadi sebuah hal yang tak terdUga. ketika udin mereka membuka game tersebut, laptop udin menunjukkan sebuah field text dan Sebuah kode Invalid bertuliskan "server SOURCE ADDRESS 7812 is invalid". ketika ditelusuri di google, hasil pencarian hanya menampilkan a1 e5 u21. jiwa detektif slamet pun bergejolak. bantulah udin dan slamet untuk menemukan solusi kode error tersebut.

Terdapat kode "server SOURCE ADDRESS 7812 is invalid", maka hal pertama yang saya cari adalah mencari nomor ke 7812 dengan filter frame.number==7812

![Screenshot 2023-09-18 192713](https://github.com/Mengz04/Jarkom-Modul-1-D10-2023/assets/92387421/b61e47d1-6443-4581-acb4-8ca281a83529)

kemudian didapat ip source **104.18.14.101** dan diubah sesuai cipher yang digunakan yaitu a1z26 kemudian **104.18.14.101** diubah ke abjad menjadi 10 4 = JD, 18 = R, 14 = N, 10 1 = JA

## 7. Berapa jumlah packet yang menuju IP 184.87.193.88?

untuk mendapatkan jumlah packet yang menuju 184.87.193.88 digunakan filter **ip.dst == 184.87.193.88**

![Screenshot 2023-09-18 192713](https://github.com/dagdo03/Word_Ladder/assets/92387421/66a2d3d0-6e4a-446c-a5b9-7d7cf19493a3)

### Dokumentasi terminal
![Screenshot 2023-09-18 192443](https://github.com/dagdo03/Word_Ladder/assets/92387421/4618fc6d-1e0d-4fff-9b6e-c0cf2e23d16d)

## 8. Berikan kueri filter sehingga wireshark hanya mengambil semua protokol paket yang menuju port 80! (Jika terdapat lebih dari 1 port, maka urutkan sesuai dengan abjad)

untuk mengambil semua protokol paket yang menuju port 80 digunakan kueri filter **tcp.dstport == 80 || udp.dstport == 80**

![Screenshot 2023-09-18 202549](https://github.com/dagdo03/Word_Ladder/assets/92387421/b5593ed6-c2cd-4109-8b37-f3efe0ff30e6)

Kegunaan filter ini untuk menampilkan semua paket yang memiliki port tujuan (destination port) 80 pada protokol TCP atau UDP

### Dokumentasi terminal
![Screenshot 2023-09-18 202357](https://github.com/dagdo03/Word_Ladder/assets/92387421/267bb40c-d149-4a1d-979b-d31cac720bee)

## 9. Berikan kueri filter sehingga wireshark hanya mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34!

untuk mengambil paket yang berasal dari alamat 10.51.40.1 tetapi tidak menuju ke alamat 10.39.55.34 digunakan filter **ip.src == 10.51.40.1 && ip.dst != 10.39.55.34

![Screenshot 2023-09-18 201840](https://github.com/dagdo03/Word_Ladder/assets/92387421/fb103ecc-0184-4c8a-ae2b-4be7b46d183a)

Filter ini akan menampilkan semua paket yang memiliki alamat sumber (source address) 10.51.40.1 dan alamat tujuan (destination address) bukan 10.39.55.34

### Dokumentasi terminal
![Screenshot 2023-09-18 201613](https://github.com/dagdo03/Word_Ladder/assets/92387421/34241e67-701f-4b1c-acfd-4e6d93c2b678)

## 10. Sebutkan kredensial yang benar ketika user mencoba login menggunakan Telnet
cara yang saya lakukan adalah menggunakan filter **telnet** agar protocol yang ditampilkan hanyalah telnet kemudian klik kanan pada salah satu frame dan klik follow -> TCP Stream kemudian temukan kredensial yang tepat.

![Screenshot 2023-09-18 203902](https://github.com/dagdo03/Word_Ladder/assets/92387421/fd1f50b8-f62b-42d8-b852-952e9c93946b)

### Dokumentasi terminal
![Screenshot 2023-09-18 203819](https://github.com/dagdo03/Word_Ladder/assets/92387421/92974b75-7a02-425e-a095-53b89376f655)

