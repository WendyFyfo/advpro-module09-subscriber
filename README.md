# ADVPRO - SOFTWARE ARCHITECTURE

## TUTORIAL
### STEP 7
 a. What is amqp?
 = AMQP (Advanced Message Queuing Protocol) adalah protokol standar terbuka di appliation layer yang digunakan untuk message-oriented middleware. AMQP memungkinkan berbagai sistem saling mengirim dan menerima message, bahkan jika sistemnya dibangun dengan bahasa atau platform yang berbeda-.

 b. What does it mean? guest:guest@localhost:5672 , what is the first guest, and what
is the second guest, and what is localhost:5672 is for?
 = URL lengkap -> `amqp://guest:guest@localhost:5672`.
 1. `amqp://` ini adalah skema protokolnya
 2. `guest:guest` adalah format username:password. jadi guest pertama adalah username dan guest kedua adalah password. Kedua guest tadi adalah kredensial default di RabbitMQ
 3. `localhost:5672` artinya broker berjalan di lokal `127.0.0.1` dengan port number default untuk koneksi AMQP.