# Diagram-Docker Compose
![gb1](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/4ad2d34b512f121032f6b269121813207d6255f5/minggu-08/Diagram-Docker.png)<br>
Penjelasan Diagram Diatas :<br>
- Docker image : Sebuah image yang nantinya dapat kita build atau pull melalui Docker Regitery (Docker Hub).
- Container : Container dapat membawa image tadi lalu digunakan untuk membantu development. Satu Image bisa dapat digunakan di banyak Container.
- Dockerd : berisikan Images - images serta Container.
- Docker Client : Sebagai antarmuka dari sisi client yang dapat melakukan perintah melalui terminal untuk menjalankan, membuat dan lain-lainnya pada docker.
- Docker Compose : Dapat menjalankan lebih dari satu container sekali jalan dan untuk memulainya hanya perlu up atau down tanpa remove container tersebut atau juga dapat digunakan untuk menajalnkan service di swarm.
- Docker Swarm : Sebagai bentuk orkestrasi docker paling sederhana yang digunakan untuk menjalankan aplikasi di atas cluster. Semisal php atau html biasa yang hanya bisa jalan di 1 host saja. Jika menggunakan pake docker swarm bisa kita duplikat dan saling load balance ke banyak host.
