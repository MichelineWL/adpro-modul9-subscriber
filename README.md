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

📌 **Kesimpulan:**

`guest:guest@localhost:5672` artinya:

> Sambungkan ke RabbitMQ yang berjalan di komputer lokal melalui port 5672, dan login menggunakan username **guest** dan password **guest**.
