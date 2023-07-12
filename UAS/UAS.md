### Konfigurasi Image MySQL
1. Buka [Docker Official Image](https://hub.docker.com/search?q=&type=image&image_filter=official) lalu cari image yang diinginkan, disini saya menggunakan [image MySQL](https://hub.docker.com/_/mysql)
2. Selanjutnya pull image MySQL dengan mengetikkan perintah ```docker pull mysql```<br>
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/1.PNG)<br>
3. Cek apakah image berhasil di pull dengan mengetikkan perintah ```docker images```<br>
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/2.PNG)<br>
4. Setelah itu jalankan containers MySQL yang dibuat tadi pada cmd dengan mengetikkan perintah berikut ```docker run --name=mysql-docker -d mysql:latest``` dan cek apakah containers MySQL tadi berhasil berjalan atau tidak dengan mengetikkan perintah ```docker ps```<br>
![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/3.PNG)
5. 
