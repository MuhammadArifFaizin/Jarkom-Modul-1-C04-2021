# Praktikum Modul 1 Jaringan Komputer

Kelompok : C4

Anggota Kelompok :

- Muhammad Arif Faizin (05111940000060)
- Aufi Fillah (05111940000148)
- Abiya Sabitta Ragadani (05111940000166)

## No 1

Sebutkan webserver yang digunakan pada "ichimarumaru.tech"!

## No 2

Temukan paket dari web-web yang menggunakan basic authentication method!

## No 3

Ikuti perintah di basic.ichimarumaru.tech! `Username` dan `password` bisa didapatkan dari file .pcapng!

## No 4

Temukan paket mysql yang mengandung perintah query select!

## No 5

Login ke portal.ichimarumaru.tech kemudian ikuti perintahnya! `Username` dan `password` bisa didapat dari query insert pada table users dari file .pcap!

## No 6

Cari `username` dan `password` ketika melakukan login ke FTP Server!

Pada soal ini, diminta untuk mencari `username` dan `password` ketika melakukan login ke FTP server. Protokol FTP menggunakan command `USER` untuk mengirimkan `username`, dan command `PASS` untuk mengirimkan `password`. Sehingga kita dapat menggunakan display filter `ftp.request.command == USER || ftp.request.command == PASS` untuk menemukan request tersebut.

![Gambar No 6](/images/soal6.png)

Dari gambar tersebut terlihat jika isi dari request body commandnya jika `username`nya adalah `secretuser` dan `password`nya adalah `aku.pengen.pw.aja`.

## No 7

Ada 500 file zip yang disimpan ke FTP Server dengan nama 0.zip, 1.zip, 2.zip, ..., 499.zip. Simpan dan Buka file pdf tersebut. (Hint = nama pdf-nya "Real.pdf")

## No 8

Cari paket yang menunjukan pengambilan file dari FTP tersebut!

## No 9

Dari paket-paket yang menuju FTP terdapat inidkasi penyimpanan beberapa file. Salah satunya adalah sebuah file berisi data rahasia dengan nama "secret.zip". Simpan dan buka file tersebut!

## No 10

Selain itu terdapat "history.txt" yang kemungkinan berisi history bash server tersebut! Gunakan isi dari "history.txt" untuk menemukan `password` untuk membuka file rahasia yang ada di "secret.zip"!

## No 11

Filter sehingga wireshark hanya mengambil paket yang berasal dari port 80!

## No 12

Filter sehingga wireshark hanya mengambil paket yang mengandung port 21!

## No 13

Filter sehingga wireshark hanya menampilkan paket yang menuju port 443!

## No 14

Filter sehingga wireshark hanya mengambil paket yang tujuannya ke kemenag.go.id!

## No 15

Filter sehingga wireshark hanya mengambil paket yang berasal dari ip kalian!
