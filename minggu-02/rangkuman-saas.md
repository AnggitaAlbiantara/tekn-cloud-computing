[ [<< Kembali](README.md) ]
## 01. What’s the difference between IaaS, SaaS, and PaaS?
Pertama, mari kita lihat beberapa contoh dan layanan dari layanan cloud ini.

- Ini adalah model layanan cloud dasar untuk IaaS, PaaS, dan SaaS.

   ![01](https://github.com/AnggerFNS/tekn-cloud-computing/blob/master/minggu-02/basic.jpg)

- Ini adalah contoh dari IaaS, PaaS, dan juga SaaS.

   ![02](https://github.com/AnggerFNS/tekn-cloud-computing/blob/master/minggu-02/example1.jpg)

   ## IaaS 
     ### IaaS (```Infrastructure as a Service```)
     Anda mendapatkan infrastruktur, yang dimaksud adalah server virtual, hard disk, koneksi jaringan. segala sesuatu yang lain terserah Anda. Dengan segala sesuatu yang lain berarti: mengkonfigurasi & menginstal semuanya, tergantung pada kasus penggunaan Anda: sistem operasi, perangkat lunak tambahan, melakukan pembaruan itu, dll.
     
     Pelanggan tidak memiliki kontrol atas sistem operasi, volume penyimpanan atau kemampuan aplikasi individual tetapi mengontrol pengaturan jaringan (misalnya penetapan alamat IP), aplikasi yang disebarkan, modul server web (misalnya mod_perl) dan mungkin kontrol terbatas atas pengaturan mesin virtual individu (misalnya memori yang dialokasikan ke VM).
     
   ## PaaS 
     ### PaaS (```Platform as a Service```)
     Anda tidak perlu melakukan beberapa hal dari IaaS, misalnya pembaruan keamanan. Biasanya ada beberapa cara otomatis untuk menyebarkan &mengonfigurasi aplikasi Anda
     
     Pelanggan memiliki kontrol atas sistem operasi, dll. Mereka tidak mengontrol infrastruktur cloud yang mendasarinya tetapi mereka memiliki kontrol lebih besar daripada dalam model SaaS.

    ## SaaS 
     ### SaaS (```Software as a Service```)
     Anda hanya menggunakan perangkat lunak yang disediakan (di web). Anda tidak perlu menginstal apa pun, Anda cukup masuk dan menggunakan perangkat lunak yang sebagian besar memiliki beberapa kasus penggunaan khusus.

     Pelanggan tidak mengelola atau mengontrol infrastruktur cloud yang mendasarinya dengan kemungkinan pengecualian pengaturan konfigurasi aplikasi khusus pengguna yang terbatas.
     
Source : https://www.quora.com/What-is-the-difference-between-IaaS-SaaS-and-Paas 

 ## 02. SaaS Platform Architecture.
   SaaS adalah model lisensi dan pengiriman perangkat lunak di mana perangkat lunak dilisensikan berdasarkan langganan dan dihosting secara terpusat. Pengguna dapat mengaksesnya dengan bantuan browser web.
 
 ### SaaS Architecture : 
 Dengan model ini, satu versi aplikasi, dengan satu konfigurasi digunakan untuk semua pelanggan. Aplikasi ini diinstal pada beberapa mesin untuk mendukung skalabilitas (disebut penskalaan horizontal). Ada dua varietas utama SaaS:
 - ```Vertical SaaS``` -> Perangkat Lunak yang menjawab kebutuhan industri tertentu (misalnya, perangkat lunak untuk industri perawatan kesehatan, pertanian, real estat, keuangan)
 - ```Horizontal SaaS``` -> Produk yang berfokus pada kategori perangkat lunak (pemasaran, penjualan, alat pengembang, SDM) tetapi agnostik industri.

   ![03](https://github.com/AnggerFNS/tekn-cloud-computing/blob/master/minggu-02/vertical.jpg)

 ### Keuntungan dari SaaS :
 Ini menawarkan peluang besar bagi organisasi dari semua ukuran untuk mengalihkan risiko akuisisi perangkat lunak, dan untuk memindahkan TI dari pusat biaya reaktif menjadi bagian proaktif yang menghasilkan nilai dari perusahaan. Model pengiriman sesuai permintaan mengubah beberapa hal ini. Aplikasi SaaS tidak memerlukan penyebaran infrastruktur besar di lokasi klien. Ini menghilangkan atau secara drastis mengurangi komitmen sumber daya di muka.
 
 Integrasi dapat direncanakan dan dijalankan dengan upaya minimal, menciptakan salah satu interval waktu-ke-nilai sesingkat mungkin untuk investasi TI utama. Memberi pelanggan kesempatan untuk mencoba perangkat lunak sebelum mereka membelinya membantu menghilangkan banyak risiko seputar pembelian perangkat lunak.
 
 ### kesimpulan
 Perusahaan akan melakukannya dengan baik untuk mempertimbangkan fleksibilitas dan implikasi manajemen risiko dari menambahkan SaaS ke portofolio layanan TI mereka. Integrasi dan komposisi adalah komponen penting dalam strategi arsitektur Anda untuk menggabungkan SaaS dengan sukses sebagai anggota yang berpartisipasi penuh dari infrastruktur TI Anda yang berpusat pada layanan. Kami percaya bahwa masa depan komputasi perusahaan tidak akan murni di tempat. Sebaliknya, mereka akan ada dalam harmoni simbiosis.

Source : https://hackernoon.com/saas-software-as-a-service-platform-architecture-757a432270f5

 ## 03. SaaS (Software as a Service) Platform itecture.
 Ledakan dalam komputasi Cloud, yang didorong oleh penyedia layanan cloud seperti Microsoft dengan Azure, Amazon Web Services (AWS), Oracle, dan IBM, telah melihat pertumbuhan produk dan layanan lain yang dikirimkan melalui internet. Ini termasuk model SaaS berikut:
   -	Infrastructure as a Service
   -	Platform as a Service
   -	Machine Learning as a Service
   -	…and much more!
  
  Mengapa menggunakan SaaS Architecture?

   ![03](https://github.com/AnggerFNS/tekn-cloud-computing/blob/master/minggu-02/mengapa.jpg)
  
  Seperti yang disebutkan dalam pendahuluan, perangkat lunak telah didistribusikan kepada pelanggan di berbagai saluran selama beberapa dekade terakhir.  Saluran distribusi yang lebih baru adalah Software as a Service (atau SaaS).
  Dari sudut pandang konsumen, aplikasi SaaS adalah salah satu cara termudah dan paling dapat diandalkan untuk menggunakan layanan atau produk digital. Anda cukup mengaksesnya melalui web, membayar layanan, dan menggunakannya.
  Dalam beberapa tahun terakhir kami telah melihat munculnya ribuan layanan aplikasi SaaS yang ditargetkan untuk konsumen seperti :
    -	Netflix
    -	Microsoft Office 365
    -	Amazon Prime
    -	Twitter
    -	Facebook
    -	Google Docs
  Kesederhanaan Aplikasi Arsitektur SaaS
  Aplikasi perangkat lunak yang dirancang sebagai solusi SaaS biasanya diakses melalui web melalui berbagai jenis perangkat.
  Kemajuan dalam bahasa pemrograman sisi klien seperti JavaScript telah menghasilkan antarmuka web yang lebih intuitif dan, dengan demikian, membuat penggunaan aplikasi yang dikirimkan melalui internet semudah digunakan seperti rekan desktop mereka.

  ### Nilai ekonomis
  Model pembayaran biaya subskrip bulanan atau tahunan memudahkan bisnis untuk menganggarkan, memasangkannya dengan biaya penyiapan infrastruktur nol, dan mudah untuk melihat bagaimana memilih untuk menggunakan solusi SaaS dapat menghemat uang bisnis.

  ### Keamanan
  Keamanan adalah aspek penting dari solusi pengembangan perangkat lunak dan platform SaaS tidak berbeda.  Sebagai konsumen aplikasi yang dirancang menggunakan SaaS, Anda tidak perlu khawatir dengan bagaimana data Anda dikunci.  Itu disimpan dengan aman di cloud!

  ### Kompatibilitas
  Dengan instalasi perangkat lunak tradisional, pembaruan dan tambalan terkadang membutuhkan banyak waktu dan uang. Ini terutama berlaku di perusahaan.

Source : https://www.devteam.space/blog/saas-software-as-a-service-platform-architecture/
 
 ## 04. How to build a cloud-based SaaS Application.
 SaaS business adalah industri yang berkembang sangat cepat yang menarik semakin banyak orang dan perusahaan. Organisasi-organisasi ini semakin banyak aplikasi mengambang di cloud. Penskalaan di cloud juga memiliki beberapa manfaat dan risiko penting.
 
Saat membangun aplikasi SaaS (global) kemungkinan besar Anda membangunnya di cloud. Cloud memiliki banyak keunggulan – pikirkan skalabilitas – berbeda dengan lingkungan server lokal.

Membangun produk untuk cloud berarti membangun produk dengan bahasa pemrograman modern. Selain kemampuan dan keterampilan pribadi, pilihan bahasa pemrograman Anda akan dipengaruhi oleh kemungkinan masing-masing bahasa. Ada berbagai bahasa pemrograman (modern) di luar sana sehingga sulit untuk memilih yang tepat.

### Kesimpulan cara membangun cloud-based SaaS Application.
Dengan Python, MongoDB – sebagai database berorientasi dokumen yang hebat, RabbitMQ dari segi perangkat lunak pengaturan dasar dilakukan. Namun, ada lebih banyak cara untuk dipikirkan.

Source : https://usersnap.com/blog/cloud-based-saas-architecture-fundamentals/

## 2. Carilah 2 layanan SaaS, cari juga software desktop / non cloud yang mempunyai fungsionalitas sama dengan layanan SaaS tersebut.
Layanan SaaS :
 - [LucidChart](https://www.lucidchart.com/pages/)
 ![06](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/eefbafd285a6f0167d9f78b78fafe54d53553b35/minggu-02/lucidchart2.PNG)
 ![05](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/eefbafd285a6f0167d9f78b78fafe54d53553b35/minggu-02/lucidchart.PNG)
 
 - [SmartDraw](https://www.smartdraw.com/)
 ![08](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/eefbafd285a6f0167d9f78b78fafe54d53553b35/minggu-02/smartdraw2.PNG)
 ![07](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/eefbafd285a6f0167d9f78b78fafe54d53553b35/minggu-02/smartdraw.PNG)
 
Layanan Saas Non-Cloud atau Software Desktop :
 - [ClickCharts](https://www.nchsoftware.com/chart/index.html)
 ![07](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/eefbafd285a6f0167d9f78b78fafe54d53553b35/minggu-02/clickcharts2.PNG)
 ![07](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/eefbafd285a6f0167d9f78b78fafe54d53553b35/minggu-02/clickcharts.PNG)
 
 - [GitMind](https://gitmind.com/)
![07](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/eefbafd285a6f0167d9f78b78fafe54d53553b35/minggu-02/gitmind2.PNG)
![07](https://github.com/AnggitaAlbiantara/tekn-cloud-computing/blob/eefbafd285a6f0167d9f78b78fafe54d53553b35/minggu-02/gitmind.PNG)
