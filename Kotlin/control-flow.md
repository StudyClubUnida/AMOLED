> ## Control Flow (Kotlin)
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Kotlin/Modul%20Kotlin.md)

Kita telah belajar mengenai If Expression pada sub-modul sebelumnya. If Expression merupakan salah satu bagian dari Control Flow. Pada sub-modul ini kita akan mempelajari tentang apa itu control flow dan juga beberapa bagian lain yang ada di dalamnya.

## Daftar Isi

- [Apa itu Control Fow?](#concurrency-pada-kotlin)
- [Expressions dan Statements](#expressions-dan-statements)
- [When Expression](#when-expression)
- [Looping](#looping)
- [While](#while)
- [Do While](#do-while)
- [Range](#range)
- [For Loop](#for-loop)


## Apa itu Control Fow?
Saat kita mengembangkan sebuah program, penting untuk memahami bagaimana alur kerjanya dikendalikan. Control flow merupakan cara kita mengelola alur dari sebuah program berdasarkan kondisi-kondisi tertentu ketika program tersebut dijalankan.

Ada beberapa aspek dari control flow yang perlu kita pahami, termasuk:

1. Ekspresi When
2. Ekspresi & Pernyataan
3. While dan Do While
4. Rentang dan Perulangan For
5. Break dan Continue pada Label

Kita akan menjelajahi dan menerapkan setiap aspek dari control flow tersebut.

## Expressions dan Statements
>> [UP](#daftar-isi)

Saat kita mempelajari bahasa pemrograman, sering kali kita menemui istilah `expressions` dan `statements` yang terkadang bisa membingungkan. 

Untuk menjelaskannya dengan lebih mudah, kita bisa melihat contoh kode If sebagai sebuah statement.

```
fun main() {
    val openCafe = 7
    val now = 8
    if (now > openCafe) {
        print("Cafe already open")
    } else {
        print("Cafe close")
    }
}
```

Pada contoh kode tersebut, if dijelaskan sebagai sebuah statement karena tidak menghasilkan nilai apa pun, melainkan hanya sebagai percabangan dalam bahasa Kotlin.

Namun, hal menariknya adalah If dalam bahasa Kotlin juga dapat digunakan sebagai sebuah expression. Expression adalah sebuah pernyataan yang dapat menghasilkan nilai dan dapat disimpan dalam sebuah variabel, seperti yang ditunjukkan dalam contoh berikut.

```
fun main() {
    val openCafe = 7
    val now = 8
    val cafe = if (now > openCafe) "Cafe already open" else "Cafe close"
    print(cafe)
}
```

Dalam kode tersebut, If akan menghasilkan nilai yang disimpan dalam variabel cafe. Jika kondisi dalam if terpenuhi, nilai `Cafe already open` akan disimpan dalam variabel cafe. Namun, jika kondisinya tidak terpenuhi, variabel tersebut akan berisi nilai `Cafe closed`.

Sebuah expression juga bisa terdapat sebuah expression. Contohnya seperti berikut:
```
 fun main() {
    sum(1 , 1 * 4)
}
 
fun sum(value1: Int, value2: Int) = value1 + value2
```
Dalam kode di atas, ekspresi 1 * 4 merupakan bagian dari pemanggilan fungsi sum(), yang merupakan sebuah fungsi yang menghasilkan nilai. Sebuah fungsi selalu menghasilkan nilai, sehingga pemanggilan fungsi merupakan sebuah ekspresi.

## When Expression
>> [UP](#daftar-isi)

When Expression adalah suatu mekanisme yang memungkinkan nilai dari suatu variabel atau ekspresi untuk mengubah alur program. Ini memberikan kemampuan untuk mengevaluasi banyak kondisi yang berbeda dan bertindak berdasarkan nilai yang cocok dengan salah satu kondisi tersebut.

Contoh sederhana dari penggunaan when expression adalah sebagai berikut:

```
fun main() {
    val value = 6

    when(value){
        6 -> println("value is 6")
        7 -> println("value is 7")
        8 -> println("value is 8")
    }

    /*
        output: value is 6
    */
}
```

`When` akan mengevaluasi argumen yang diberikan pada setiap cabangnya secara berurutan hingga satu kondisi terpenuhi. Dalam `when`, kita juga memiliki opsi untuk menambahkan cabang `else` sebagai berikut:

```
fun main() {
    val value = 20

    when(value){
        6 -> println("value is 6")
        7 -> println("value is 7")
        8 -> println("value is 8")
        else -> println("value cannot be reached")
    }

    /*
        output: value cannot be reached
    */
}
```
`else` akan dievaluasi jika tiada satupun kondisi yang terpenuhi pada branch sebelumnya.

else adalah hal wajib jika kita menggunakan when expression untuk mengembalikan nilai. Bagaimana jika kita melewatkannya? Akan tampil eror berikut:
**'when' expression must be exhaustive, add necessary `else` branch**

Apabila kita memiliki dua atau lebih baris kode yang akan dijalankan di setiap cabang, kita dapat memindahkannya ke dalam kurung kurawal ({ }) seperti berikut:

```
fun main() {
    val value = 7
    val stringOfValue = when (value) {
        6 -> {
            println("Six")
            "value is 6"
        }
        7 -> {
            println("Seven")
            "value is 7"
        }
        8 -> {
            println("Eight")
            "value is 8"
        }
        else -> {
            println("undefined")
            "value cannot be reached"
        }
    }

    println(stringOfValue)

    /*
        output : 
            Seven
            value is 7
    */
}
```

`when` juga memungkinkan kita untuk memeriksa instance dengan tipe tertentu dari sebuah objek menggunakan `is` atau `!is`. Contohnya seperti berikut:

```
fun main() {
    val anyType : Any = 100L
    when(anyType){
        is Long -> println("the value has a Long type")
        is String -> println("the value has a String type")
        else -> println("undefined")
    }

    /*
        output : the value has a Long type
    */
}
```

Jika kita melihat penjelasan dan contoh penggunaan dari when expression di atas, kita akan menemukan kesamaan dengan if expression. Namun, kapan sebaiknya kita menggunakan keduanya?

- **If expression** sebaiknya digunakan ketika kita memiliki kondisi yang sederhana, biasanya tidak lebih dari dua, dan ketika strukturnya tidak terlalu rumit.

- **when expression** lebih cocok digunakan ketika kita memiliki lebih dari dua kondisi yang berbeda.

## Looping
>> [UP](#daftar-isi)

Ketika ditugaskan untuk mencetak beberapa baris teks yang sama ke dalam konsol, kita cenderung akan merencanakan program dengan pendekatan berikut:

```
Hello World
Hello World
Hello World
Hello World
Hello World
```

Kita pasti langsung terpikir akan menulis programnya seperti berikut:
```
fun main() {
    println("Hello World")
    println("Hello World")
    println("Hello World")
    println("Hello World")
    println("Hello World")
}
```

Bagaimana jika kita harus menampilkan sejumlah besar teks? Tentu saja, menulis fungsi println() sesuai dengan jumlah teks yang ingin kita tampilkan tidaklah praktis.

Untuk mengatasi ini, kita dapat menggunakan perulangan. Perulangan adalah proses menjalankan blok yang sama berulang kali hingga kondisi yang ditentukan tidak terpenuhi atau bernilai false.

Perulangan terbagi menjadi `While`, `Do While`, dan `For Loop`. Pada sub-modul ini, kita akan membahas `While` dan `Do While`, sementara `For Loop` akan dibahas pada sub-modul berikutnya.

## While
>> [UP](#daftar-isi)

Untuk menggunakan While, kita membutuhkan kata kunci `while`, lanjut ke kondisi di dalam tanda kurung, dan diakhiri oleh blok body dari `while` itu sendiri. Berikut adalah contoh dari penggunaan While:

```
fun main() {
    var counter = 1
    while (counter <= 7){
        println("Hello, World!")
        counter++
    }
}
/*
   output :
       Hello, World!
       Hello, World!
       Hello, World!
       Hello, World!
       Hello, World!
       Hello, World!
       Hello, World!
*/
```

Perhatikan kondisi yang diberikan pada perulangan While di atas; selama nilai dari variabel counter kurang dari atau sama dengan 7, kode di dalamnya akan terus dieksekusi. Begitu kondisi tersebut tidak lagi terpenuhi, proses perulangan akan dihentikan.

While merupakan jenis perulangan yang disebut sebagai **_Entry Controlled Loop_**. Ini berarti bahwa kondisi yang diberikan akan dievaluasi terlebih dahulu sebelum proses perulangan dimulai. Jika kondisi tersebut memenuhi syarat, maka proses perulangan akan dilakukan.

Namun, jika kondisi yang diberikan tidak memenuhi syarat sejak awal, maka proses perulangan tidak akan pernah dijalankan. Anda dapat menguji hal ini dengan menulis dan menjalankan kode berikut:

```
fun main() {
    var counter = 8
    while (counter <= 7){
        println("Hello, World!")
        counter++
    }
}
```

Dengan While kita tidak perlu menuliskan fungsi println() secara berulang untuk mencetak teks ke dalam konsol seperti contoh kasus di awal.

## Do While
>> [UP](#daftar-isi)

Selain menggunakan While, kita dapat menggunakan Do While untuk melakukan perulangan, seperti yang terlihat pada contoh berikut:
```
fun main() {
    var counter = 1
    do {
        println("Hello, World!")
        counter++
    } while (counter <= 7)
}
 
/*
   output:
       Hello, World!
       Hello, World!
       Hello, World!
       Hello, World!
       Hello, World!
       Hello, World!
       Hello, World!
*/
```

Berbeda dengan While, Do While merupakan jenis perulangan yang disebut sebagai **_Exit Controlled Loop_**, di mana proses perulangan akan langsung dieksekusi pada awalnya. Evaluasi kondisi baru dilakukan setelah satu iterasi perulangan selesai.

Ketika menggunakan While dan Do While, perhatikan kemungkinan terjadinya infinite loop, yaitu kondisi di mana proses perulangan terus berlangsung tanpa henti sampai aplikasi mengalami crash. Contoh dari infinite loop dapat dilihat seperti berikut:

```
fun main() {
    var value = 'A'
    do {
        print(value)
    } while (value <= 'Z')
}
```

_Infinite loop_ terjadi jika kondisi yang diberikan selamanya terpenuhi atau bernilai true.

## For Loop
>> [UP](#daftar-isi)

Sebagaimana halnya dengan While dan Do While, For adalah suatu konsep perulangan di mana blok yang sama akan dieksekusi selama hasil evaluasi kondisi yang diberikan memenuhi atau bernilai true. For dapat digunakan pada Ranges, Collections, Arrays, dan segala sesuatu yang menyediakan iterator. Contoh dari For loop dapat dilihat seperti berikut.
```
fun main() {
    val ranges = 1..5
    for (i in ranges){
        println("value is $i!")
    }
}
 
/*
   output :
       value is 1!
       value is 2!
       value is 3!
       value is 4!
       value is 5!
*/
```

**For loop** menggunakan range expression seperti berikut.
```
fun main() {
    val ranges = 1.rangeTo(10) step 3
    for (i in ranges ){
        println("value is $i!")
    }
}
 
/*
   output :
       value is 1!
       value is 4!
       value is 7!
       value is 10!
*/
```
Pada kode di atas, kita menambahkan ekstensi `step` yang akan mengembalikan nilai baru dengan tipe `IntProgression` dengan jarak nilai sebelumnya adalah 3.

Untuk tujuan yang sama, kita juga bisa memanfaatkan salah satu ekstensi pada Kotlin yaitu forEach. Contohnya seperti berikut.
```
fun main() {
    val ranges = 1.rangeTo(10) step 3
    ranges.forEach { value ->
        println("value is $value!")
    }
}
 
/*
   output :
       value is 1!
       value is 4!
       value is 7!
       value is 10!
*/
```


## Range
>> [UP](#daftar-isi)

Range adalah salah satu jenis yang khas dalam Kotlin. Dalam Range, kita dapat menentukan nilai awal dan nilai akhir. Range dapat dinyatakan dengan menggunakan operator .. atau dengan menggunakan fungsi rangeTo() dan downTo().

Ada beberapa cara untuk membuat Range di Kotlin.

**1. Menggunakan `..`**

```
val rangeInt = 1..10
```

Kode diatas menggunakan operator .. untuk membuat Range. Variabel rangeInt di atas mencakup nilai 1, 2, 3, 4, 5, 6, 7, 8, 9, 10. Jarak antara dua nilai yang dicakup, ditentukan oleh step. Secara default, step bernilai 1. Untuk mendapatkan step kita bisa menggunakan properti step seperti contoh berikut:

```
fun main() {
    val rangeInt = 1..10
    print(rangeInt.step)
}
 
/*
   output: 1
*/
```

untuk mengubah nilai dari step bisa dilakukan ketika kita menginisialisasi nilai yang dicakup Range itu sendiri:
```
fun main() {
    val rangeInt = 1..10 step 2
    rangeInt.forEach {
        print("$it ")
    }
    println(rangeInt.step)
}
 
/*
   output: 1 3 5 7 9 2
*/
```
Pada kode di atas kita menentukan nilai step adalah 2, maka nilai yang dicakup variabel rangeInt adalah 1, 3, 5, 7, 9.

**2. Menggunakan Fungsi `rangeTo()`**
```
val rangeInt = 1.rangeTo(10)
```

Kode di atas, operator `..` digantikan dengan fungsi `rangeTo()` untuk membuat Range . Nilai yang dicakup pada kode di atas sama seperti kode sebelumnya ketika menggunakan operator `..`.

Nilai yang dicakup pada Range dengan urutan **terbalik** seperti berikut:
```
val downInt = 10.downTo(1)
```

Kode berikut memeriksa apakah suatu nilai ada pada cakupan nilai Range.
```
fun main() {
    val tenToOne = 10.downTo(1)
    if (7 in tenToOne) {
        println("Value 7 available")
    }
}
/*
   output: Value 7 available
*/
```
Pada kode di atas kita menggunakan kata kunci in untuk memeriksa apakah 7 berada diantara kisaran 1 sampai 10.
