## Understanding Subscriber and Message Broker

### a. What is AMQP?

**AMQP** (Advanced Message Queuing Protocol) adalah sebuah *open standard communication protocol* yang dirancang untuk **message-oriented middleware**.  
AMQP digunakan untuk memungkinkan sistem yang berbeda — baik dari segi bahasa pemrograman maupun platform — untuk **berkomunikasi satu sama lain dengan cara mengirim dan menerima pesan secara andal** melalui *message broker* seperti **RabbitMQ**.

---

### b. What does it mean? `guest:guest@localhost:5672`

Penjelasan:

- `**guest:guest**` → format ini merupakan **`username:password`** untuk otentikasi ke message broker.
  - **Guest pertama** → *username*
  - **Guest kedua** → *password*

- `**localhost:5672**` → menunjukkan **alamat dan port** dari server message broker.
  - **localhost** → RabbitMQ dijalankan secara lokal di komputer kita.
  - **5672** → port default yang digunakan oleh **AMQP** untuk komunikasi.

 
 **Kesimpulan:**

`guest:guest@localhost:5672` artinya:

> Sambungkan ke RabbitMQ yang berjalan di komputer lokal melalui port 5672, dan login menggunakan username **guest** dan password **guest**.

---

### c. Slowdown Subscriber
![image](https://github.com/user-attachments/assets/aefce6bb-0834-4a73-97f1-90a2b0c90666)
Saya mengirim 10 command "cargo run" dan mendapatkan 1 antrian.
Hal ini terjadi karena ketika saya melakukan spam menjalankan 10 command tersebut, publisher mengirim pesan dengan cepat.
Subscriber tidak dapat mengimbangi kecepatan publisher dalam memproses event. 
Dengan demikian, terjadilah delay dan menumpuk pada antrian. 
