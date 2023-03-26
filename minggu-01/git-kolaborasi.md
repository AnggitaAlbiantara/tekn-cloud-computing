[ [<< Kembali](README.md) ]
# Kolaborasi
## FORK
  Fork adalah membuat clone dari suatu repo di GitHub milik upstream author, diletakkan ke milik kontributor. Fork hanya dilakukan sekali saja. Pada dasarnya, proses untuk fork ini meliputi:
  1. Fork repo di web GitHub.
  2. Clone fork tersebut di komputer lokal.
  3. Kontributor harus mem-fork repo upstream author sehingga di repo kontributor muncul repo tersebut. Proses forking ini dijelaskan dengan langkah-langkah berikut:
    1. Login ke GitHub
    2. Akses repo yang akan di-fork: https://github.com/Afifa9/tekn-computing-2
    3. Pada sisi kanan atas, klik Fork:

![gmb01](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/fork1.PNG)
![gmb02](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/fork2.PNG)
![gmb03](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/fork3.PNG)
      
Setelah proses tersebut, clone di komputer lokal:

![gmb04](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/clone.PNG)

Setelah itu, konfigurasikan repo lokal kontributor. Pada kondisi saat ini, di komputer lokal sudah terdapat repo playground-1 yang berada pada direktori dengan nama yang sama. Untuk keperluan berkontribusi, ada 2 nama repo yang harus diatur:
   - origin: menunjuk ke repo milik kontributor di GitHub, hasil dari fork.
   - upstream: menunjuk ke repo milik upstream author (repo asli) di account Afifa9.
Repo origin sudah dituliskan konfigurasinya pada saat melakukan proses clone dari repo kontributor. Konfigurasi repo upstream harus dibuat dan Tambahkan remote upstream, Hasil:
![gmb05](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/kolab1.PNG)

## Mengirimkan Pull Request
Setiap kali melakukan perubahan, kirim perubahan tersebut. Pengiriman ini disebut dengan Pull Request. Pada posisi ini, kontributor bisa mengirimkan kontribusi dengan cara mengirimkan pull request (PR) ke upstream author. Secara umum, langkah-langkahnya adalah sebagai berikut:
  1. Kontributor akan bekerja di repo lokal (create, update, delete isi)
  2. Commit
  3. Push ke repo kontributor
  4. Kirimkan PR ke repo upstream author.
  5. Upstream author me-review dan kemudian menyetujui (merge) ke master atau menolak PR.
  6. Jika disetujui dan di-merge ke repo master dari upstream author, sinkronkan repo di komputer lokal dan repo GitHub kontributor.
Berikut ini adalah contoh pengiriman perubahan isi README.md dengan menambahkan kontributor.
## Membuat Perubahan di Repo Lokal
Sebelum melakukan perubahan, pastikan:
  1. Sudah ada koordinasi secara manual tentang perubahan-perubahan yang akan dilakukan.
  2. Setelah melakukan perubahan-perubahan, pastikan bahwa isi repo lokal tersinkronisasi dengan repo dari upstream author.
  3. Cara melakukan sinkronisasi:
  
  ![gmb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/kolab2.PNG)
  
  4. Lakukan perubahan-perubahan, setelah itu push ke origin (milik kontributor)
  ![gmb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/kolab3.PNG)
  ![gmb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/kolab4.PNG)
  ![gmb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/kolab5.PNG)
  
  5. Setelah itu, buka halaman Web dari repo kontributor https://github.com/AnggitaAlbiantara/tekn-cloud-computing-1. Pada halaman tersebut akan ditampilkan isi yang kita push.
  
  ![gmb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/kolab6.PNG)
  
  6. Pilih ```Compare and pull request```, kemudian isikan deskripsi PR dan klik pada ```Create pull request```:
  ![gmb11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/kolab7.PNG)
  7. Pada repo upstream author, muncul angka 1 (artinya jumlahnya 1) pada Pull requests di bagian atas.
  8. Upstream author bisa menyetujui setelah melakukan review: klik pada Pull requests, akan muncul PR dengan message seperti yang ditulis oleh kontributor (Add: contributor). Klik pada PR tersebut, review kemudian klik Merge pull request diikuti dengan Confirm merge. Setelah itu, status akan berubah menjadi   Merged.
  9. Sinkronkan semua repo (lokal maupun GitHub kontributor)
  ![gmb12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/ee6b7ab962cbe83a9c02fa9d0364b52089cb1150/minggu-01/kolab8.PNG)
