[ [<< Kembali](README.md) ]
# 01. Instalasi Git Pada Windows

sebelum kita menginstall Git di windows, kita sudah harus memiliki editor teks. Bisa menggunakan [Notepad++](https://notepad-plus-plus.org/) atau [Visual Studion Code](https://code.visualstudio.com/) atau [Vim](https://www.vim.org/).

1. Setelah download [Git](https://git-scm.com/downloads), lalu open file installernya yang telah di download, lalu akan muncul lisensi, selanjutnya klik **Next**.

![install-01](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-01.PNG)

2. Kemudian pilih folder untuk penyimpanan Git, Secara default Git akan tersimpan di folder C:\Program Files\Git, setelah itu klik **Next**.

![install-02](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-02.PNG)

3. Lalu klik **Next**, biarkan settingan Git di setting secara default.

![install-03](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-03.PNG)

4. Klik **Next**.

![install-04](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-04.PNG)

5. Lalu pilih editor teks yang ingin digunakan (Disini saya menggunakan editor teks Visual Code Code), lalu klik **Next**.

![install-05](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-05.PNG)

6. Checklist pada pilihan **Let Git Decide** selanjutnya klik **Next**.

![install-06](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-06.PNG)

7. Selanjutnya checklist pada pilihan **Git from the command line.....**, lalu klik **Next**.

![install-07](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-07.PNG)

8. Selanjutnya checklist pada pilihan **Use Bundled OpenSSH**, lalu klik **Next**.

![install-08](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-08.PNG)

9. Checklist pada pilihan **Use the OpenSSH library**, klik **Next**.

![install-09](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-09.PNG)

10. Checklist pada pilihan **Checkout windows-style....**, klik **Next**.

![install-10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-10.PNG)

11. Checklist lagi pada pilihan **Use MinTTY...**, klik **Next**.

![install-11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-11.PNG)

12. Checklist pada pilihan **Default**, klik **Next**.

![install-12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-12.PNG)

13. Lalu pilih **Git Credential Manager**, **Next**.

![install-13](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-13.PNG)

14. Pilih **Enable file system caching**, **Next**.

![install-14](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-14.PNG)

15. Checklist pada **Enable experimental.....**, klik **Next**.

![install-15](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-15.PNG)

16. Tunggu hingga proses installasi berhasil.

![install-16](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-16.PNG)

17. Lalu klik **Finish**.

![install-17](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-17.PNG)

18. Jika berhasil terinstal, maka pada windows terdapat aplikasi **Git**.

![install-18](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-18.PNG)

19. Tampilan jika kita menggunakan aplikasi **Git-Bash**.

![install-19](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-19.PNG)

20. Tampilan jika kita menggunakan aplikasi **Git-Gui**.

![install-20](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-20.PNG)

21. Cek versi Git dengan cara ketikkan pada CMD **git --version**.

![install-21](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4bf8182d24b3927693c1f722e50351cb7b8f4157/minggu-01/install-21.PNG)


# 02. Konfigurasi Git Pada Windows
Konfigurasi Git pada windows dapat dilakukan dengan cara mengetikkan kode dibawah ini di CMD
```
$ git config --global user.name "AnggitaAlbiantara
$ git config --global user.email anggita.albiantara@students.utdi.ac.id
```
![konfig1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/f9ab2c90c09b90fbacf1ae39145622ad0f97faaf/minggu-01/konfig1.PNG)

Selanjutnya jika kalian ingin melihat hasil dari konfigurasi diatas maka kalian dapat mengetikkan code berikut di CMD
```
$ git config --lists
```
![konfig2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/f9ab2c90c09b90fbacf1ae39145622ad0f97faaf/minggu-01/konfig2.png)

Langkah ini cukup dilakukan sekali saja, kecuali jika kalian ingin melakukan perubahan nama dan email.

# 03. Membuat Repo Di Account Git Kita
  Untuk membuat repo, dapat menggunakan langkah-langkah berikut :
  1.  Klik tanda **+** pada bagian atas dekat profil Git kita, klik lalu pilih **New repository**
  
  ![repo1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/c082351cb70c186dd935708c5bb00fa93a36852a/minggu-01/membuat-repo.PNG)
  
  2. Isikan nama owner, nama repo, keterangan, pilih settingan repo untuk private atau public, checklist untuk add README.md atau tidak, serta pilih lisensi.

![repo2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/c082351cb70c186dd935708c5bb00fa93a36852a/minggu-01/membuat-repo-2.PNG)
  
  3. Klik **Create Repository**
Setelah langkah-langkah tersebut berhasil, maaka repo akan dibuat dan bisa diakses dengan menggunakan pola ```https://github.com/username/reponame```. Pada repo tersebut, hanya akan muncul 1 file, yaitu LICENSE. Jika kalian memilih membuat README pada saat langkah ke 2, juga akan muncul README.md. Ada atau tidak ada README.md tidak mempunyai efek apapun pada langkah ini.

![repo3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/c082351cb70c186dd935708c5bb00fa93a36852a/minggu-01/membuat-repo-3.PNG)
    
# Clone Repo
Untuk clone repo, kalian dapat mengetikkan code dibawah pada CMD,
```git clone https://github.com/UserName/NameRepository```
![clone](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e90682af032420d78376421fb21ff55cc878cbd9/minggu-01/clone.PNG)

Sehingga hasil clonenya akan masuk ke penyimpanan lokal komputer kita.
![clone2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e90682af032420d78376421fb21ff55cc878cbd9/minggu-01/hasil-clone.PNG)

# Mengelola Repo
  Setelah melakukan ```clone``` ke penyimpanan lokal komputer kita, semua manipulasi konten dilakukan di komputer lokal dan hasilnya akan di-**push** ke remote repo di GitHub. Dengan demikian, jangan berganti-ganti remote lokal, sekali dibuat disitu, tetap berada disitu. Jika kehilangan repo lokal, maka harus melakukan clone ulang ke direktori yang bersih (kosong) setelah itu baru lakukan pengelolaan repo. Beberapa hal yang biasanya dilakukan seperti berikut ini.

# Mengubah Isi - Push Tanpa Branching dan Merging
Perubahan isi bisa terjadi karena satu atau kombinasi beberapa hal berikut:
  1. File dihapus
  2. File diedit
  3. Membuat file / direktori baru
  4. Menghapus direktori
Untuk kasus-kasus tersebut, lakukan perubahan di komputer lokal, setelah itu push ke repo. 
![isi](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5028c39e5ea4a0b51c8bcf0e68d2a3418713efdb/minggu-01/mengubah-isi-1.PNG)
![push](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/5028c39e5ea4a0b51c8bcf0e68d2a3418713efdb/minggu-01/mengubah-isi-2.PNG)

# Mengubah Isi dengan Branching and Merging
Dengan menggunakan cara ini, setiap kali akan melakukan perubaham, perubahan itu dilakukan di komputer lokal dengan membuat suatu *cabang* yang nantinya digunakan untuk menampung perubahan-perubahan tersebut. Setelah itu, cabang itu yang akan dikirim ke repo GitHub untuk dimintai review kemudian digabungkan (```merge```) ke master. Secara umum, repo yang dibuat biasanya sudah mempunyai satu branch yang disebut dengan ```master```. Cara ini lebih aman, terstruktur, terkendali, dan mempunyai history yang lebih baik. Jika perubahan yang kita buat sudah terlalu kacau dan kita menyesal, maka ada cara untuk "membersihkan" repo lokal kita. Secara umum, langkahnya adalah sebagai berikut :

1. Buat branch untuk menampung perubahan-perubahan
2. Lakukan perubahan-perubahan
3. Add dan commit perubahan-perubahan tersebut ke branch
4. Kembali ke repo master
5. Buat pull request di GitHub
6. Merge pull request di GitHub
7. Merge branch untuk menampung perubahan-perubahan tersebut ke master.
8. Selesai.

![isi1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/8f161b5872863806e1f23bb06d68e73676e0afa5/minggu-01/mengubah-isi-3.PNG)
![isi2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/050e0778ea0aff57dd42622bac6267757994d5ab/minggu-01/mengubah-isi-4_1.PNG)
![isi3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/8f161b5872863806e1f23bb06d68e73676e0afa5/minggu-01/mengubah-isi-4.PNG)
