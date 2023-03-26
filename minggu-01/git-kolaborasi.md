# 04 Kolaborasi
# FORK
  Fork adalah membuat clone dari suatu repo di GitHub milik upstream author, diletakkan ke milik kontributor. Fork hanya dilakukan sekali saja. Pada dasarnya, proses untuk fork ini meliputi:
  1. Fork repo di web GitHub.
  2. Clone fork tersebut di komputer lokal.
  3. Kontributor harus mem-fork repo upstream author sehingga di repo kontributor muncul repo tersebut. Proses forking ini dijelaskan dengan langkah-langkah berikut:
    1. Login ke GitHub
    2. Akses repo yang akan di-fork: https://github.com/AnggitaAlbiantara/tekn-cloud-computing
    3. Pada sisi kanan atas, klik Fork:
      ![gmb01](https://user-images.githubusercontent.com/114986359/224532029-5095463c-3965-4cbf-b0bc-4c82aebbe591.png)
      ![gmb02](https://user-images.githubusercontent.com/114986359/224532068-f40696e9-2c78-42a6-a2a9-58454dca1f94.png)
Setelah proses tersebut, clone di komputer lokal:
![gmb1](https://user-images.githubusercontent.com/114986359/224532326-e6d02cff-7545-4bf9-8083-07c13d569789.png)
Setelah itu, konfigurasikan repo lokal kontributor. Pada kondisi saat ini, di komputer lokal sudah terdapat repo playground-1 yang berada pada direktori dengan nama yang sama. Untuk keperluan berkontribusi, ada 2 nama repo yang harus diatur:
   1. origin: menunjuk ke repo milik kontributor di GitHub, hasil dari fork.
   2. upstream: menunjuk ke repo milik upstream author (repo asli) di account oldstager.
Repo origin sudah dituliskan konfigurasinya pada saat melakukan proses clone dari repo kontributor. Konfigurasi repo upstream harus dibuat.
![gmb2](https://user-images.githubusercontent.com/114986359/224532363-00c3a599-a8e1-4d57-a8e4-8d7033626b9d.png)
Tambahkan remote upstream:
![gmb2](https://user-images.githubusercontent.com/114986359/224532491-99ac3d34-fe3b-4efa-9b5a-3350725e5940.png)
Hasil:
![gmb2](https://user-images.githubusercontent.com/114986359/224532478-1c4265d2-a5dd-4020-8850-4dfe2d10220a.png)

# Mengirimkan Pull Request
Setiap kali melakukan perubahan, kirim perubahan tersebut. Pengiriman ini disebut dengan Pull Request. Pada posisi ini, kontributor bisa mengirimkan kontribusi dengan cara mengirimkan pull request (PR) ke upstream author. Secara umum, langkah-langkahnya adalah sebagai berikut:
  1. Kontributor akan bekerja di repo lokal (create, update, delete isi)
  2. Commit
  3. Push ke repo kontributor
  4. Kirimkan PR ke repo upstream author.
  5. Upstream author me-review dan kemudian menyetujui (merge) ke master atau menolak PR.
  6. Jika disetujui dan di-merge ke repo master dari upstream author, sinkronkan repo di komputer lokal dan repo GitHub kontributor.
Berikut ini adalah contoh pengiriman perubahan isi README.md dengan menambahkan kontributor.
# Membuat Perubahan di Repo Lokal
Sebelum melakukan perubahan, pastikan:
  1. Sudah ada koordinasi secara manual tentang perubahan-perubahan yang akan dilakukan.
  2. Setelah melakukan perubahan-perubahan, pastikan bahwa isi repo lokal tersinkronisasi dengan repo dari upstream author.
  3. Cara melakukan sinkronisasi:
  ![gmb3](https://user-images.githubusercontent.com/114986359/224532643-a372d96e-c241-4963-9b5a-b33666863399.png)
  4. Lakukan perubahan-perubahan, setelah itu push ke origin (milik kontributor)
  ![gmb3](https://user-images.githubusercontent.com/114986359/224532676-97fc3a20-54ca-4d53-bb06-752a1b42e1c9.png)
  ![gmb4](https://user-images.githubusercontent.com/114986359/224532704-33ce5703-76f0-456d-8e52-c52f6765cfeb.png)
  ![gmb5](https://user-images.githubusercontent.com/114986359/224532728-0f4522e3-f4c1-44bf-938f-bc47bfcdcda7.png)
  ![gmb6](https://user-images.githubusercontent.com/114986359/224532744-0ed13019-48ae-43f2-9e7f-8635147e7e8c.png)
  5. Setelah itu, buka halaman Web dari repo kontributor https://github.com/Afifa9/tekn-cloud-computing-1. Pada halaman tersebut akan ditampilkan isi yang kita push.
  ![gmb01](https://user-images.githubusercontent.com/114986359/224533037-86b08d83-bc8b-4c01-8233-507b54869577.png)
  6. Pilih ```Compare and pull request```, kemudian isikan deskripsi PR dan klik pada ```Create pull request```:
  ![gmb02](https://user-images.githubusercontent.com/114986359/224533087-11e3756c-a897-4c2c-82bc-488b0c7b7b0f.png)
  7. Pada repo upstream author, muncul angka 1 (artinya jumlahnya 1) pada Pull requests di bagian atas.
  8. Upstream author bisa menyetujui setelah melakukan review: klik pada Pull requests, akan muncul PR dengan message seperti yang ditulis oleh kontributor     (Add: contributor). Klik pada PR tersebut, review kemudian klik Merge pull request diikuti dengan Confirm merge. Setelah itu, status akan berubah menjadi   Merged.
  9. Sinkronkan semua repo (lokal maupun GitHub kontributor)
  ![gmb7](https://user-images.githubusercontent.com/114986359/224533184-cea0ac68-21a0-4122-9e5f-013341fd9b82.png)
  **Source Code** : [kolaborasi.txt](https://github.com/Afifa9/tekn-cloud-computing/files/10950318/kolaborasi.txt)
