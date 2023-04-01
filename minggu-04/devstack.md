[ [<<Kembali] ](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ac8862185f3ee378a4cbf8e0d5d4609b49b0834a/minggu-04/README.md)
# Penerapan OpenStack di Ubuntu 22.04 dengan DevStack
## Langkah 1: Perbarui Sistem Ubuntu
- Open terminal Ubuntu, lalu ketikkan kode dibawah ini
![gb1]()

- Nyalakan ulang setelah proses update
![gb2]()

## Langkah 2: Tambahkan User Stack
- Jalankan perintah dibawah ini untuk membuat user penerapan DevStack
![gb3]()
- Aktifkan hak istimewa sudo untuk user ini supaya tidak memerlukan password
![gb4]()
- Pindah ke user stack untuk menguji apakan berhasil terbuat atau belum
![gb5]()

## Langkah 3: Download DevStack
- Melakukan cloning DevStack dari GitHub
![gb6]()
- Buat file local.conf lalu isikan 4 password dan alamat ip Host dengan menambahkan kode seperti gambar dibawah ini
![gb7]()

## Langkah 4: Mulai Penerapan OpenStack di Ubuntu 22.04 dengan DevStack
- Setelah proses konfigurasi berhasil, selanjutnya yaitu melakukan penginstallan OpenStack dengan mengetikkan kode berikut
![gb8]()
- Diakhir proses installasi, jika berhasil menghasilkan output seperti gambar dibawah ini, maka proses installasi telah berhasil
![gb9]()

## Langkah 5: Akses Dashboard OpenStack
- Salin URL Horizon yang dihasilkan pada hasil installasi lalu tempelkan ke browser web
![gb10]()
- Gunakkan user default **demo atau admin** dan password yang dikonfigurasi untuk login
![gb11]()
- Browser akan menampilkan konsol Web Manajemen Openstack setelah login
![gb12]()
- Jika ingin menggunakan Openstack untuk mengelola DevStack gunakanlah perintah terminal linux, lalu ketikkan source openrc di terminal linux
![gb13]()
Setelah itu kita bisa menambahkan suatu gambar instans ke glance untuk digunakan saat membuat Mesin Virtual dengan Nova
- Menambahkan Gambar Uji Cirros, lalu download Gambar Virtual dengan mengetikkan kode berikut: wget http://download.cirros-cloud.net/0.5.2/cirros-0.5.2-x86_64-disk.img
![gb14]()
- Lalu upload ke Glance dengan mengetikkan kode berikut:
![gb15]()
- Lalu konfirmasi apabila gambar berhasil terupload
![gb16]()
- Jika berhasil, maka gambar akan terlihat di browser
![gb17]()
