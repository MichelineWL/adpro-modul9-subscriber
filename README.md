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

---

### d. Three Subscriber's Console 
![image](https://github.com/user-attachments/assets/51b849e1-7b0f-4455-989c-a947f6daa5f8)
![image](https://github.com/user-attachments/assets/85b0906c-5189-49c8-9413-58ad8ab05004)
Setelah melakukan run pada 3 terminal untuk subscriber, meskipun saya sudah melakukan spam command "cargo run" pada publisher, tidak terjadi delay sama sekali 
Kemudian terjadi pembagian diantara 3 terminal tersebut secara rata: 
1. Terminal 1 menjalankan id 5 --> Terminal 2 menjalankan id 1 --> Terminal 3 menjalankan id 2 
2. Terminal 1 menjalankan id 3 --> Terminal 2 menjalankan id 4 --> Terminal 3 menjalankan id 5
Dengan demikian, ini membuktikan bahwa message broker membagi pesan secara rata ke subscriber. 
Ternyata delay dapat diminimalisir dengan melakukan penambahan jumlah subscriber, tanpa melakukan refactor sama sekali pada kode program
