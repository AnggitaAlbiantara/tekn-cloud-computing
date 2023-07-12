# Konfigurasi Image MySQL
1. Buka [Docker Official Image](https://hub.docker.com/search?q=&type=image&image_filter=official) lalu cari image yang diinginkan, disini saya menggunakan [image MySQL](https://hub.docker.com/_/mysql)
2. Selanjutnya pull image MySQL dengan mengetikkan perintah ```docker pull mysql```<br>
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/1.PNG)<br>
3. Cek apakah image berhasil di pull dengan mengetikkan perintah ```docker images```<br>
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/2.PNG)<br>
4. Setelah itu jalankan containers MySQL yang dibuat tadi pada cmd dengan mengetikkan perintah berikut ```docker run --name=mysql-docker -d mysql:latest``` dan cek apakah containers MySQL tadi berhasil berjalan atau tidak dengan mengetikkan perintah ```docker ps```<br>
![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/3.PNG)
5. Cek apakah Client MySQL sudah bisa digunakan atau belum dengan mengetikkan perintah ```docker logs some-mysql```<br>
![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/4.PNG)
6. Coba jalankan Client MySQL dengan mengetikkan perintah ```docker exec -it some-mysql bash``` lalu ketikkan perintah ```mysql -uroot -p``` pada terminal bash<br>
![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/5.PNG)

# Buat Repository Baru Di DockerHUB
1. Kunjungu website [DockerHUB](https://hub.docker.com/), lalu klik create repository, isikan repository name, lalu klik create untuk membuat repository baru<br>
![gb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/6.PNG)
2. Selanjutnya login pada Docker lokal dengan akun Docker Hub dengan mengetikkan perintah ```docker login```<br>
![gb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/7.PNG)
3. Kemudian buat tag pada sample docker dengan mengetikkan perintah ```docker tag mysql:latest anggitaalbiantara/mysql_docker:latest```<br>
![gb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/8.PNG)
4. Push sample ke Docker Hub dengan mengetikkan perintah ```docker push anggitaalbiantara/mysql_docker:latesst.<br>
![gb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/9.PNG)



![gb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/10.PNG)
![gb11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/11.PNG)
![gb12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/e5acb25c17f93fe4108cb6ac59c79a469f2c6286/UAS/Gambar%20Hasil%20Praktek/12.PNG)
