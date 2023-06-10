> ## Fundamental Kotlin

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
10. [Safe Call](#safe-call)
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


## Numbers
>> [UP](#daftar-isi)
## Arrays
>> [UP](#daftar-isi)
## Tipe Nullable
>> [UP](#daftar-isi)
## Safe Call
>> [UP](#daftar-isi)
## String Template
>> [UP](#daftar-isi)
