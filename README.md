# Jarkom-Modul-1-D10-2023
### Muhammad Rafi Insan Fillah (5025211169)
### Ken Anargya Alkausar (5025211168)

## 1. User melakukan berbagai aktivitas dengan menggunakan protokol FTP. Salah satunya adalah mengunggah suatu file.

### a. Berapakah sequence number (raw) pada packet yang menunjukkan aktivitas tersebut? 

Langkah pertama yang perlu dilakukan untuk mendapat paket yang dimaksud adalah dengan display filter `ftp.request.command == STOR`. Syntax tersebut akan memfilter protokol FTP yang mungkin digunakan untuk upload file. Command yang difilter adalah command STOR yang digunakan untuk upload file ke FTP server.

Hasil menunjukkan sebuah paket dengan info request: STOR. Pada paket tersebut dapat dilihat raw sequence numbernya adalah **258040667**.
### b. Berapakah acknowledge number (raw) pada packet yang menunjukkan aktivitas tersebut? 

Langkah menemukan paket bersangkutan sama persis dengan poin a namun yang dilihat adalah raw acknowledge number paket tersebut adalah **1044861039**.
### c. Berapakah sequence number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

Untuk mendapatkan paket yang menunjukkan response dari aktivitas bersangkutan adalah dengan filter `ftp.response.arg contains "zip"`. Filter tersebut akan menunjukkan paket yang mengandung string `zip` di informasi paketnya.

Hasil menunjukkan satu paket dan jika dilihat raw sequence numbernya adalah **1044861039**.

### d. Berapakah acknowledge number (raw) pada packet yang menunjukkan response dari aktivitas tersebut?

Langkah menemukan paket bersangkutan sama persis dengan poin c namun yang dilihat adalah raw acknowledge number paket tersebut adalah **258040696***.

## 2. Sebutkan web server yang digunakan pada portal praktikum Jaringan Komputer!

Untuk mendapatkan informasi web server dari portal praktikum jarkom langkah pertama adalah dengan filter display paket dengan protokol http karena http adalah protokol yang menghubungkan perangkat dengan web. Setelah itu dapat kita pilih salah satu paket dengan http protokol dan follow http stream paket tersebut.

Hasil menunjukkan salah satu baris pada http stream tersebut terdapat nama web servernya adalah **gunicorn**.

## 3. Dapin sedang belajar analisis jaringan. Bantulah Dapin untuk mengerjakan soal berikut:

### a. Berapa banyak paket yang tercapture dengan IP source maupun destination address adalah 239.255.255.250 dengan port 3702?

Untuk mendapatkan paket-paket dengan port 3702 maka kita cek terlebih dahulu protokol-protokol yang ada pada capture tersebut. Setelah difilter protokol UDP lah yang terdapat paket dengan port 3702. Lalu difilter berdasarkan ip.src dan ip.dst, sehingga didapat syntax filter `(ip.src == 239.255.255.250 or ip.dst == 239.255.255.250) and udp.port==3702`.

Hasil menunjukkan terdapat **21 paket** dengan filter tersebut.


### b. Protokol layer transport apa yang digunakan?
Untuk mendapatkan paket-paket dengan ketentuan soal, syntax filter yang digunakan sama dengan poin b.

Hasil menunjukkan terdapat protokol yang digunakan adalah **UDP**.

## 4. Berapa nilai checksum yang didapat dari header pada paket nomor 130?

Untuk mendapat paket dengan nomor 130 kita dapat scroll down hingga ke paket 130 atau dengan filter `frame.number == 130`.

Hasil menunjukkan 1 paket dengan informasi UDP checksum **0x18e5**.

## 5. Elshe menemukan suatu file packet capture yang menarik. Bantulah Elshe untuk menganalisis file packet capture tersebut.

Langkah pertama yang dilakukan adalah analisa capture file agar mendapat password zip file yang tertera. Oleh karena itu kita coba filter by string "zip" dengan `tcp contains "zip"`.

Hasil menunjukkan 1 paket dan jika kita follwo TCP stream ditemukan sebuah bagian yang menunjukkan password zip file yang terencode Base64 **"NWltcGxlUGFzNXdvcmQ="**. Jika kita decode akan menghasilkan **"5implePas5word"** sehingga kita mendapat kode nc untuk soal nomor 5 ini.
### a. Berapa banyak packet yang berhasil di capture dari file pcap tersebut?

Untuk mendapat banyak paket yang tercapture sederhananya dapat kita scroll down sehingga muncul nomor paket terakhir yaitu **60**.
### b. Port berapakah pada server yang digunakan untuk service SMTP?

Protokol SMTP by default menggunakan port **25**, sebagai bukti contoh 1 paket terdapat detail portnya adalah 25.


### c. Dari semua alamat IP yang tercapture, IP berapakah yang merupakan public IP?

Ciri dari IP private adalah dengan awalan "10.", oleh karena itu jika kita ingin mendapat IP public maka kita ambil contoh dengan filter IP dst dengan `!(ip.dst_host == "10.")`.

Hasil menunjukkan 1 jenis IP dest yaitu **74.53.140.153**
