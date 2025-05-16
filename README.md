# ADVPRO - SOFTWARE ARCHITECTURE

## TUTORIAL
### SUBSCRIBER - STEP 7
a. What is amqp?

 = AMQP (Advanced Message Queuing Protocol) adalah protokol standar terbuka di appliation layer yang digunakan untuk message-oriented middleware. AMQP memungkinkan berbagai sistem saling mengirim dan menerima message, bahkan jika sistemnya dibangun dengan bahasa atau platform yang berbeda-.

b. What does it mean? guest:guest@localhost:5672 , what is the first guest, and what
is the second guest, and what is localhost:5672 is for?

= URL lengkap -> `amqp://guest:guest@localhost:5672`.
 1. `amqp://` ini adalah skema protokolnya
 2. `guest:guest` adalah format username:password. jadi guest pertama adalah username dan guest kedua adalah password. Kedua guest tadi adalah kredensial default di RabbitMQ
 3. `localhost:5672` artinya broker berjalan di lokal `127.0.0.1` dengan port number default untuk koneksi AMQP.

### Monitoring multiple slow subsriber
![Log of multipe subscribers](/image/image%20copy.png)
Pada tangkapan layar di atas, kita dapat melihat 3 instance slow subscriber yang berjalan bersamaan. Lalu kita juga dapat melihat tiap baris log dari tiap instance kalau mereka memproses pesan-pesan yang berbeda (bisa dilihat dari id tiap pesan yang tidak urut). hal ini menunjukkan bahwa pada event-driven architectur ayang menggunakan satu queue yang dibagikan, kita bisa melakukan parallel proccessing dengan banyak subcriber.

![Monitoring multiple slow subscriber](/image/image.png)
Pada gambar di atas, kita bisa melihat bahwa queuenya mencapai sekitar 30 message, tapi dapt dengan cepat diproses. Hal tersebut menunjukkan kalau konkurensi subscriber bisa mencegah backlog dalam kondisi load yang besar.

Satu hal yang dapat ditingkatkan disini adalah menggunakan async (seperti tokio) pada subscriber agar satu subscriber dapat memproses banyak pesan secara bersamaan.