> ## Fundamental Kotlin
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Kotlin/Modul%20Kotlin.md)

## Daftar Isi
1. [Kotlin Fundamental](#kotlin-fundamental)
2. [Tipe Data & Variable](#tipe-data--variable)
3. [Char](#char)
4. [String](#string)
5. [If Conditions](#if-conditions)
6. [Boolean](#boolean)
7. [Numbers](#numbers)
8. [Arrays](#arrays)
9. [Tipe Nullable](#tipe-nullable)
10. [Safe Call & Elvis Operator](#safe-call-dan-elvis-operator)
11. [String Template](#string-template)

## Kotlin Fundamental
>> [UP](#daftar-isi)

Kita sudah tahu cara  membangun dan menjalankan program Kotlin. Kini di sub-modul ini kita akan mempelajari konsep-konsep dasar (fundamental) pada Kotlin. Kita akan belajar bersama mengenai _data types_, _function_, _expression_ dan juga _nullability_ pada Kotlin.

Buat Anda yang pernah belajar pemrograman sebelumnya, tentu tak asing dengan program ini. **Hello World!** sering digunakan untuk menunjukkan sintaks dasar pada sebuah bahasa pemrograman. Karena kita sedang belajar bahasa pemrograman Kotlin, maka kita mengganti namanya dengan **Hello Kotlin!**.

Berikut adalah contoh kode dari program tersebut:

```
// Contoh mencetak tulisan
fun main() {
   println("Hello Kotlin!")
}
```

Baris pertama dari kode di atas adalah komentar yang ditandai dengan tanda `//`.

Ada 2 jenis Komentar, diantaranya :
1. Single-line Comment `//`

``// single line comment``
2. Multi-line Comment `/* .. */`

```
/*
Multi-line Comment
Hello Kotlin
*/
```

Sebuah komentar akan diabaikan selama proses kompilasi, sehingga tidak akan mempengaruhi jalannya program yang kita tulis. Komentar dapat digunakan untuk mendokumentasikan kode agar ketika kita membuka kembali kode tersebut di masa mendatang, kita dapat dengan mudah memahami fungsinya.


Selanjutnya adalah fungsi yang disebut `main()`. Fungsi ini harus didefinisikan saat membuat sebuah program. Fungsi `main()` berfungsi sebagai titik masuk utama yang akan otomatis dipanggil saat program dijalankan. Pada bab berikutnya, kita akan mempelajari lebih lanjut tentang cara mendefinisikan sebuah fungsi.

Lalu Kemudian fungsi `println()`, fungsi yang akan kita gunakan untuk mencetak teks ke dalam layar atau konsol. Fungsi `println()` membutuhkan satu argumen berupa message dengan tipe data yang dikehendaki.

Selain fungsi `println()`, terdapat juga fungsi `print()` yang berfungsi sama seperti fungsi `println()`. Bedanya, `println()` akan **_menambahkan_ baris baru setelah selesai mencetak argumen yang diberikan**, sementara fungsi `print()` **_tidak_ melakukan apapun ketika argumen yang diberikan, selesai dicetak.**


## Tipe Data & Variable
>> [UP](#daftar-isi)

Data types atau tipe data adalah sebuah pengklasifikasian data berdasarkan jenis data tersebut. Untuk mengembangkan sebuah program, ada beberapa tipe data yang akan kita pelajari. Di antaranya adalah _Character_, _String_, _Array_, _Numbers_ dan _Booleans_. 

Sebuah variabel akan membutuhkan kata kunci var atau val, identifier, type dan initialization. Berikut contoh penerapan Tipe Data: 

``var company: String = "AMOLED"``

Mari kita bahas satu per satu

- `var` atau `val` digunakan untuk mengontrol nilai dari sebuah variabel.
Kata kunci `var` dapat mengubah nilai yang sudah kita inisialisasikan. Contoh penggunaan `var` :

````
var studyClub: String = "AMOLED"
studyClub = "Academy of Mobile Darussalam"
````
Sedangkan `val`  tidak bisa mengubah nilai yang sebelumnya sudah kita inisialisasi.  Jika kita memaksa untuk mengubahnya, maka akan terjadi eror seperti berikut:

```
val studyClub: String = "AMOLED"
studyClub = "Academy of Mobile Darussalam" // Error : Val cannot be reassigned
```

- Indetifier

  Identifier merupakan nama dari sebuah variabel. Pada contoh kode di atas yang merupakan identifier adalah `studyClub`.
Di dalam sebuah program kita tidak bisa membuat **lebih dari 1 (satu) variabel** dengan nama sama.

- Type

    Tipe data dibutuhkan agar kompiler dapat mengetahui bagaimana sebuah data akan digunakan. Tipe data dari contoh variabel di atas adalah String.
- Initialization

    Initialization atau nilai awal dari sebuah variabel. Pada contoh di atas yang berperan sebagai initialization adalah `AMOLED` dan `Academy of Mobile Darussalam`.

Tipe data juga menentukan operasi apa saja yang dapat dilakukan pada sebuah variabel dan bagaimana nilai dari sebuah variabel disimpan.

Contoh, ketika kita menggunakan operator `+` terhadap dua variabel yang bertipe _String_ seperti berikut:
```
fun main() {
    val firstWord = "Amoled"
    val lastWord = "UNIDA"
    print(firstWord + lastWord)
}

/*
   output: Amoled UNIDA
*/
```
Maka kedua nilai dari variabel `firstWord` dan `lastWord` akan digabungkan menjadi satu nilai.

Berbeda ketika kita menggunakan operator `+` pada variabel yang bertipe _Int_ seperti berikut:
```
fun main() {
    val valueA: Int = 20
    val valueB = 30
    print(valueA + valueB)
}

/*
   output: 50
*/
```


## Char
>> [UP](#daftar-isi)

Ketika kita mengembangkan sebuah program kita pasti membutuhkan variabel dengan tipe data yang mampu menyimpan nilai berbentuk teks. Terdapat dua (2) tipe data yang bisa kita gunakan, yaitu _**Char**_ dan _**String**_. 

Characters direpresentasikan menggunakan tipe `Char`. Untuk mendefinisikan sebuah variabel dengan tipe data `Char` kita bisa menggunakan tanda kutip tunggal **(' ')** seperti berikut:

`val character = 'Z'`

Tipe data `Char` hanya dapat kita gunakan untuk _menyimpan karakter tunggal._ Sebaliknya jika kita memasukkan lebih dari 1 (satu) karakter, akan terjadi eror:

`val character: Char = 'ABC' // Error: Incorrect character literal`

Kita bisa melakukan operasi _increment_ `(++)` dan _decrement_ `(--)` pada sebuah variabel dengan tipe data Char seperti berikut:

```
fun main() {
    var vocal = 'A'
 
    println("Vocal " + vocal++)
    println("Vocal " + vocal++)
    println("Vocal " + vocal++)
    
    println("Vocal " + vocal--)
    println("Vocal " + vocal--)
    println("Vocal " + vocal--)
    println("Vocal " + vocal--)
}
 
/*
   output:
       Vocal A
       Vocal B
       Vocal C
       Vocal D
       Vocal C
       Vocal B
       Vocal A
*/
```
Operasi increment dan decrement sendiri merupakan operasi yang bisa kita gunakan pada tipe data **Number**.
## String
>> [UP](#daftar-isi)

**_String_** merupakan tipe data yang mirip dengan Char. Ia dapat digunakan untuk menyimpan nilai berupa teks. Perbedaannya, String bisa menampung beberapa karakter di dalamnya. 

Kita bisa mendefinisikan variabel tersebut dengan tanda petik ganda `("...")` seperti berikut:

`val textString  = "Kotlin"`


Pada dasarnya, sebuah string terdiri dari kumpulan karakter yang memiliki struktur array, sehingga kita dapat dengan mudah mengakses karakter tunggal dalam string tersebut. Untuk melakukannya, kita dapat menggunakan indeks seperti yang ditunjukkan di bawah ini:

```
fun main() {
    val text  = "Kotlin"
    val firstChar = text[0]
 
    print("Huruf pertama dari kata $text adalah $firstChar")
}
 
/*
  Output : Huruf pertama dari kata Kotlin adalah K
*/
```

### Escaped String 
Escaped String yang memungkinkan kita untuk mengurangi ambiguitas nilai yang berada di dalam sebuah String.
Misal kita akan mendefinisikan kode :

`val statement = "Kotlin is Awesome!"`

Kemudian kita ingin menambahkan tanda petik ganda di dalam sebuah String seperti berikut:

`val statement = "Kotlin is "Awesome!""`

Untuk mengatasinya, kita bisa melakukan escaped dengan menambahkan karakter `backslash (\)` sebelum tanda petik ganda seperti berikut:

`val statement = "Kotlin is \"Awesome!\""`

Terdapat beberapa karakter lain yang dapat digunakan untuk melakukan escaped di dalam sebuah String, antara lain:
 
- `\t`: menambah tab ke dalam teks.

- `\n`: membuat baris baru di dalam teks.

- `\’`: menambah karakter single quote kedalam teks.

- `\”`: menambah karakter double quote kedalam teks.

- `\\`: menambah karakter backslash kedalam teks.

### Raw String
**Raw String** yang memungkinkan kita menuliskan multiline dan arbitrary text. Ketika ingin membuat beberapa baris String biasanya kita melakukan escaped terhadap String dengan memanfaatkan karakter escape `\n` seperti berikut:

```
val line = 
        "Line 1\n" +
        "Line 2\n" +
        "Line 3\n" +
        "Line 4\n"
```
Dengan _**Raw String**_, kita dapat membuatnya dengan cara yang lebih mudah yaitu seperti berikut:
```
fun main() {
    val line = """
        Line 1
        Line 2
        Line 3
        Line 4
    """.trimIndent()
 
    print(line)
}
 
/*
    Output:
        Line 1
        Line 2
        Line 3
        Line 4
 */
 ```


## If Conditions
>> [UP](#daftar-isi)

**_If Condition_** direpresentasikan dengan kata kunci `if`. If akan kita perlukan untuk menyelesaikan kasus di atas, dimana `if` akan digunakan untuk menguji suatu kondisi untuk menjalankan sebuah proses. If akan mengeksekusi sebuah statement atau expression jika hasil evaluasi dari expressions yang diberikan pada blok `if` bernilai **true**. Sebaliknya, jika bernilai **false** maka _proses yang ditentukan akan dilewatkan_.

```
val openHours = 7
val now = 20
val office: String
if (now > openHours) {
    office = "Office already open"
} else {
    office = "Office is closed"
}
 
print(office)
```

Kode di atas adalah contoh sederhana penggunaan `if` dengan memanfaatkan operator **_greater than_** untuk membandingkan nilai.

`Else` akan dijalankan jika hasil evaluasi pada expression yang diberikan menghasilkan nilai false. `If` merupakan sebuah expressions yang dapat mengembalikan nilai, sehingga kita dapat menyimpan hasilnya ke dalam sebuah variabel.

Lalu bagaimana jika kita memiliki beberapa kondisi? Kita bisa menggabungkan **_else_** dan **_if_** seperti berikut:

```
val openHours = 7
val now = 7
val office: String
office = if (now > 7) {
    "Office already open"
} else if (now == openHours){
    "Wait a minute, office will be open"
} else {
    "Office is closed"
}
 
print(office)
```

Blok else if akan dijalankan jika hasil evaluasi pada branch sebelumnya bernilai false. Jika hasil evaluasi pada branch else if juga bernilai nilai false, maka lanjut ke evaluasi branch selanjutnya.

## Boolean
>> [UP](#daftar-isi)

**_Boolean_** adalah sebuah tipe data yang hanya memiliki dua nilai, yaitu `true` dan `false`. Terdapat 3 (tiga) operator yang dapat digunakan pada Boolean.

### Conjunction atau AND `&&`

Operator AND `&&` akan mengembalikan nilai **true** jika semua hasil evaluasi expression yang diberikan bernilai true.

```
fun main() {
    val officeOpen = 7
    val officeClosed = 16
    val now = 20
 
    val isOpen = if (now >= officeOpen && now <= officeClosed){
        true
    } else {
        false
    }
 
    print("Office is open : $isOpen")
 
    /*
        Output : Office is open : false
     */
}
```

### Disjunction atau OR `||`
Operator **_OR_** `||` akan mengembalikan nilai true jika hasil evaluasi dari salah satu expressions yang diberikan bernilai true.
Berikut contoh kode untuk **_OR_**

```
  fun main() {
    val officeOpen = 7
    val officeClosed = 16
    val now = 20
 
    val isClose = now < officeOpen || now > officeClosed
 
    print("Office is closed : $isClose")
    
      // Output : 
          Office is closed : true
}
```
Variabel _**isClose**_ di atas bernilai true. Alasannya, hasil evaluasi salah satu expression yang diberikan, bernilai true, yaitu expression disebelah kanan.

### Negation atau NOT `!`
Operator **_NOT_** `!` digunakan untuk melakukan negasi pada hasil evaluasi sebuah ekspresi yang diberikan. Misalnya, jika hasil evaluasi ekspresi tersebut bernilai true, maka operator **_NOT_** akan mengembalikan nilai false.

```
  fun main() {
    val officeOpen = 7
    val now = 10
    val isOpen = now > officeOpen
 
    if (!isOpen) {
        print("Office is closed")
    } else {
        print("Office is open")
    }
 
        // Output : Office is open
}
```
Hasil expression di atas adalah **true**. Tapi ketika menggunakan operator NOT maka akan dinegasikan menjadi nilai false.

## Numbers
>> [UP](#daftar-isi)

Di Kotlin, tipe data **Number** disimpan dengan cara yang berbeda. Beberapa tipe bawaan yang merepresentasikan Numbers adalah **_Double_**, **_Long_**, **_Int_**, **_Short_** dan **_Byte_**. Setiap tipe data Number memiliki ukuran (satuan Bit) berbeda-beda, tergantung besaran nilai yang dapat simpan.

- **Int (32 Bit)**

  Tipe data Int umumnya digunakan untuk menyimpan nilai numerik. Tipe data Int dapat menyimpan data dalam rentang dari **-2<sup>31</sup>** hingga **+2<sup>31-1</sup>**. Dengan ukuran 32 bit, kita dapat menggunakan tipe data Int untuk menyimpan nilai yang besar. Namun, perlu diperhatikan batasan nilai maksimal yang dapat dimasukkan ke dalamnya.

  ```
  val intNumber = 100
  ```

- Long (64 Bit)

  Tipe data Long digunakan untuk menyimpan nilai numerik yang lebih besar, yaitu dalam rentang dari **-2<sup>63</sup>** hingga **+2<sup>63-1</sup>**. 

  Tipe data Long dapat didefinisikan secara eksplisit dengan menentukan tipe data tersebut dalam kode program.

  ```
  val longNumber: Long = 50
  ```

  Atau dengan menambahkan suffix L seperti berikut:

  ```
  val longNumber = 50L
  ```

- Short (16 Bit)

  Short adalah tipe data bilangan bulat yang memiliki batasan nilai yang relatif kecil karena hanya berukuran 16 bit.

  ```
  val shortNumber: Short = 10
  ```

- Byte (8 Bit)

  Tipe data Byte hanya dapat menyimpan nilai yang terbatas, dikarenakan ukurannya yang kecil mirip dengan tipe data Short. Byte sering digunakan untuk membaca dan menulis data dari stream file atau jaringan.

  ```
  val byteNumber = 0b11010010
  ```

- Double (64 Bit)

  Pada umumnya Double digunakan untuk menyimpan nilai numerik pecahan sampai dengan maksimal **_15-16_** angka di belakang koma.

  ```
  val doubleNumber: Double = 1.3
  ```

- Float (32 Bit)

  Sama seperti Double, namun memiliki ukuran yang lebih kecil, yakni hanya sampai **_6-7_** angka di belakang koma.

  ```
  val floatNumber: Float = 0.123456789f // terbaca hanya 0.1234567
  ```

### Operator pada Numbers
Terdapat beberapa operator matematika pada tipe data Number seperti **_penjumlahan_** `+`, **_pengurangan_** `-`, **_perkalian_** `*` , **_pembagian_** `/` dan **_modulus_** `%` (sisa hasil bagi).

```
fun main() {
    val numberOne = 4
    val numberTwo = 2
 
    // Penjumlahan
    print(numberOne + numberTwo)
    /*
        output : 6
     */
     
     
     // Pengurangan
    print(numberOne - numberTwo)
    /*
        output : 2
     */
     
     
     // Perkalian
    print(numberOne * numberTwo)
    /*
        output : 8
     */
     
     
     // Pembagian
    print(numberOne / numberTwo)
    /*
        output : 2
     */
     
     
     // Sisa bagi
    print(numberOne % numberTwo)
    /*
        output : 0
     */
}
```

### Konversi satuan
konversi dengan bantuan beberapa fungsi seperti `toInt()` berikut:

```
fun main() {
    val byteNumber: Byte = 15
    val intNumber: Int = byteNumber.toInt()
}
```

Kode di atas menggunakan fungsi `toInt()` untuk melakukan konversi secara eksplisit dari tipe data **_Byte_** ke tipe data **_Int_**.

Ada beberapa fungsi konversi yang dapat digunakan antara lain:

- toByte(): Byte 
- toShort(): Short 
- toInt(): Int 
- toLong(): Long 
- toFloat(): Float 
- toDouble(): Double 
- toChar(): Char

## Arrays
>> [UP](#daftar-isi)

Array merupakan tipe data yang memungkinkan untuk menyimpan beberapa objek di dalam sebuah variabel. **_Array_** di Kotlin direpresentasikan oleh kelas `Array` yang memiliki fungsi `get` dan `set` serta properti size. 

Untuk membuat sebuah `Array` bisa memanfaatkan sebuah library function `arrayOf()` seperti berikut:
```
val array = arrayOf(1, 3, 5, 7)
```

Dapat juga memasukkan nilai dengan berbagai jenis tipe data ke dalam `arrayOf()` misalnya:

```
val mixArray = arrayOf(1, 3, 5, 7 , "Dicoding" , true)
```

Membuat Array dengan tipe data primitif dengan memanfaatkan beberapa fungsi spesifik berikut:

- intArrayOf() : IntArray 
- booleanArrayOf() : BooleanArray 
- charArrayOf() : CharArray 
- longArrayOf() : LongArray 
- shortArrayOf() : ShortArray 
- byteArrayOf() : ByteArray

Untuk mendapatkan nilai tunggal dari sekumpulan nilai yang berada di dalam sebuah `Array` dengan memanfaatkan _indexing_ seperti berikut:

```
fun main() {
    val intArray = intArrayOf(1, 2, 4, 5, 7)
    print(intArray[2])
}
 
/*
   Output: 4
*/
```

Perlu diketahui bahwa sebuah indeks selalu dimulai dari 0.

Selain mendapatkan nilai tunggal, dengan indexing kita juga bisa mengubah nilai tunggal tersebut. Sebagai contoh:

```
fun main() {
    val intArray = intArrayOf(1, 3, 5, 7)  // [1, 3, 5, 7] sebelum perubahan
    intArray[2] = 11                       // [1, 3, 11, 7] setelah perubahan
 
    print(intArray[2])
}
 
/*
   Output: 11
*/
```

## Tipe Nullable
>> [UP](#daftar-isi)

Saat mengembangkan program, kita harus sangat berhati-hati terhadap **_NullPointerException (NPE)_**. **_NPE_** adalah sebuah kesalahan yang terjadi ketika kita mencoba mengakses atau memanipulasi nilai dari sebuah variabel yang belum diinisialisasi atau memiliki nilai `null`. Kesalahan ini sangat umum terjadi dan dapat memiliki dampak yang fatal. **_NPE_** juga dikenal sebagai **_"The Billion Dollar Mistake"_** karena kerusakan yang dapat ditimbulkannya.

Dalam menangani **_NPE_**, kita harus berhati-hati karena kesalahan ini dapat menyebabkan kerusakan pada aplikasi saat dijalankan.

Kotlin mampu membedakan objek yang boleh bernilai null dan objek yang tidak boleh bernilai null pada saat objek tersebut dibuat.

```
val text: String = null   // compile time error
```

Jika  ingin sebuah objek bisa bernilai null, kita bisa menambahkan tanda `?` setelah menentukan tipe dari objek tersebut:

```
val text: String? = null 
```

Lalu bagaimana cara kita mengakses atau mengelola nilai dari objek yang ditandai sebagai **_nullable_**? Cara mudahnya, periksa objek tersebut apakah bernilai `null` atau tidak.
Dengan cara menggunakan if/else, kompiler akan mengizinkan untuk mengelola nilai dari sebuah variabel yang kita tandai sebagai nullable.
```
val text: String? = null
 
// val textLength = text.length   // compile time error
 
if (text != null){
    val textLength = text.length // ready to go
}
```



## Safe Call dan Elvis Operator
>> [UP](#daftar-isi)

### Safe Call `?.` 

**_Safe call_** akan menjamin kode yang kita tulis aman dari **_NullPointerException_**. Dalam menggunakan safe call, kita akan mengganti tanda titik `.` dengan tanda `?.` saat mengakses atau mengelola nilai dari objek **_nullable_**. Seperti ini:

```
val text: String? = null
text?.length
```
Dengan safe call, kompiler akan melewatkan proses jika objek tersebut bernilai _null_.

### Elvis Operator `?:`

**_Elvis operator_** memungkinkan kita untuk menetapkan default value atau nilai dasar jika objek bernilai null.

```
val text: String? = null
val textLength = text?.length ?: 7
```

Kode di atas sama seperti ketika menggunakan `if/else` berikut:

```
val textLength = if (text != null) text.length else 7
```

Elvis akan mengembalikan nilai `text.length` jika `text` tidak bernilai _null_. Sebaliknya, jika `text` bernilai _null_ maka default value yang akan dikembalikan.


Satu hal yang perlu diperhatikan dalam penanganan objek nullable. Perhatikan penggunaan operator _non-null assertion_ `!!`, misalnya seperti berikut:

```
val text: String? = null
val textLength = text!!.length
```

Dengan menggunakan _non-null assertion_ kompiler akan mengizinkan kita untuk mengakses atau mengelola nilai dari sebuah objek _nullable_. Namun penggunaan operator tersebut **sangat tidak disarankan** karena akan memaksa sebuah objek menjadi _non-null_.

## String Template
>> [UP](#daftar-isi)

**_String Template_** merupakan sebuah fitur yang memungkinkan kita untuk menyisipkan sebuah variabel ke dalam sebuah String tanpa _**concatenation**_ (penggabungan objek `String` menggunakan `+`) seperti berikut:

```
fun main() {
    val name = "Kotlin"
    print("My name is " + name)
}
/*
   output : My name is Kotlin
*/
```

Untuk menggunakan **_string template_**, kita hanya perlu menambahkan karakter `$` sebelum nama variabel yang akan disisipkan seperti berikut:

```
  fun main() {
    val name = "Kotlin"
    print("My name is $name")
}
/*
   output : My name is Kotlin
*/
```

Variabel yang dapat disisipkan tidak sebatas `String`. Kita juga bisa menyisipkan objek lain misal `Int` atau `Double` seperti berikut:

```
fun main() {
    val name = "Jons"
    val old = 16
    print("My name is $name, im $old years old")
}
/*
   output : My name is Jons, im 16 years old
*/
```

**_String template_** juga bisa menyisipkan sebuah **expression** ke dalam sebuah string template. 

Caranya, sisipkan expression ke dalam **_curly braces**_ yang diikuti karakter `$`.

```
fun main() {
    val hour = 7
    print("Office ${if (hour > 7) "already close" else "is open"}")
}

/*
   output : Office is open
*/
```

Dengan String template, mudahkan membuat objek `String` yang dinamis.