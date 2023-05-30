[ [<<Kembali] ](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/2943e95f0e0572ecd1be1cb465190bddc631a8e1/minggu-06/README.md)
# Gin RESTful API membaca data dari MySQL dan MongoDB
## MySQL
1. Buat direktori baru dengan nama mysql-restfulapi, kemudian instal module dan driver yang diperlukan.

![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/2bb6e0528ef0f04ec67a066703facebbfbc857ca/minggu-06/Lat3.PNG)
![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/2bb6e0528ef0f04ec67a066703facebbfbc857ca/minggu-06/Lat3_1.PNG)

2. Create database MySQL, lalu masukan data kedalamnya.

![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/2bb6e0528ef0f04ec67a066703facebbfbc857ca/minggu-06/Lat3_2.PNG)

3. Setelah itu buat file GO dengan nama [main.go](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/2bb6e0528ef0f04ec67a066703facebbfbc857ca/minggu-06/main.go).

4. Lalu jalankan file tersebut di cmd.

![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/2bb6e0528ef0f04ec67a066703facebbfbc857ca/minggu-06/Lat3_3.PNG)

5. Jalankan server api nya dengan mengetikkan localhost:3000/persons di browser

![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/2bb6e0528ef0f04ec67a066703facebbfbc857ca/minggu-06/Lat3_4.PNG)

## MongoDB
1. Buat folder baru dengan nama restful-api-mongo dan download package nodeJS dengan mengetikkan *Npm Init* dan *npm i express mongoose nodemon dotenv* di cmd

![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo1.PNG)

![gb2](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo2.PNG)

2. Buat file dengan nama *index.js* pada folder restful-api-mongo lalu ketikkan kode berikut pada file

![gb3](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo15.PNG)

3. Selanjutnya buat folder baru dengan nama *Routes* dan buat juga file *Routes.js* pada folder Routes, lalu ketikkan kode berikut pada file Routes.js

![gb4](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo16.PNG)

4. Selanjutnya buat folder baru dengan nama *Model* dan buat juga file *model.js* pada folder Model, lalu ketikkan kode berikut pada file model.js

![gb5](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo17.PNG)

5. Pada file package.json tambahkan kode pada baris 17 - 19

![gb6](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo18.PNG)

6. Buat database baru pada website [Cloud mongoDB](https://account.mongodb.com/account/login?signedOut=true), lalu klik create Cluster

![gb7](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo6.PNG)

![gb8](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo7.PNG)

7. Lalu connect database cluster0 ke MongoDB Compass dengan memilih menu Compass pada web Cloud MongoDB

![gb9](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo8.PNG)

8. Lalu copy code kode koneksi string pada bagian no 2

![gb10](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo9.PNG)

9. Selanjutnya buat file baru dengan nama *.env* dan pastekan kode yang dicopy tadi ke file *.env*, lalu isikan password yang sesuai dengan password akun cloud mongoDB kalian

![gb11](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo10.PNG)

10. Lalu buka MongoDB Compass, lalu klik new connection dan pastekan juga code yang dicopy tadi ke MongoDB Compass, lalu klik connect dan tunggu hingga proses koneksi selesai

![gb12](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo11.PNG)

![gb13](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo12.PNG)

![gb14](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo13.PNG)

11. Setelah semua selesai terbuat maka nantinya isi seluruh dari folder *Restful-Api-Mongo* adalah sebagai berikut

![gb15](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo14-1.PNG)

12. Lalu jalankan server dengan mengetikkan *npm start* pada cmd

![gb16](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo5.PNG)

13. Isikan suatu data yang nantinya tersimpan di database cluster0, lalu Jalankan url berikut pada website postman *localhost:3000/api/post* dan klik send untuk memposting data yang diambil dari database cluster0

![gb17](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo20.PNG)

14. Dan yang terakhir jalankan url berikut pada website postman *localhost:3000/api/getAll* dan klik send untuk mendapatkan data yang didapatkan dari database cluster0

![gb18](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/527c47ccb9ec1693f60483a0988b2ff88e641828/minggu-06/restmongo21.PNG)
