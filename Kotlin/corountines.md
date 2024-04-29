> ## Kotlin Corountines
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Kotlin/Modul%20Kotlin.md)

Pada modul terakhir ini, kita akan belajar tentang pengaturan tugas-tugas secara bersamaan dalam Kotlin dan mengapa Kotlin Coroutines sangat berguna untuk itu. Ini adalah topik yang menarik dan akan membantu kita mengembangkan aplikasi dengan lebih baik. Semangat Belajar💪🏻

## Daftar Isi

- [Concurrency Pada Kotlin](#concurrency-pada-kotlin)
- [Concurrency vs Parallelism](#concurrency-vs-parallelism)
- [Process, Thread, I/O-Bound](#process-thread-io-bound)
- [Permasalahan Deadlocks dan Livelocks](#permasalahan-deadlocks-dan-livelocks)
- [Permasalahan Starvation dan Race Cond](#permasalahan-starvation-dan-race-conditions)
- [Kotlin Coroutines](#kotlin-coroutines)
- [Memulai Coroutines](#memulai-coroutines)
- [Coroutines Builder](#coroutines-builder)
- [job](#job)
- [Membuat dan Menjalankan Job Baru](#membuat-dan-menjalankan-job-baru)
- [Membatalkan Job](#membatalkan-job)
- [Deferred](#deferred)
- [Coroutine Dispatcher](#coroutine-dispatcher)
- [Channels](#channels)
- [Rangkuman](#rangkuman)

## Concurrency Pada Kotlin
Apa itu Concurency? Concurrency merujuk pada situasi ketika beberapa proses terjadi secara simultan dalam suatu sistem. Fenomena ini sangat umum dan sering terjadi dalam kehidupan sehari-hari. Misalnya, di dunia nyata, kita sering melakukan beberapa kegiatan sekaligus. Oleh karena itu, ketika merancang sistem yang mendukung kegiatan nyata, perhatian terhadap concurrency menjadi sangat penting.

## Concurrency vs Parallelism
Concurrency terjadi ketika beberapa proses saling tumpang tindih pada saat yang sama. Hal ini dapat terjadi ketika terdapat dua atau lebih thread yang sedang aktif. Jika komputer hanya memiliki satu core, semua thread tidak akan dieksekusi secara paralel. Meskipun demikian, concurrency memungkinkan komputer dengan satu core terlihat seperti melakukan banyak tugas secara bersamaan, meskipun sebenarnya tugas-tugas tersebut dilakukan secara bergantian.

Sementara itu, parallelism terjadi ketika dua proses dieksekusi secara bersamaan pada titik waktu yang sama. Parallelism dapat terjadi jika terdapat dua atau lebih thread dan komputer memiliki dua core atau lebih. Dengan demikian, setiap core dapat menjalankan perintah dari masing-masing thread secara bersamaan.

## Process, Thread, I/O-Bound

**Process:**  sebuah program yang sedang berjalan di dalam sistem komputer. Setiap proses memiliki ruang memori sendiri dan dapat berjalan secara independen. Proses juga dapat memiliki satu atau lebih thread yang bekerja bersama untuk menyelesaikan tugas yang diberikan.

**Threed:**   unit terkecil dalam pemrograman yang dapat dijadwalkan (scheduled) oleh sistem operasi. Thread berjalan dalam konteks proses dan berbagi ruang memori yang sama dengan proses induknya. Dalam satu proses, terdapat satu thread utama (main thread), dan thread-thread tambahan dapat dibuat untuk menjalankan tugas-tugas yang berbeda secara bersamaan.

**I/O-Bound:**  merujuk pada jenis pekerjaan yang lebih banyak bergantung pada operasi input/output (I/O) daripada pada penggunaan CPU. Tugas I/O-Bound seringkali melibatkan membaca atau menulis data ke perangkat I/O seperti disk atau jaringan. Pada tugas-tugas ini, sebagian besar waktu dihabiskan untuk menunggu operasi I/O selesai, sementara penggunaan CPU relatif rendah.

## Permasalahan Deadlocks dan Livelocks

**Deadlock:**  Deadlock adalah kondisi di mana beberapa proses terjebak karena saling menunggu sumber daya yang dipegang oleh proses lain. Untuk terjadi deadlock, empat kondisi harus terpenuhi: mutual exclusion, hold and wait, no preemption, dan circular wait. Deadlock dapat dicegah dengan menggunakan strategi penghindaran, deteksi, pencegahan, atau pemulihan. Memahami deadlock penting untuk mencegah terjadinya dan menjaga kinerja sistem yang stabil.

**Livelocks:**  kondisi di mana dua atau lebih proses terjebak dalam siklus aktif tanpa membuat kemajuan nyata dalam eksekusi mereka. Dalam livelock, proses-proses tersebut terus melakukan tindakan, tetapi tidak ada kemajuan yang terjadi dalam sistem.

Perbedaan antara livelock dan deadlock adalah bahwa dalam livelock, proses-proses terus bergerak dan melakukan tindakan, namun mereka tidak berhasil mencapai tujuan akhir atau saling mempengaruhi satu sama lain. Ini bisa terjadi ketika dua atau lebih proses saling menghambat satu sama lain dan terus menyesuaikan tindakan mereka tanpa mencapai keadaan yang diharapkan.

## Permasalahan Starvation dan Race Conditions

**Starvation** adalah kondisi di mana sebuah proses atau sumber daya sistem tidak mendapatkan akses yang adil atau tidak pernah mendapatkan kesempatan untuk melanjutkan eksekusi atau menggunakan sumber daya yang diperlukan. Hal ini dapat terjadi jika sistem memberikan prioritas yang tidak seimbang atau tidak adil kepada proses-proses tertentu, sehingga proses lain terus-menerus terabaikan.

**Contoh dari starvation** adalah ketika beberapa proses memiliki prioritas yang lebih tinggi daripada proses lain, dan proses-proses dengan prioritas rendah tidak pernah diberikan kesempatan untuk menjalankan tugas mereka. Akibatnya, proses-proses tersebut terjebak dalam antrian atau terhenti dalam keadaan yang tidak efektif.

**Race conditions** terjadi ketika hasil akhir dari eksekusi program bergantung pada urutan atau kecepatan akses bersama terhadap sumber daya yang dibagikan.

**Contoh dari race conditions** adalah ketika dua atau lebih thread mencoba mengubah nilai variabel bersama secara bersamaan tanpa pengaturan sinkronisasi.

## Kotlin Coroutines

Coroutines adalah fitur unggulan dalam Kotlin yang digunakan untuk menulis kode asynchronous dan non-blocking. Mereka dianggap sebagai "thread yang ringan" karena coroutines lebih efisien daripada thread dalam hal penggunaan sumber daya. Coroutines dapat berjalan dalam thread tunggal dan memungkinkan jutaan coroutines berjalan dalam beberapa thread. Coroutines dikelola oleh pengguna, sedangkan thread dikelola oleh sistem operasi. Meskipun coroutines dijalankan dalam thread, mereka tidak saling terikat dan satu thread dapat memiliki banyak coroutines di dalamnya.

## Memulai Coroutines

Untuk mendapatkan pemahaman yang lebih baik tentang coroutines, mari kita memulai dengan mencobanya langkah demi langkah. Yang perlu Anda ketahui pertama adalah bahwa coroutines bukanlah bagian asli dari bahasa Kotlin, tetapi merupakan sebuah library yang disediakan oleh JetBrains. Oleh karena itu, untuk menggunakan coroutines, Anda perlu menambahkan dependensi berikut ke file **build.gradle.kts:**

```agsl
dependencies {
    implementation(org.jetbrains.kotlinx:kotlinx-coroutines-core:1.5.1)
}
```

## Coroutines Builder

Kotlin menyediakan beberapa pembuat coroutine yang dapat disesuaikan dengan berbagai skenario, seperti:

- Pembuat coroutines "launch" digunakan untuk memulai coroutines yang tidak mengembalikan hasil. Dengan menggunakan "launch", kita dapat memperoleh objek Job yang dapat digunakan untuk membatalkan eksekusi coroutines.

- Pembuat coroutines "runBlocking" digunakan untuk mengubah kode yang memblokir menjadi kode yang dapat ditangguhkan. Ketika menggunakan "runBlocking", thread saat ini akan diblokir hingga eksekusi coroutines selesai. Fungsi ini berguna dalam skenario seperti penggunaan pada fungsi "main()" atau dalam penerapan unit test.

- Pembuat coroutines "async" digunakan untuk memulai coroutines yang mengembalikan hasil. Namun, perlu diingat bahwa "async" akan menangkap setiap pengecualian (exception) yang terjadi dalam coroutines. Sebagai hasilnya, "async" akan mengembalikan objek "Deferred" yang berisi hasil atau pengecualian. Jika hasilnya adalah pengecualian, kita harus siap untuk menanganinya.

```
import kotlinx.coroutines.*
import kotlin.system.measureTimeMillis
suspend fun getCapital(): Int {
    delay(1000L)
    return 50000
}
 
suspend fun getIncome(): Int {
    delay(1000L)
    return 75000
    
    fun main() = runBlocking {
    val timeOne = measureTimeMillis {
        val capital = getCapital()
        val income = getIncome()
        println("Your profit is ${income - capital}")
    }
 
    val timeTwo = measureTimeMillis {
        val capital = async { getCapital() }
        val income = async { getIncome() }
        println("Your profit is ${income.await() - capital.await()}")
    }
 
    println("Completed in $timeOne ms vs $timeTwo ms")
 
}
    
}
```

## Job

Secara umum, dalam coroutines, terdapat dua jenis fungsi asynchronous. Pertama, fungsi yang mengembalikan hasil, yang digunakan ketika kita ingin mendapatkan data setelah fungsi tersebut selesai dijalankan. Misalnya, ini berguna saat mengambil informasi dari web service yang memberikan respon dalam format JSON atau format lainnya. Kedua, fungsi yang tidak mengembalikan hasil, yang biasanya digunakan untuk mengirimkan analitik, mencatat log, atau melakukan tugas serupa yang tidak memerlukan pengembalian nilai.

**Job** adalah Sebuah perintah asynchronous yang menghasilkan objek yang disebut "job" yang merepresentasikan coroutine yang sebenarnya. Objek job ini memiliki tiga properti yang mencerminkan keadaan atau statusnya. Berikut adalah ketiga properti tersebut:

- **isActive**: Properti ini menunjukkan apakah job sedang aktif atau tidak.

- **isCompleted**: Properti ini menunjukkan apakah job telah selesai atau belum.

- **isCancelled**: Properti ini menunjukkan apakah job telah dibatalkan atau tidak.

Secara umum, sebuah job akan segera dijalankan setelah dibuat. Namun, kita juga memiliki kemampuan untuk membuat sebuah job tanpa menjalankannya. 

Berikut adalah penjelasan tentang setiap state yang mungkin terjadi pada sebuah job:
    
- **New**: Ini adalah keadaan awal ketika sebuah job telah diinisialisasi tetapi belum pernah dijalankan.

- **Active**: Sebuah job dikatakan aktif ketika sedang berjalan. Ini mencakup job yang sedang berjalan serta job yang ditangguhkan (suspended).

- **Completed**: Ketika sebuah job sudah tidak berjalan lagi, statusnya menjadi Completed. Ini berlaku baik untuk job yang berakhir dengan normal, dibatalkan, maupun karena terjadi pengecualian (exception).

- **Cancelling**: Ini adalah kondisi ketika fungsi cancel() dipanggil pada job yang sedang aktif. Job ini memerlukan waktu untuk menyelesaikan proses pembatalan.

- **Cancelled**: Ini adalah keadaan ketika sebuah job berhasil dibatalkan. Penting untuk dicatat bahwa job yang dibatalkan juga dapat dianggap sebagai Completed.

Dengan memahami setiap state ini, kita dapat melacak dan mengelola keadaan job dalam coroutines.

## Membuat dan Menjalankan Job Baru

Job dapat dimulai dengan menggunakan fungsi launch() atau dengan membuat objek Job() seperti contoh di bawah ini:

```agsl
//menggunakan launch():
fun main() = runBlocking {
    val job = launch {
        // Do background task here
    }
}
 
//menggunakan Job():
fun main() = runBlocking {
    val job = Job()
}
```

Setelah diinisialisasi, job akan berada dalam keadaan New dan akan segera dijalankan. Namun, jika Anda ingin membuat sebuah job tanpa menjalankannya secara langsung, Anda dapat menggunakan CoroutineStart.LAZY seperti contoh di bawah ini:

```
fun main() = runBlocking {
    val job = launch(start = CoroutineStart.LAZY) {
        TODO("Not implemented yet!")
    }
}
```
### Menjalankan Job
Setelah membuat sebuah job, kini kita bisa mulai menjalankan job tersebut. Caranya pun cukup sederhana, kita bisa menggunakan fungsi start() seperti berikut:
```
fun main() = runBlocking {
    val job = launch(start = CoroutineStart.LAZY) {
        delay(1000L)
        println("Start new job!")
    }
 //pilih salah satu join atau star
    job.start()
    job.join()
    println("Other task")
}
```
Perbedaan antara start() dan join() adalah bahwa start() akan memulai eksekusi job tanpa menunggu job selesai, sedangkan join() akan menunda eksekusi sampai job selesai.

Dengan menggunakan start(), program akan melanjutkan eksekusi setelah job dimulai, tanpa menunggu job selesai. Ini memungkinkan program untuk menjalankan tugas lain secara bersamaan dengan job yang sedang berjalan.

Di sisi lain, dengan menggunakan join(), program akan menunggu hingga job selesai sebelum melanjutkan eksekusi ke perintah selanjutnya. Dengan join(), kita dapat memastikan bahwa hasil dari job telah tersedia sebelum melanjutkan eksekusi ke bagian selanjutnya dalam program.

Jadi, start() digunakan ketika kita ingin menjalankan job secara asynchronous dan melanjutkan eksekusi program tanpa menunggu hasilnya, sedangkan join() digunakan ketika kita ingin menunggu job selesai sebelum melanjutkan eksekusi program.

## Membatalkan Job

nya job yang sedang aktif yang dapat dibatalkan. Anda dapat melakukan pembatalan ini dengan memanggil fungsi cancel() seperti contoh di bawah ini:

```
fun main() = runBlocking {
    val job = launch {
        delay(5000)
        println("Start new job!")
    }
 
    delay(2000)
    job.cancel()
    println("Cancelling job...")
    if (job.isCancelled){
        println("Job is cancelled")
    }
}
```
untuk menambah pesan error bisa menambahkan dengan kode ini
```
//menambah kode ni
@InternalCoroutinesApi
fun main() = runBlocking {
    val job = launch {
        delay(5000)
        println("Start new job!")
    }
 
    delay(2000)
    //ini 
    job.cancel(cause = CancellationException("time is up!"))
    println("Cancelling job...")
    if (job.isCancelled){
        println("Job is cancelled because ${job.getCancellationException().message}")
    }
}
```
## Deferred
Pada dasarnya, nilai yang dikembalikan oleh fungsi async juga merupakan sebuah job. Nilai deferred ini dibuat dan dimulai ketika coroutine mencapai state active. Namun, fungsi async juga memiliki parameter opsional seperti CoroutineStart.LAZY yang memungkinkan deferred untuk dimulai saat fungsi start, join, atau await dipanggil. Dengan menggunakan parameter tersebut, kita dapat mengaktifkan deferred hanya saat dibutuhkan oleh perintah start, join, atau await.

## Coroutine Dispatcher

Dalam coroutines, kita perlu menentukan thread mana yang akan digunakan untuk menjalankan dan melanjutkan sebuah coroutine. Untuk melakukan ini, kita menggunakan base class yang disebut CoroutineDispatcher. Di dalam kelas tersebut, terdapat beberapa objek yang dapat digunakan untuk menentukan thread yang akan digunakan untuk menjalankan coroutines.

- Dispatchers.Default : merupakan dispatcher dasar yang digunakan oleh semua builder standar seperti launch, async, dan sebagainya, jika tidak ada dispatcher lain yang ditentukan secara eksplisit. Dispatchers.Default menggunakan kumpulan thread yang tersedia pada JVM. Pada dasarnya, jumlah maksimum thread yang digunakan oleh Dispatchers.Default adalah sama dengan jumlah core yang ada pada CPU.

untuk menulisnya bisa dengan dengan code ini :
```agsl
launch {
    // TODO: Implement suspending lambda here
}
//atau
launch(Dispatchers.Default){
    // TODO: Implement suspending lambda here
}
```
- Dispatchers.IO : sebuah dispatcher yang digunakan untuk menghindari pemblokiran pada operasi I/O. Dispatcher ini akan menggunakan kumpulan thread yang dibuat berdasarkan permintaan. Anda dapat menggunakannya dengan menambahkan Dispatchers.IO pada builder coroutines.

contoh penulisannya :
```agsl
launch(Dispatcher.IO){
    // TODO: Implement algorithm here
}
```
- Dispatchers.Unconfined : Dispatcher ini akan menjalankan coroutines pada thread yang sedang aktif hingga mencapai titik penangguhan. Setelah penangguhan terjadi, coroutines akan dilanjutkan pada thread di mana operasi penangguhan tersebut dipanggil.

Sebagai contoh, ketika fungsi a memanggil fungsi b yang dijalankan dengan dispatcher pada thread tertentu, fungsi a akan dilanjutkan pada thread yang sama di mana fungsi b dijalankan.
```
import kotlinx.coroutines.*
 
fun main() = runBlocking<Unit> {
    launch(Dispatchers.Unconfined) {
        println("Starting in ${Thread.currentThread().name}")
        delay(1000)
        println("Resuming in ${Thread.currentThread().name}")
    }.start()
}
```

ada beberapa builder yang dapat digunakan untuk menentukan thread yang dibutuhkan:

- Single Thread Context : Dispatcher ini memastikan bahwa setiap saat coroutines akan dijalankan pada thread yang ditentukan. Untuk mengimplementasikannya, Anda dapat menggunakan newSingleThreadContext() seperti contoh kode berikut:

```
import kotlinx.coroutines.*
 
fun main() = runBlocking<Unit> {
    val dispatcher = newSingleThreadContext("myThread")
    launch(dispatcher) {
        println("Starting in ${Thread.currentThread().name}")
        delay(1000)
        println("Resuming in ${Thread.currentThread().name}")
    }.start()
}
----------------------------
//output
//Starting in myThread
//Resuming in myThread
```
- Thread Pool : Dispatcher ini merupakan sebuah pool thread yang memiliki kumpulan thread. Dispatcher ini akan memulai dan melanjutkan coroutines di salah satu thread yang tersedia dalam kumpulan tersebut. Pada saat runtime, sistem akan menentukan thread mana yang tersedia dan juga bagaimana proses distribusi beban kerjanya.

contoh codingannya :
```
import kotlinx.coroutines.*
 
fun main() = runBlocking<Unit> {
    val dispatcher = newFixedThreadPoolContext(3, "myPool")
 
    launch(dispatcher) {
        println("Starting in ${Thread.currentThread().name}")
        delay(1000)
        println("Resuming in ${Thread.currentThread().name}")
    }.start()
}
------------------------
//output
//Starting in myPool-1
//Resuming in myPool-2
```
## Channels

**Channels** merupakan nilai deferred yang menyediakan mekanisme yang mudah untuk mentransfer nilai tunggal antara coroutines. Secara konsep, channels memiliki kesamaan dengan BlockingQueue [11], namun alih-alih memblokir sebuah thread, channels menangguhkan sebuah coroutine yang lebih efisien dan ringan.

contoh codenya
```
import kotlinx.coroutines.*
import kotlinx.coroutines.channels.Channel
 
fun main() = runBlocking(CoroutineName("main")) {
    val channel = Channel<Int>()
    launch(CoroutineName("v1coroutine")){
        println("Sending from ${Thread.currentThread().name}")
        for (x in 1..5) channel.send(x * x)
    }
 
    repeat(5) { println(channel.receive()) }
    println("received in ${Thread.currentThread().name}")
}
```

## Rangkuman
Rangkuman dari berbagai konsep dan fitur yang telah kita pelajari dalam pengenalan coroutines adalah sebagai berikut:

- Concurrency adalah kemampuan menjalankan beberapa proses secara bersamaan, sedangkan parallelism adalah menjalankan proses-proses tersebut secara benar-benar bersamaan.

- Proses adalah bagian dari aplikasi yang dijalankan dan dapat terdiri dari beberapa thread.

- Thread adalah proses ringan yang menjalankan tugas tertentu dalam suatu proses.

- I/O-Bound adalah algoritma yang bergantung pada perangkat input atau output.

- Deadlocks adalah kondisi di mana dua atau lebih proses saling menunggu dan tidak dapat melanjutkan prosesnya.

- Livelocks adalah kondisi di mana sebuah proses tetap berjalan tanpa dapat menyelesaikan tugasnya, mirip dengan deadlocks.

- Starvation adalah kondisi di mana sebuah proses kekurangan sumber daya dan tidak dapat melanjutkan tugasnya.

- Race Conditions adalah kondisi di mana banyak thread mengakses dan mengubah data bersama secara bersamaan.

- Coroutines adalah cara baru dalam menuliskan thread yang ringan dan efisien dalam Kotlin.

- Coroutine builders seperti launch, runBlocking, dan async digunakan untuk menjalankan coroutines.

- Job adalah hasil dari perintah asynchronous yang dijalankan dan merepresentasikan coroutine yang sebenarnya.

- Deferred adalah nilai kembalian dari fungsi async yang dapat berupa hasil atau exception.

- CoroutineDispatcher adalah base class yang menentukan thread yang menjalankan coroutines.

- Dispatcher.Default adalah dispatcher dasar yang digunakan jika tidak ada dispatcher lain yang ditentukan.

- Dispatcher.IO digunakan untuk operasi I/O yang dapat membongkar pemblokiran.

- Dispatcher.Unconfined menjalankan coroutines pada thread yang sedang berjalan sampai mencapai titik penangguhan.

- Coroutine channel adalah nilai deferred yang menyediakan cara mudah untuk mentransfer nilai tunggal antara coroutines.

- Dengan menggunakan coroutines dan konsep-konsep di atas, kita dapat membuat kode concurrent yang efisien dan dapat berkomunikasi antar coroutines dengan mudah.
