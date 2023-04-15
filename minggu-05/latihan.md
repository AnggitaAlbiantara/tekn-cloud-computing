[ [<<Kembali] ](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/05b259494b79562304b3ddeaedf8e4cc05a2b424/minggu-04/README.md)
# Install Apache Ofbiz
## Langkah 1: Install Java
- Open terminal Ubuntu, lalu ketikkan kode berikut: *sudo apt install openjdk-8-jdk openjdk-8-jre*
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/1.PNG)

- Verifikasi Java, apakah berhasil terinstal atau tidak, dengan mengetikkan kode berikut: *java -version*
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/2.PNG)

- Konfigurasi Java Home dan Jre Home dengan mengetikkan perintah seperti gambar dibawah ini 
![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/3.PNG)

## Langkah 2: Download Apache Ofbiz
- Download Apache Ofbiz dengan mengetikkan kode **wget https://dlcdn.apache.org/ofbiz/apache-ofbiz-18.12.07.zip**
![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/4.PNG)

- Extract folder zip yang didownload tadi dengan mengetikkan kode seperti gambar dibawah ini
![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/5.PNG)
![gb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/6.PNG)

## Langkah 3: Install Apache Ofbiz pada terminal linux
- Jalankan perintah dibawah ini untuk menginstall Apache Ofbiz
![gb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/7.PNG)

- Membersihkan sistem dan muat ulang data Apache OFBiz lengkap dengan menggunakan perintah gradlew berikut:
![gb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/8.PNG)

## Langkah 4: Muat Data Demo di Apache Ofbiz
- Melakukan muat data Demo di Apache Ofbiz dengan mengetikkan kode berikut:
![gb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/9.PNG)

## Langkah 5: Memulai Layanan Apache Ofbiz 
- Memulai Layanan Apache Ofbiz dengan mengetikkan kode berikut:
![gb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/10.PNG)

## Langkah 6: Mengakses Server Apache Ofbiz di Browser
- Mengakses server Apache Ofbiz di browser dengan mengetikkan url localhost:8443/accounting/control/main di browser, lalu masukkan nama pengguna **admin**, password **ofbiz**:
![gb12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/12.PNG)

- Apabila berhasil maka akan mengeluarkan output seperti gambar dibawah ini:
![gb13](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/745761c333ddc9b567b8c3aa4cb862c75f77bd12/minggu-05/13.PNG)
