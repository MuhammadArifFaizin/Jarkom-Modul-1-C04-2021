# Praktikum Modul 1 Jaringan Komputer

Kelompok : C4

Anggota Kelompok :

- Muhammad Arif Faizin (05111940000060)
- Aufi Fillah (05111940000148)
- Abiya Sabitta Ragadani (05111940000166)

## No 1

Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

Pada soal ini diminta untuk mencari webserver yang digunakan oleh website "ichimarumaru.tech" menggunakan wireshark. Sehingga untuk mencari webserver dicari dulu paket yang berasal dari website tersebut. Cara mencarinya menggunakan display filter `http.host eq "ichimarumaru.tech"`. Jika difilter maka akan menunjukan hasil sebagai berikut
![Gambar No 1](/images/soal1.png)
Kemudian untuk mencari servernya caranya klik kanan kemudian follow -> http stream. Kemudian akan mendapat dialog box seperti berikut
![Gambar No 1-2](/images/soal1-2.jpg)

Bisa dilihat dari gambar tersebut server yang digunakan oleh web tersebut adalah nginx/1.18.0 (Ubuntu)

## No 2

Temukan paket dari web-web yang menggunakan basic authentication method!

Pada soal ini diminta untuk mencari paket dari web yang menggunakan authentication basic. Maka dari itu untuk mencari paket tersebut digunakan display filter `http.authbasic`. Hasilnya akan terlihat sebagai berikut.
![Gambar No 2](/images/soal2.png)

## No 3

Ikuti perintah di basic.ichimarumaru.tech! `Username` dan `password` bisa didapatkan dari file .pcapng!

Pada soal nomor 3 diminta untuk login ke website basic.ichimarumaru.tech, kemudian untuk mencari `Username` dan `password` bisa didapatkan dari file .pcapng nya. Untuk mencari username dan password tersebut maka digunakan display filter `http.authbasic` untuk mencari paket yang memiliki authenticator, tetapi bisa juga ditambahkan display filter `http.host eq "basic.ichimarumaru.tech"` untuk menambah filter paket yang berasal dari website tersebut. Menggunakan yang manapun memberikan hasil filter sebagai berikut.
![Gambar No 3](/images/soal3.png)
Dari hasil tersebtu bisa dilihat authorization terdapat credentials yang berisi username dan password. Didapat credentialsnya sebagai berikut `kuncimenujulautan:tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN`. Sehingga untuk `Username`nya adalah `kuncimenujulautan` dan `password` adalah `tQKEJFbgNGC1NCZlWAOjhyCOm6o3xEbPkJhTciZN`. Setelah login akan mendapatkan halaman web sebagai berikut, dan diminta untuk menyebutkan urutan kabel T568A
![Gambar No 3-2](/images/soal3-2.png)

Untuk urutan kabel T568A adalah
1. Hijau - Putih
2. Hijau
3. Orange - Putih
4. Biru
5. Biru - Putih
6. Orange
7. Cokelat - Putih
8. Cokelat

## No 4

Temukan paket mysql yang mengandung perintah query select!

Pada soal ini diminta untuk mencari paket mysql yang mengandung perintah query select. Hal tersebut bisa didapatkan dari display filter `mysql.query contains "select"`. Jika dijalankan maka akan terlihat seperti berikut
![Gambar No 4](/images/soal4.png)

## No 5

Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! `Username` dan `password` bisa didapat dari query insert pada table users dari file .pcap!

Pada soal ini diminta untuk login ke portal.ichimarumaru.tech dan untuk mendapatkan username dan password bisa didapat dari paket mysql yang mengandung insert. Untuk mencari username dan password maka menggunakan display filter `mysql.query contains "INSERT"`. Maka akan didapatkan sebagai berikut
![Gambar No 5](/images/soal5.png)

Kemudian setelah mendapatkan username dan password dimana username adalah `akakanomi` dan passwordnya `pemisah4lautan` akan mendapat page website sebagai berikut, dan diminta untuk menuliskan urutan kabel T568B
![Gambar No 5-2](/images/soal5-2.png)

Untuk urutan kabel T568B adalah sebagai berikut.
1. Orange - Putih
2. Orange
3. Hijau - Putih
4. Biru
5. Biru - Putih
6. Hijau
7. Cokelat - Putih
8. Cokelat

## No 6

Cari `username` dan `password` ketika melakukan login ke FTP Server!

Pada soal ini, diminta untuk mencari `username` dan `password` ketika melakukan login ke FTP server. Protokol FTP menggunakan command `USER` untuk mengirimkan `username`, dan command `PASS` untuk mengirimkan `password`. Sehingga kita dapat menggunakan display filter `ftp.request.command == USER || ftp.request.command == PASS` untuk menemukan request tersebut.

![Gambar No 6](/images/soal6.png)

Dari gambar tersebut terlihat jika isi dari request body commandnya jika `username`nya adalah `secretuser` dan `password`nya adalah `aku.pengen.pw.aja`.

## No 7

Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

Pada soal ini, diminta untuk mencari file PDF dengan nama file `Real.pdf` dalam sebuah file ZIP diantara 500 file ZIP.

Untuk mencarinya, kita perlu menggunakan display filter `ftp-data contains "Real.pdf"` untuk menemukan data FTP yang memiliki konten berupa nama file PDF `"Real.pdf"` seperti gambar di bawah. 

![Gambar No 7](/images/soal7.png)

Kemudian pilih packet tersebut, lalu klik kanan, pilih `Follow`, pilih `TCP Stream`. Kemudian akan muncul jendela baru, ubah `Show data as` menjadi `Raw` seperti gambar di bawah. 

![Gambar No 7 2](/images/soal7-2.png)

Kemudian pilih `save as...` dan simpan sebagai `Real.pdf`. Setelah dibuka, isi dari file PDF tersebut seperti gambar berikut.

![Gambar No 7 3](/images/soal7-3.png)

## No 8

Cari paket yang menunjukan pengambilan file dari FTP tersebut!

Pada soal ini, kita diminta untuk menampilkan paket yang menunjukkan adanya pengambilan file / download dari FTP yang tersedia.

Seperti yang kita tahu pada modul pertama, ada beberapa command pada paket seperti `SOTR` yang berarti upload / menaruh file dalam FTP, dan `RETR` yang berarti sebaliknya. Maka dari itu untuk menjawab soal ini, kita perlu menjalankan filter `ftp.request.command == "RETR"`, dengan hasil sebagai berikut 

![Gambar No 8](/images/soal8.png)

## No 9

Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

Pada soal ini, kita diminta untuk mencari file bernama `secret.zip` dan mendownloadnya.

Untuk melakukannya, kita pertama harus mencari paket dimana file tersebut berada, dan untuk mempermudah pencarian, kita akan menggunakan filter `ftp-data.command contains "secret.zip"` dan didapat hasil sebagai berikut :

![Gambar No 9](/images/soal9.png)

Setelah menemukan paket yang berisi file `secret.zip` tersebut, untuk mendownloadnya kita lakukan klik kanan pada paket, lalu klik `follow`, lalu `TCP stream`. Setelah muncul windows baru kita ubah `show data as` menjadi `raw`. Lalu, klik `save as`

![Gambar No 9 2](/images/soal9-2.png)

Setelah itu kita melakukan `save as` dan menyimpannya dengan nama `secret.zip`. Ketika dibuka akan seperti ini :

![Gambar No 9 3](/images/soal9-3.png)

## No 10

Selain itu terdapat `"history.txt"` yang kemungkinan berisi history bash server tersebut! Gunakan isi dari `"history.txt"` untuk menemukan `password` untuk membuka file rahasia yang ada di `"secret.zip"`!

Pada soal ini, kita diminta mencari tahu isi dari file `history.txt` untuk membuka file yang ada di dalam file `secret.zip`, kemudian membuka file tersebut.

Untuk itu, kita dapat mencari file `"history.txt"` dengan menggunakan display filter `ftp-data.command contains "history.txt"`. Kemudian kami menemukan sebuah packet seperti gambar berikut

![Gambar No 10](/images/soal10.png)

Untuk mengetahui isinya, kita harus mengikut `TCP Stream`nya, yaitu dengan cara klik kanan, kemudian pilih `Follow`, lalu pilih `TCP Stream`. Kemudian akan muncul jendela baru seperti gambar berikut 

![Gambar No 10 2](/images/soal10-2.png)

Dari gambar tersebut, diketahui jika terdapat file `bukanapapa.txt` yang menjadi key dari file.

Oleh karena itu, kita harus mencari file `"bukanapaapa.txt"` dengan menggunakan display filter `ftp-data.command contains "bukanapaapa.txt"`. Kemudian kami menemukan sebuah packet seperti gambar berikut

![Gambar No 10 3](/images/soal10-3.png)

Lalu seperti sebelumnya, untuk mengetahui isinya, kita harus mengikut `TCP Stream`nya, yaitu dengan cara klik kanan, kemudian pilih `Follow`, lalu pilih `TCP Stream`. Kemudian akan muncul jendela baru seperti gambar berikut 

![Gambar No 10 4](/images/soal10-4.png)

Dari gambar tersebut, kita mendapatkan `password` untuk membuka file rahasia yang ada di file `"secret.zip"`.

![Gambar No 10 5](/images/soal10-5.png)

Setelah itu, file PDF berhasil dibuka dan hasilnya adalah seperti berikut

![Gambar No 10 6](/images/soal10-6.png)

## No 11

Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

Dari soal tersebut, kita diminta untuk memfilter hasil tangkapan Wireshark hanya untuk packet yang berasal dari port 80.

### Capture Filter
Untuk menggunakan capture filter, filter yang digunakan adalah `src port 80`. Berikut tampilannya

![Gambar No 11](/images/soal11.png)

### Display Filter
Untuk menggunakan display filter, filter yang digunakan adalah `tcp.srcport == 80 || udp.srcport == 80`

![Gambar No 11 2](/images/soal11-2.png)

## No 12

Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

Dari soal tersebut, kita diminta untuk memfilter hasil tangkapan Wireshark hanya untuk packet yang mengandung port 21.

### Capture Filter
Untuk menggunakan capture filter, filter yang digunakan adalah `port 21`. Berikut tampilannya

![Gambar No 12](/images/soal12.png)

### Display Filter
Untuk menggunakan display filter, filter yang digunakan adalah `tcp.port == 21 || udp.port == 21`

![Gambar No 12 2](/images/soal12-2.png)

## No 13

Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

Dari soal tersebut, kita diminta untuk memfilter packet dengan port 443.

### Capture Filter
Filter yang digunakan untuk capture filter adalah `port 443`. dihasilkan :

![Gambar No 13](/images/soal13.png)

### Display Filter
Filter yang digunakan untuk display filter adalah `tcp.dstport == 443 || udp.dstport == 443`

![Gambar No 13 2](/images/soal13-2.png)

## No 14

Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

Dari soal tersebut, kita diminta untuk mengambil paket yang bertujuan ke `kemenag.go.id`.

### Capture Filter
Filter yang digunakan untuk capture filter adalah `dst host kemenag.go.id`. dihasilkan :

![Gambar No 14](/images/soal14.png)


## No 15

Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!

Dari soal tersebut, kita diminta untuk mengambil paket yang berasal dari IP komputer.

Untuk itu, pertama kita mencari ip kita sendiri dengan membuka `CMD` dan mengetikkan `ipconfig` dan enter. Kita akan mengambil alamat ip pada baris yang bertuliskan `ipv4` dan didapatkan :

![Gambar No 15](/images/soal15.png)

Setelah itu, kita akan mencoba mencari pake menggunakan ip yang sudah dicari menggunakan `ip.src==192.168.1.101`

![Gambar No 15 2](/images/soal15-2.png)

## Kenadala yang Dialami
Kendala yang dialami adalah untuk nomor 14, dimana menggunakan capture filter `dst host kemenag.go.id` sempat tidak tertangkap sama sekali paketnya.
