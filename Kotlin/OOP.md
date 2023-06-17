> ## Object-Oriented Programming (OOP)

## Daftar Isi
1. [Konsep Object-Oriented Programing](#konsep-object-oriented-programing)
2. [Object Everywhere](#object-everywhere)
3. [Class](#class)
4. [Membuat Class](#membuat-class)
5. [Properties](#properties)
6. [Property Delegation](#property-delegation)
7. [Extension Properties](#extension-properties)
8. [Primary Constructor](#primary-constructor)
9. [Secondary Constructor](#secondary-constructor)
10. [Visibility Modifier](#visibility-modifier)
11. [Inheritances](#inheritances)
12. [Overloading](#overloading)
13. [Abstract Class](#abstract-class)
14. [Interfaces](#interfaces)
15. [Import dan Packages](#import-dan-packages)
16. [Membuat Object Baru](#membuat-package-baru)
17. [Exception](#exception)
18. [Exception Handling](#exception-handling)


## Konsep Object-Oriented Programing
>> [UP](#daftar-isi)

Kita telah mempelajari di sub-modul sebelumnya bahwa Kotlin mendukung pengembangan program berorientasi objek dengan sangat baik. Hal ini dikarenakan OOP masih menjadi paradigma atau teknik pemrograman yang populer dalam pengembangan aplikasi. Paradigma OOP memungkinkan kita untuk memvisualisasikan kode dengan mudah karena mirip dengan situasi dalam kehidupan nyata.

![Scenario OOP](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20190430142436d1d3240f3e0d70090704499c40954776.png)

Gambaran di atas mengilustrasikan konsep umum OOP, di mana ada sebuah gambaran dasar tentang mobil, komponen yang ada dalam mobil, dan kemampuan yang dapat dilakukan oleh mobil tersebut. Dalam OOP, gambaran dasar ini dikenal sebagai **Class** (kelas), komponen yang ada dikenal sebagai atribut, kemampuan yang dimiliki dikenal sebagai perilaku (behavior), dan hasil nyata dari gambaran dasar tersebut disebut **objek**.

Pada bagian ini, kami akan mengulas secara mendalam mengenai **objek, kelas, atribut,** dan **perilaku** yang ada dalam OOP.


## Object Everywhere
>> [UP](#daftar-isi)

Dalam sub-modul **Data Types**, dijelaskan bahwa dalam Kotlin, semua hal berperan sebagai objek, yang memungkinkan kita untuk memanggil _fungsi anggota_ dan properti dari sebuah variabel. Objek sendiri merupakan hasil nyata dari sebuah _blueprint_ atau _kelas_, yang memiliki fungsi dan properti yang sama dengan _blueprint_ tersebut. Dengan membuat objek, kita dapat mengakses fungsi dan properti yang terdapat dalam kelas tersebut.

Di Kotlin, tipe data primitif seperti **String, Integer, Char, dan Boolean** dianggap sebagai **objek**. Ini merupakan perbedaan dengan bahasa pemrograman lainnya. Oleh karena itu, terdapat istilah yang terkenal dalam Kotlin yaitu **"Object Everywhere"**. Berikut adalah contoh kode yang dapat diperhatikan:

```
val someString = “Amoled”
```

Dalam kode tersebut, kita membuat sebuah variabel bernama `someString` yang juga merupakan objek. Objek tersebut adalah hasil konkret dari kelas `String`, sehingga objek `someString` memiliki fungsi dan properti yang merupakan anggota dari kelas `String`.

![Completion Sugestion](https://d17ivq9b7rppb3.cloudfront.net/original/academy/202007010844593d92b258aea10a4c158d1ecd6089c5f5.png)

Dari daftar saran penyelesaian yang tersedia di IntelliJ Idea, kita dapat melihat beberapa fungsi yang dapat digunakan pada objek `someString`. Misalnya, kita dapat menggunakan fungsi `reverse()` untuk mengubah urutan huruf menjadi terbalik, fungsi `toUpperCase()` untuk mengubah huruf menjadi huruf kapital, atau fungsi `toLowerCase()` untuk mengubah huruf menjadi huruf kecil.

```
    fun main() {
    val someString = "Amoled"
    println(someString.reversed())
    println(someString.toUpperCase())
    println(someString.toLowerCase())
}
 
/*
Output:
delomA
AMOLED
amomled
*/
```

Selain itu, kita juga memiliki kemampuan untuk mengubah tipe data dengan menggunakan fungsi-fungsi yang tersedia pada objek String.

```
    fun main() {
    val someString = "123"
    val someInt = someString.toInt()
    val someOtherString = "12.34"
    val someDouble = someOtherString.toDouble()
 
    println(someInt is Int)
    println(someDouble is Double)
}
 
/*
Output:
 
true
true
*/
```

Output kode menunjukkan bahwa nilai true diperoleh pada kedua variabel tersebut, yang menunjukkan bahwa kita berhasil mengubah tipe data dari String ke tipe data lain menggunakan fungsi yang ada pada objek String.

Mungkin inilah konsep dasar mengenai objek. Penting untuk dicatat bahwa objek adalah hasil nyata dari sebuah blueprint yang memiliki properti dan fungsi yang serupa dengan blueprint tersebut. Salah satu manfaat utama objek adalah untuk mengakses berbagai properti dan fungsi yang ada pada kelas.


## Class
>> [UP](#daftar-isi)

Seperti yang telah dijelaskan sebelumnya mengenai konsep objek, **kelas** merupakan sebuah blueprint. Dalam kelas, kita mendefinisikan **atribut dan perilaku (behavior)**. Sebagai contoh, dalam kelas Kendaraan, atributnya bisa berupa roda, warna, nomor kendaraan, merk, dan sebagainya. Sedangkan perilaku atau behavior-nya meliputi kemampuan untuk maju, mundur, belok kanan, belok kiri, dan berhenti. Contoh lainnya adalah dalam kelas **Hewan**, atributnya bisa berupa nama, berat, umur, serta informasi apakah termasuk mamalia atau bukan. Sementara perilaku-nya dapat mencakup kemampuan untuk makan, tidur, berjalan, dan sebagainya.

Setiap kelas memiliki atribut dan perilaku. Dalam Kotlin, atribut lebih sering disebut sebagai **properti (properties)**, sedangkan perilaku lebih sering disebut sebagai **fungsi (functions)**. Properti dalam sebuah kelas memiliki tipe data tertentu. Sebagai contoh, dalam kelas Hewan, properti berat dapat memiliki tipe data **Double**, properti nama dapat memiliki tipe data **String**, properti umur dapat memiliki tipe data **Int**, dan properti indikasi mamalia dapat memiliki tipe data **Boolean**. Jika kita menggambarkan kelas Hewan dalam bentuk tabel, akan terlihat seperti berikut:

Berikut adalah tabel dalam format Markdown dengan detail yang Anda berikan:

| Animal           |                 
|------------------|
| name:String      |           
| weight:Double    |           
| age:Int          |              
| isMammal:Boolean |         
| eat()            |                 
| sleep()          |                

`+merupakan properti`

`-merupakan fungsi`

+ **Class**: Merupakan sebuah blueprint yang terdapat properti dan fungsi di dalamnya

+ **Properties**: Karakteristik dari sebuah kelas, memiliki tipe data.

+ **Functions**: Kemampuan atau aksi dari sebuah kelas.


## Membuat Class
>> [UP](#daftar-isi)

Untuk membuat definisi kelas dalam Kotlin, Anda hanya perlu menggunakan kata kunci `"class"` diikuti dengan nama kelas yang ingin Anda buat. Mari kita contohkan pembuatan kelas dalam Kotlin:

```
class Animal
```

Sekarang kita tambahkan properti dan fungsi pada kelas tersebut.

```
class Animal(val name: String,
             val weight: Double,
             val age: Int,
             val isMammal: Boolean
) {
 
    fun eat(){
        println("$name makan !")
    }
 
    fun sleep() {
        println("$name tidur !")
    }
}
```

Lalu untuk membuat sebuah objek dari suatu kelas, Anda bisa perhatikan struktur kode berikut:

```
val nameOfObject = NameOfClass([property1], [property2])
```

Mirip dengan variabel, kita dapat menggunakan `"val" atau "var"` diikuti dengan nama objek yang ingin Anda buat. Tanda `"="` menunjukkan bahwa kita akan menginisialisasi objek tersebut, dan kemudian diikuti dengan nama kelas dan tanda kurung. Tanda kurung tersebut menunjukkan bahwa kita sedang membuat sebuah objek baru. Di dalam tanda kurung, kita dapat menambahkan nilai-nilai properti sesuai dengan kebutuhan pada **Primary Constructor**.

Jika kita mencoba membuat objek dari kelas yang telah kita buat, kode akan terlihat seperti berikut:Jika kita mencoba membuat objek dari kelas yang telah kita buat, kode akan terlihat seperti berikut:

```
val amoledCat = Animal("Dicoding Miaw", 4.2, 2,true)
```

Berikut adalah contoh kode lengkap yang mencakup fungsi cetak untuk melihat nilai properti dalam objek:

```
class Animal(val name: String,
             val weight: Double,
             val age: Int,
             val isMammal: Boolean
) {
 
    fun eat(){
        println("$name makan!")
    }
 
    fun sleep() {
        println("$name tidur!")
    }
}
 
fun main() {
    val amoledCat = Animal("Amoled Miaw", 4.2, 2,true)
    println("Nama: ${amoledCat.name}, Berat: ${amoledCat.weight}, Umur: ${amoledCat.age}, mamalia: ${amoledCat.isMammal}" )
    amoledCat.eat()
    amoledCat.sleep()
}

output:
Nama: Amoled Miaw, Berat: 4.2, Umur: 2, mamalia: true
Amoled Miaw makan!
Amoled Miaw tidur!
```


## Properties
>> [UP](#daftar-isi)

Setiap kelas dalam Kotlin memiliki properti yang unik. Sebagai contoh, pada kelas `Animal` yang telah disebutkan sebelumnya, terdapat properti seperti `name` (nama), `weight` (berat), `age` (umur), dan `isMammal` (indikasi mamalia).

Seperti yang telah kita pelajari pada sub-modul Data Types, properti dalam Kotlin dapat dideklarasikan sebagai nilai yang dapat diubah (mutable) dengan menggunakan `"var"` atau sebagai nilai yang hanya dapat dibaca (read-only) dengan menggunakan `"val"`.

### Property Accessor
Secara default, ketika sebuah properti dalam sebuah kelas dideklarasikan sebagai mutable, Kotlin akan secara otomatis menghasilkan fungsi getter dan setter untuk properti tersebut. Namun, jika properti dalam sebuah kelas dideklarasikan sebagai read-only, Kotlin hanya akan menghasilkan fungsi getter untuk properti tersebut. Meskipun demikian, Anda masih memiliki kemampuan untuk membuat fungsi getter dan setter secara manual jika diperlukan dalam situasi tertentu dengan melakukan override pada fungsi-fungsi tersebut.

Perhatikan kode berikut:

```
class Animal{
    var name: String = "Amoled Miaw"
}
 
fun main(){
    val amoledCat = Animal()
    println("Nama: ${amoledCat.name}" )
    amoledCat.name = "Skuyy"
    println("Nama: ${amoledCat.name}")
}
 
/*
output:
Nama: amoled Miaw
Nama: Skuyy
*/
```

Pada kode `${dicodingCat.name}`, sebenarnya terjadi pemanggilan fungsi _getter_ pada properti `name`. Namun, kita tidak melakukan _override_ pada fungsi _getter_ tersebut, sehingga fungsi tersebut hanya mengembalikan nilai `name` saja. Demikian juga pada kode `dicodingCat.name = "Skuyy"`, terjadi pemanggilan fungsi _setter_ pada properti `name`.

Namun, jika kita melakukan _override_ pada fungsi _getter_ dan _setter_, kita dapat menambahkan kode tambahan dalam fungsi _getter_ sesuai dengan kebutuhan. Mari kita coba memodifikasi kode sebelumnya menjadi sebagai berikut:

```
class Animal{
    var name: String = "Amoled Miaw"
        get(){
            println("Fungsi Getter terpanggil")
            return field
        }
        set(value){
            println("Fungsi Setter terpanggil")
            field = value
        }
}
 
fun main(){
    val amoledCat = Animal()
    println("Nama: ${amoledCat.name}" )
    amoledCat.name = "Skuyy"
    println("Nama: ${amoledCat.name}")
}
 
/*
output:
Fungsi Getter terpanggil
Nama: Amoled Miaw
Fungsi Setter terpanggil
Fungsi Getter terpanggil
Nama: Skuyy
*/
```

Urutan pendefinisian fungsi `get()` dan `set()` tidaklah penting, kita dapat mendefinisikan fungsi `get()` tanpa mendefinisikan fungsi `set()`, dan sebaliknya. Yang terpenting, pendefinisian tersebut dilakukan setelah mendeklarasikan properti tersebut. Dalam fungsi `get()`, kita perlu mengembalikan nilai sesuai dengan tipe data properti, atau kita dapat mengembalikan nilai dari properti itu sendiri menggunakan kata kunci `"field"`. Sedangkan dalam fungsi `set()`, kita memerlukan sebuah parameter yang merupakan nilai baru yang akan dijadikan nilai properti. Pada contoh kode sebelumnya, parameter tersebut diberi nama `"value"`.


## Property Delegation
>> [UP](#daftar-isi)

Penanganan properti dalam sebuah kelas, baik dalam memberikan nilai awal atau merubah nilainya, dapat didelegasikan kepada kelas lain. Dengan demikian, kita dapat mengurangi repetisi kode yang umumnya terjadi saat menulis _getter_ dan _setter_ (jika properti menggunakan **"var"**) di setiap kelas yang kita buat. Sebagai contoh, kita memiliki tiga kelas yang masing-masing memiliki satu properti String. Jika kita ingin menerapkan _getter_ dan _setter_ pada setiap properti kelas, maka kita perlu menulis _getter_ dan _setter_ tersebut di setiap kelas, yang dapat mengurangi efisiensi penulisan kode karena adanya repetisi yang berlebihan. Untuk mengatasi hal ini, kita dapat membuat kelas yang bertugas mengatur atau mengelola fungsi _getter_ dan _setter_ untuk sebuah properti kelas. Teknik ini disebut **"Delegate"** dalam Kotlin.

Sebelum melakukan delegasi properti, langkah pertama adalah membuat kelas delegasi terlebih dahulu. Mari kita buat sebuah kelas delegasi.

```
import kotlin.reflect.KProperty
 
 
class DelegateName {
    private var value: String = "Default"
 
    operator fun getValue(classRef: Any?, property: KProperty<*>) : String {
        println("Fungsi ini sama seperti getter untuk properti ${property.name} pada class $classRef")
        return value
    }
 
    operator fun setValue(classRef: Any?, property: KProperty<*>, newValue: String){
        println("Fungsi ini sama seperti setter untuk properti ${property.name} pada class $classRef")
        println("Nilai ${property.name} dari: $value akan berubah menjadi $newValue")
        value = newValue
    }
}
```

Selanjutnya, untuk mendelegasikan sebuah properti dalam kelas, kita menggunakan kata kunci `"by"` saat menginisialisasi properti tersebut, diikuti dengan nama kelas delegasi. Berikut adalah contoh kode:

```
class Animal {
    var name: String by DelegateName()
}
```

Dengan menggunakan pendekatan tersebut, nilai properti `"name"` dikelola melalui kelas `"DelegateName"`. Kita dapat melakukan delegasi terhadap banyak properti dari berbagai kelas ke dalam satu kelas "Delegate" yang sama. Berikut adalah contoh kode yang lebih jelas untuk ilustrasinya:

```
class Animal {
    var name: String by DelegateName()
}
 
class Person {
    var name: String by DelegateName()
}
 
class Hero {
    var name: String by DelegateName()
}
```

Ayo kita buat sebuah objek, ubah nilai propertinya, dan mengakses nilai propertinya di setiap kelas, lalu jalankan programnya. Hasilnya akan seperti yang ditunjukkan dalam kode berikut:

```
fun main() {
    val animal = Animal()
    animal.name = "Amoled Miaw"
    println("Nama Hewan: ${animal.name}")
 
    val person = Person()
    person.name = "Diki"
    println("Nama Orang: ${person.name}")
 
    val hero = Hero()
    hero.name = "Supermi"
    println("Nama Pahlawan: ${hero.name}")
}
 
/*
output:
    Fungsi ini sama seperti setter untuk properti name pada class Animal@17f052a3
    Nilai name dari: Default akan berubah menjadi Amoled Miaw
    Fungsi ini sama seperti getter untuk properti name pada class Animal@17f052a3
    Nama Hewan: Amoled Miaw
    Fungsi ini sama seperti setter untuk properti name pada class Person@2e0fa5d3
    Nilai name dari: Default akan berubah menjadi Diki
    Fungsi ini sama seperti getter untuk properti name pada class Person@2e0fa5d3
    Nama Orang: Diki
    Fungsi ini sama seperti setter untuk properti name pada class Hero@5010be6
    Nilai name dari: Default akan berubah menjadi Supermi
    Fungsi ini sama seperti getter untuk properti name pada class Hero@5010be6
    Nama Pahlawan: Supermi
*/
```

Pada contoh di atas, delegasi hanya diterapkan pada properti dengan tipe data String. Namun, kita juga dapat membuat sebuah kelas delegasi yang bersifat umum dan dapat digunakan oleh semua tipe data dengan menggunakan tipe data `Any`.

```
class DelegateGenericClass {
    private var value: Any = "Default"
 
    operator fun getValue(classRef: Any, property: KProperty<*>): Any {
        println("Fungsi ini sama seperti getter untuk properti ${property.name} pada class $classRef")
        return value
    }
 
    operator fun setValue(classRef: Any, property: KProperty<*>, newValue: Any) {
        println("Nilai ${property.name} dari: $value akan berubah menjadi $newValue")
        value = newValue
    }
}
 
class Animal {
    var name: Any by DelegateGenericClass()
    var weight: Any by DelegateGenericClass()
    var age: Any by DelegateGenericClass()
}
```

Selanjutnya, mari kita buat sebuah objek dari kelas `Animal`, lakukan perubahan dan akses nilai propertinya, lalu jalankan programnya. Hasilnya akan sama seperti yang ditunjukkan dalam kode berikut:

```
fun main(){
    val animal = Animal()
    animal.name = "Amoled cat"
    animal.weight = 6.2
    animal.age = 1
 
    println("Nama: ${animal.name}")
    println("Berat: ${animal.weight}")
    println("Umur: ${animal.age} Tahun")
}
 
/*
output:
    Nilai name dari: Default akan berubah menjadi Amoled cat
    Nilai weight dari: Default akan berubah menjadi 6.2
    Nilai age dari: Default akan berubah menjadi 1
    Fungsi ini sama seperti getter untuk properti name pada class Animal@17f052a3
    Nama: Amoled cat
    Fungsi ini sama seperti getter untuk properti weight pada class Animal@17f052a3
    Berat: 6.2
    Fungsi ini sama seperti getter untuk properti age pada class Animal@17f052a3
    Umur: 1 Tahun
*/
```

Perhatikanlah kode di atas, di mana kita memberikan nilai kepada setiap properti dengan tipe data yang berbeda. Namun, dengan menggunakan `DelegateGenericClass()`, pengelolaan properti dapat diterapkan pada semua tipe data properti.


## Extension Properties
>> [UP](#daftar-isi)

Dalam materi Functional Programming Kotlin, kita telah mempelajari bahwa Kotlin memungkinkan kita untuk memperluas (extends) fungsi pada sebuah kelas tanpa harus mewarisi (inherit) kelas tersebut. Hal ini dapat dilakukan melalui deklarasi khusus yang disebut dengan **Extension**.

Extension properties dalam Kotlin memiliki fungsi yang serupa dengan Extension function. Kita dapat menambahkan properti baru tanpa perlu membuat kelas yang mewarisi kelas tersebut. Namun, perlu diingat bahwa properti yang kita tambahkan sebenarnya tidak benar-benar berada di dalam kelas tersebut. Extension properties dideklarasikan di luar kelas. Oleh karena itu, Extension properties hanya dapat didefinisikan dengan cara menyediakan getter dan/atau setter secara eksplisit. Mari kita buat sebuah Extension properties pada kelas `Animal`.

```
class Animal(var name: String, var weight: Double, var age: Int, var isMammal: Boolean)
 
val Animal.getAnimalInfo : String
    get() =  "Nama: ${this.name}, Berat: ${this.weight}, Umur: ${this.age} Mamalia: ${this.isMammal}"
```

Dengan menambahkan Extension properties `getAnimalInfo` pada kelas `Animal`, kita dapat menggunakan properti tersebut pada sebuah objek kelas `Animal`.

```
fun main() {
    val amoledCat = Animal("Amoled Miaw", 5.0, 2, true)
    println(amoledCat.getAnimalInfo)
}

output:
Nama: Dicoding Miaw, Berat: 5.0, Umur: 2 Mammalia: true
```


## Primary Constructor
>> [UP](#daftar-isi)

Seperti yang disebutkan namanya, ketika kita ingin membuat objek dari sebuah kelas yang memiliki constructor utama (primary constructor), kita perlu memberikan nilai sesuai dengan properti yang diperlukan. Penulisan primary constructor mirip dengan parameter dalam sebuah fungsi. Properti dapat dituliskan dalam header class dan diawali dengan `var` atau `val`. Berikut adalah contoh kode:

```
class Animal(val name: String, val weight: Double, val age: Int, val isMammal: Boolean)
```

Pada baris kode tersebut, kita tidak hanya membuat sebuah kelas, tetapi juga menambahkan sebuah constructor utama _(primary constructor)_ pada kelas tersebut. Sekarang mari kita mencoba membuat objek dari kelas tersebut:

```
fun main(){
    val amoledCat = Animal("Amoled Miaw", 4.2, 2, true)
    println("Nama: ${amoledCat.name}, Berat: ${amoledCat.weight}, Umur: ${amoledCat.age}, mamalia: ${amoledCat.isMammal}" )
}
 
/*
output:
    Nama: Amoled Miaw, Berat: 4.2, Umur: 2, mamalia: true
*/
```

Perhatikan kode di atas. Karena kelas `Animal` memiliki constructor utama (primary constructor), saat membuat objek dari kelas tersebut, kita perlu menyediakan beberapa nilai seperti `  name`, `weight`, `age`, dan `isMammal`.

Primary constructor juga dapat memiliki nilai default. Dengan ini, jika kita tidak memberikan nilai untuk parameter tersebut saat pembuatan objek, properti akan menggunakan nilai default yang telah ditentukan. Sebagai contoh, kita dapat memberikan nilai default untuk properti `age`. Dengan demikian, saat membuat objek, pengiriman nilai `age` pada primary constructor menjadi opsional.

```
class Animal(var name: String, var weight: Double, var age: Int = 0, var isMammal: Boolean = true)
```

Kode di atas menunjukkan bahwa kita memberikan nilai `default 0` untuk properti `age` dan true untuk properti `isMammal`. Oleh karena itu, saat membuat objek **Animal**, kita hanya perlu mengirimkan nilai `name` dan `weight` ke primary constructor. Mari kita mencoba membuat objek dengan memanfaatkan nilai default pada konstruktor.

```
fun main(){
    val amoledCat = Animal("Amoled Miaw", 4.2)
    println("Nama: ${amoledCat.name}, Berat: ${amoledCat.weight}, Umur: ${amoledCat.age}, mamalia: ${amoledCat.isMammal}" )
}
 
/*
 output:
    Nama: Amoled Miaw, Berat: 4.2, Umur: 0, mamalia: true
*/
```

Output dari kode tersebut menunjukkan bahwa properti `age` dan `isMammal` memiliki nilai default. Penting untuk diingat bahwa properti tersebut bersifat **opsional**, yang berarti kita masih dapat mengirimkan nilai ke properti tersebut meskipun mereka memiliki nilai default.

Kita juga dapat secara eksplisit memilih properti yang ingin kita berikan nilai dengan menambahkan nama properti dan tanda = sebelum mengisikan nilai properti.

```
val dicodingCat = Animal("Dicoding Miaw", 4.2, isMammal =  true)
```

### Init Block

Kotlin menyediakan blok **init**, yang memungkinkan kita untuk menulis kode di dalam body kelas ketika menggunakan primary constructor. Memang, memiliki banyak kode di dalam body kelas bukanlah hal yang baik. Kotlin bertujuan agar kita dapat menulis kode secara ringkas. Namun, blok **init** memiliki beberapa fungsi selain menginisialisasi properti kelas. Salah satu fungsinya adalah untuk membantu dalam memvalidasi nilai properti sebelum diinisialisasi. Pada contoh kelas `Animal`, misalnya, kita dapat memverifikasi bahwa berat dan usia hewan tidak boleh kurang dari nol.

Untuk membuatnya, kita dapat menggunakan kata kunci `init` dan kemudian menginisialisasi semua properti di dalam blok tersebut dengan parameter kelas:

```
class Animal(pName: String, pWeight: Double, pAge: Int, pIsMammal: Boolean){
    val name: String
    val weight: Double
    val age: Int
    val isMammal: Boolean
 
    init {
        weight = if(pWeight < 0) 0.1 else pWeight
        age = if(pAge < 0) 0 else pAge
        name = pName
        isMammal = pIsMammal
    }
}
```

Primary constructor dan `init` harus saling terhubung. Fungsi `init` dijalankan ketika suatu objek dibuat dengan menggunakan primary constructor. Mari kita coba untuk membuatnya.

```
fun main() {
    val amoledCat = Animal("Amoled Miaw", 4.2, 2, true)
    println("Nama: ${amoledCat.name}, Berat: ${amoledCat.weight}, Umur: ${amoledCat.age}, mamalia: ${amoledCat.isMammal}")
}
 
/*
output:
    Nama: Amoled Miaw, Berat: 4.2, Umur: 2, mamalia: true
*/
```

Perhatikan juga bahwa penamaan properti di dalam body class dan parameter di dalam header class harus berbeda agar tidak terjadi ambiguitas. Namun, jika kita ingin menggunakan penamaan yang sama, kita dapat menggunakan kata kunci `this` untuk merujuk pada properti yang sama dalam inisialisasi di blok `init`.

```
class Animal(name: String, weight: Double, age: Int, isMammal: Boolean) {
    val name: String
    val weight: Double
    val age: Int
    val isMammal: Boolean
 
    init {
        this.weight = if(weight < 0) 0.1 else weight
        this.age = if(age < 0) 0  else age
        this.name = name
        this.isMammal = isMammal
    }
}
```

Kata kunci `"this"` merujuk pada kelas itu sendiri. Jika kita menggunakannya diikuti dengan nama properti, kita merujuk pada properti yang ada di dalam kelas tersebut. Dengan menggunakan `"this"`, kita dapat menghindari ambiguitas meskipun kita menggunakan penamaan yang sama antara properti dan parameter _primary constructor_.


## Secondary Constructor
>> [UP](#daftar-isi)

Anda dapat menggunakan `secondary constructor` saat ingin melakukan inisialisasi kelas dengan pendekatan yang berbeda. Kemampuan untuk membuat beberapa secondary constructor juga dimungkinkan. Sebagai contoh, dalam kelas `Animal`, kita dapat menambahkan `secondary constructor`.

```
class Animal(name: String, weight: Double, age: Int) {
    val name: String
    val weight: Double
    val age: Int
    var isMammal: Boolean
 
    init {
        this.weight = if(weight < 0) 0.1 else weight
        this.age = if(age < 0) 0  else age
        this.name = name
        this.isMammal = false
    }
 
    constructor(name: String, weight: Double, age: Int, isMammal: Boolean) : this(name, weight, age) {
        this.isMammal = isMammal
    }
}
 
fun main() {
    val amoledCat = Animal("Amoled Miaw", 2.5, 2, true)
    println("Nama: ${amoledCat.name}, Berat: ${amoledCat.weight}, Umur: ${amoledCat.age}, mamalia: ${amoledCat.isMammal}")
 
    val amoledBird = Animal("Amoled tweet", 0.5, 1)
    println("Nama: ${amoledBird.name}, Berat: ${amoledBird.weight}, Umur: ${amoledBird.age}, mamalia: ${amoledBird.isMammal}")
}
 
/*
output:
    Nama: Amoled Miaw, Berat: 2.5, Umur: 2, mamalia: true
    Nama: Amoled tweet, Berat: 0.5, Umur: 1, mamalia: false
*/
```

Dengan begitu, objek Animal dapat diinisialisasi dengan secondary constructor ketika nilai `name`, `weight`, `age` dan `isMammal` tersedia. Tetapi jika nilai `isMammal` tidak tersedia,  primary constructor lah yang akan digunakan dan nilai `isMammal` dapat diinisialisasi pada blok **init** dengan nilai default.

### Default Constructor

Jika kita tidak secara manual membuat konstruktor, Kotlin akan secara otomatis membuat sebuah konstruktor default pada kelas. Contoh kode berikut ini perlu diperhatikan:

```
class Animal{
    val name: String = "Amoled Miaw"
    val weight: Double = 4.2
    val age: Int = 2
    val isMammal: Boolean = true
}
 
fun main(){
    val amoledCat = Animal()
    println("Nama: ${amoledCat.name}, Berat: ${amoledCat.weight}, Umur: ${amoledCat.age}, mamalia: ${amoledCat.isMammal}" )
}
 
/*
output:
    Nama: Dicoding Miaw, Berat: 4.2, Umur: 2, mamalia: true
*/
```

Saat objek dibuat, konstruktor default akan dipanggil dan bertanggung jawab untuk menginisialisasi properti kelas dengan nilai default yang telah ditentukan.


## Visibility Modifier
>> [UP](#daftar-isi)

Pada kali ini, kita akan mempelajari tentang modifier visibilitas atau aksesibilitas dalam Kotlin. Tidak semua properti dan fungsi dalam sebuah kelas memiliki aksesibilitas publik. Beberapa dari mereka hanya dapat diakses dari dalam kelas itu sendiri, sementara yang lain dapat diakses dari luar kelas. Dengan menggunakan modifier visibilitas ini, kita dapat membatasi akses data dalam sebuah kelas. Berikut adalah beberapa jenis modifier visibilitas beserta penjelasan singkat yang dapat digunakan dalam Kotlin:

+ **Public**: Hak akses yang cakupannya paling luas. Anggota yang diberi modifier ini dapat diakses dari manapun.

+ **Private**: Hak akses yang cakupannya paling terbatas. Anggota yang menerapkannya hanya dapat diakses pada scope yang sama.

+ **Protected**: Hak akses yang cakupannya terbatas pada hirarki kelas. Anggota hanya dapat diakses pada kelas turunannya atau kelas itu sendiri.

+ **Internal**: Hak akses yang cakupannya terbatas pada satu modul. Anggota yang menggunakannya tidak dapat diakses diluar dari modulnya tersebut.

### Public

Tidak seperti bahasa pemrograman umumnya, dalam Kotlin, modifier default adalah public. Jika suatu anggota memiliki hak akses public, maka anggota tersebut dapat diakses dari luar kelas melalui objek dari kelas tersebut.

Pada pembahasan sebelumnya kita sudah memiliki sebuah kelas `Animal` dengan properti publik seperti `name`, `age`, `weight` dan `isMammal`. Properti tersebut dapat kita akses dari luar kelas `Animal`.

![Completion Sugestion](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20190429171924c871aeea325dad57f899bd1964051bb8.png)

Dari completion suggestion terlihat bahwa properti tersebut dapat kita akses di luar dari kelasnya.

### Private

Apabila sebuah anggota memiliki hak akses private, maka anggota tersebut tidak dapat diakses dari luar ruang lingkupnya. Untuk menggunakan modifier private, kita perlu menambahkan kata kunci private seperti pada contoh berikut ini:

```
private var name: String
```

Mari kita coba ubah hak akses pada seluruh properti kelas `Animal` menjadi private.

```
class Animal(private val name: String, private val weight: Double, private val age: Int, private val isMammal: Boolean)
 
fun main() {
    val amoledCat = Amoled("Dicoding Miaw", 2.5, 2)
    println("Nama: ${amoledCat.name}, Berat: ${amoledCat.weight}, Umur: ${amoledCat.age}, mamalia: ${amoledCat.isMammal}")
```

Dengan menggunakan hak akses private, kita tidak diizinkan untuk mengakses properti dalam kelas `Animal` tersebut dari luar kelasnya. Anda akan menghadapi pesan kesalahan `"Cannot access '[PROPERTY]': it is private in 'Animal'"`. Satu-satunya cara untuk mengakses properti private dari sebuah kelas adalah dengan menambahkan manual fungsi getter dan setter. Secara default, Kotlin menghasilkan fungsi getter dan setter secara otomatis ketika properti memiliki hak akses public, tetapi tidak untuk hak akses private. Untuk menuliskan getter dan setter pada hak akses private, caranya sama seperti menulis fungsi pada umumnya:

```
fun getName() : String {
    return name
}
 
fun setName(newName: String) {
    name = newName
}
```

Fungsi `getName()` bertujuan untuk mengembalikan nilai `name` yang memiliki tipe data String. Kemudian fungsi `setName()` bertujuan untuk mengubah nilai properti `name` dengan nilai baru. Fungsi `setName()` membutuhkan satu parameter bertipe String yang nantinya akan dimasukkan nilainya ke dalam properti `name`.

Mari kita coba menerapkannya.

```
class Animal(private var name: String, private val weight: Double, private val age: Int, private val isMammal: Boolean = true) {
 
    fun getName() : String {
        return name
    }
 
    fun setName(newName: String) {
        name = newName
    }
 
}
 
fun main() {
    val amoledCat = Animal("Amoled Miaw", 2.5, 2)
    println(amoledCat.getName())
    amoledCat.setName("skuyy")
    println(amoledCat.getName())
}
 
/*
output:
    Amoled Miaw
    Skuyy
*/
```

Dalam kode di atas, dapat dilihat bahwa kita berhasil mengubah nilai properti `name` dari nilai awal yang diinisialisasi dalam konstruktor. Nilai tersebut diubah menjadi nilai baru yang ditentukan menggunakan fungsi `setName()`.

### Protected

Hak akses **protected** memiliki kesamaan dengan **private**, namun batasan aksesnya lebih luas dalam hierarki kelas. Hak akses protected digunakan ketika kita ingin anggota dari kelas induk hanya dapat diakses oleh kelas-kelas turunannya. Silakan perhatikan kode berikut ini sebagai contoh penggunaan hak akses protected.

```
open class Animal(val name: String, protected val weight: Double)
 
class Cat(pName: String, pWeight: Double) : Animal(pName, pWeight)
```

Dalam kode tersebut, terdapat properti `weight` pada kelas `Animal` dengan hak akses protected. Meskipun demikian, kita masih dapat mengakses properti tersebut dari kelas `Cat` yang merupakan turunan dari kelas `Animal`. Namun, kita tidak dapat mengakses properti tersebut secara langsung dari luar hierarki kelasnya. Jika kita mencoba melakukannya, akan terjadi kesalahan (error).

```
fun main() {
    val cat = Cat("Amoled Miaw", 2.0)
    println("Nama Kucing: ${cat.name}")
    println("Berat Kucing: ${cat.weight}") //Cannot access 'weight': it is protected in 'Cat'
}
```

### Internal

Internal adalah salah satu hak akses baru yang diperkenalkan dalam Kotlin. Hak akses ini membatasi aksesibilitas suatu anggota hanya pada satu modul. Berikut ini adalah contoh penggunaan hak akses internal:

```
internal class Animal(val name: String)
```

Pada contoh di atas, kelas Animal telah diberi hak akses internal, yang berarti kelas tersebut hanya dapat diakses dari modul yang sama. Hak akses ini sangat bermanfaat ketika kita mengembangkan aplikasi dengan beberapa modul di dalamnya.


## Inheritances
>> [UP](#daftar-isi)

Dalam kehidupan nyata, terdapat banyak objek yang beragam namun memiliki beberapa kesamaan atau kemiripan. Sebagai contoh, kucing dan kambing memiliki banyak kesamaan karena keduanya adalah hewan. Baik kucing maupun kambing adalah mamalia. Perbedaan antara keduanya mungkin terletak pada cara mereka mencari makanan dan jenis makanan yang mereka konsumsi. Konsep yang serupa juga diterapkan dalam pemrograman berorientasi objek (OOP), di mana beberapa objek yang berbeda dapat memiliki kesamaan dalam beberapa aspek. Inilah mengapa konsep **pewarisan** atau **inheritance** sangat penting. Melalui pewarisan, kita dapat mencegah pengulangan kode yang tidak perlu. Untuk memberikan gambaran lebih jelas, berikut ini adalah contoh diagram kelas:

|   Cat   |   Fish   |  Snake   |
|:-------:|:-------:|:-------:|
| name: String | name: String | name: String |
| furColor: String | scaleColor: String | skinColor: String |
| weight: Double | weight: Double | weight: Double |
| age: Integer | age: Integer | age: Integer |
| numberOfFeet: Integer | numberOfFin: Integer | - |
| isCarnivore: Boolean | isCarnivore: Boolean | isToxic: Boolean |
| eat() | eat() | eat() |
| sleep() | sleep() | sleep() |
| playWithHuman() | swim() | bite() |

Dalam diagram tersebut, dapat diamati bahwa kelas-kelas `Cat`, `Fish`, dan `Snake` memiliki properti yang serupa seperti `name`, `weight`, `age`, dan `isCarnivore`. Selain itu, mereka juga memiliki fungsi yang serupa seperti `eat()` dan `sleep()`. Jika kita mengonversi diagram kelas Cat menjadi kode, maka akan terlihat seperti berikut ini:

```
class Cat(val name: String, val furColor: String, val weight: Double, val age: Integer, val numberOfFeet: Integer, val isCarnivore: Boolean) {
    fun eat(){
        println("$name sedang makan!")
    }
 
    fun sleep() {
        println("$name sedang tidur!")
    }
 
    fun playWithHuman() {
        println("$name bermain dengan Manusia!")
    }
}
```

Kode tersebut tidak menghadapi masalah tertentu, namun saat kita ingin membuat kelas baru berdasarkan diagram lain, misalnya `Fish`, kita harus menuliskan kembali properti seperti `name`, `weight`, `age`, dan properti atau fungsi yang sama lainnya. Hal ini dapat mengakibatkan penulisan kode menjadi kurang efisien.

Dengan menggunakan teknik inheritance, kita dapat mengelompokkan properti dan fungsi yang serupa. Caranya adalah dengan membuat sebuah kelas baru yang kemudian akan diwariskan sifatnya kepada kelas lainnya:

|   Animal   |
|:----------:|
| name: String |
| weight: Double |
| age: Integer |
| isCarnivore: Boolean |
| eat() |
| sleep() |

|   Cat   |   Fish   |  Snake  |
|:-------:|:-------:|:-------:|
| furColor: String | scaleColor: String | skinColor: String |
| numberOfFeet: Integer | numberOfFin: Integer | isToxic: Boolean |
| playWithHuman() | swim() | bite() |

Setelah kelas `Animal` dibuat, kelas lain dapat memperluas atau mewarisi dari kelas tersebut. Dalam konteks pewarisan, kelas `Animal` (kelas utama) dapat disebut sebagai kelas super atau kelas induk. Kelas yang melakukan pewarisan dari kelas tersebut disebut kelas anak atau kelas turunan. Dalam bahasa Kotlin, pewarisan dari sebuah kelas dapat dilakukan dengan menggunakan tanda `:` seperti yang ditunjukkan dalam contoh berikut:

```
class ChildClass : ParentClass {
 
}
```

Ayo kita buat sebuah kelas `Animal` yang akan berfungsi sebagai kelas induk seperti yang ditunjukkan di bawah ini:

```
open class Animal(val name: String, val weight: Double, val age: Int, val isCarnivore: Boolean){
 
    open fun eat(){
        println("$name sedang makan!")
    }
 
    open fun sleep(){
        println("$name sedang tidur!")
    }
}
```

Untuk membuat kelas super atau induk, kita perlu menggunakan kelas terbuka atau **open class**. Secara default, kelas-kelas dalam Kotlin bersifat `final`, sehingga kita perlu mengubahnya menjadi open class sebelum melakukan pewarisan atau extends dari kelas tersebut.

Ubahlah kelas `Cat` dengan melakukan extends pada kelas `Animal` seperti berikut:

```
class Cat(pName: String, pWeight: Double, pAge: Int, pIsCarnivore: Boolean, val furColor: String, val numberOfFeet: Int)
    : Animal(pName, pWeight, pAge, pIsCarnivore) {
 
    fun playWithHuman() {
        println("$name bermain bersama Manusia !")
    }
 
    override fun eat(){
        println("$name sedang memakan ikan !")
    }
 
    override fun sleep() {
        println("$name sedang tidur di bantal !")
    }
}
```

Dengan demikian, selain memiliki fungsi-fungsi yang dimilikinya sendiri, kelas `Cat` juga dapat mengakses semua fungsi dan properti yang ada di kelas `Animal`.

```
fun main(){
    val amoledCat = Cat("Amoled Miaw", 3.2, 2, true, "Brown", 4)
 
    amoledCat.playWithHuman()
    amoledCat.eat()
    amoledCat.sleep()
}
 
/*
output:
    Amoled Miaw bermain bersama Manusia !
    Amoled Miaw sedang memakan ikan !
    Amoled Miaw sedang tidur di bantal !
*/
```


## Overloading
>> [UP](#daftar-isi)

Dalam Kotlin, penggunaan dua atau lebih fungsi dengan nama yang sama disebut sebagai overloading. Overloading dapat dilakukan ketika fungsi-fungsi tersebut memiliki parameter-parameter yang berbeda. Berikut ini adalah contoh overloading fungsi `eat()` dalam sebuah kelas `Animal`.

```
class Animal(private var name: String) {
    fun eat() {
        println("$name makan!")
    }
 
    fun eat(typeFood: String) {
        println("$name memakan $typeFood!")
    }
 
    fun eat(typeFood: String, quantity: Double) {
        println("$name memakan $typeFood sebanyak $quantity grams!")
    }
 
    fun sleep() {
        println("$name tidur!")
    }
}
```

Di kelas `Animal`, terdapat beberapa fungsi dengan nama yang sama, namun hal ini tidak menyebabkan kesalahan atau error. Hal ini disebabkan oleh adanya perbedaan parameter pada setiap fungsi tersebut, sehingga tidak ada ambiguitas saat memanggil fungsi tersebut. Mari kita coba membuat sebuah objek dari kelas tersebut dan mengakses fungsi-fungsinya satu per satu.

```
fun main() {
    val amoledCat = Animal("Amoled Miaw")
 
    amoledCat.eat()
    amoledCat.eat("Ikan Tuna")
    amoledCat.eat("Ikan Tuna", 450.0)
}
```

Fungsi `eat()` pertama dapat digunakan tanpa perlu mengirimkan parameter apa pun. Sementara itu, fungsi `eat()` kedua membutuhkan parameter String yang akan digunakan sebagai nilai `typeFood`. Dan fungsi `eat()` terakhir membutuhkan 2 (dua) parameter, yaitu `typeFood` dan `quantity`.

Overloading pada fungsi adalah fitur yang sangat kuat. Untuk memahami betapa pentingnya overloading, mari kita buat sebuah kelas **Calculator** yang memiliki fungsi matematika dan menerapkan overloading pada salah satu fungsi tersebut.

```
class Calculator {
    fun add(value1: Int, value2: Int) = value1 + value2
    fun add(value1: Int, value2: Int, value3: Int) = value1 + value2 + value3
    fun add(value1: Double, value2: Double) = value1 + value2
    fun add(value1: Float, value2: Float) = value1 + value2
 
    fun min(value1: Int, value2: Int) = if (value1 < value2) value1 else value2
    fun min(value1: Double, value2: Double) = if (value1 < value2) value1 else value2
}
```

Selanjutnya, mari kita membuat sebuah objek `Calculator` dalam fungsi `main()` dan mengakses fungsi-fungsi yang ada di dalam kelas tersebut.

```
fun main() {
    val calc = Calculator()
 
    println(calc.add(2, 4))
    println(calc.add(2.5, 2.2))
    println(calc.add(6f, 7f))
    println(calc.add(1, 2, 3))
 
    println(calc.min(9, 2))
    println(calc.min(17.2, 18.3))
}
 
/*
output
    6
    4.7
    13.0
    6
    2
    17.2
*/
```

Pada contoh yang telah kita buat, ketika kita memanggil fungsi `add(2, 4)`, itu akan menjalankan fungsi `add` yang menerima parameter **Integer**. Sedangkan ketika kita memanggil fungsi `add(2.5, 2.2)`, itu akan menjalankan fungsi `add` yang menerima parameter **Double**. Hal yang sama juga berlaku untuk fungsi-fungsi lainnya.


## Abstract Class
>> [UP](#daftar-isi)

Seperti yang disiratkan oleh namanya, sebuah kelas **abstract** merupakan sebuah konsepsi umum dari suatu kelas. Kelas tersebut tidak dapat diinstansiasi menjadi sebuah objek. Pada sub-modul sebelumnya, kita telah membuat kelas `Animal`. Secara konkret, hewan adalah suatu sifat atau konsep. Kita mengetahui bagaimana kucing, ikan, dan ular terlihat, tetapi kita tidak memiliki gambaran konkret tentang "hewan" secara umum. Oleh karena itu, konsep abstract class perlu diterapkan agar kelas `Animal` tidak dapat diinstansiasi menjadi objek secara langsung, tetapi masih dapat mewarisi sifat-sifatnya kepada kelas anaknya (child class).

Untuk membuat sebuah kelas menjadi abstract, kita hanya perlu menambahkan kata kunci `abstract` sebelum menuliskan nama kelas:

```
abstract class Animal(var name: String, var weight: Double, var age: Int, var isCarnivore: Boolean){
 
    fun eat(){
        println("$name sedang makan !")
    }
 
    fun sleep(){
        println("$name sedang tidur !")
    }
}
```

Dengan begitu kelas `Animal` tidak dapat kita inisialisasikan menjadi sebuah objek.

```
fun main(){
    val animal = Animal("dicoding animal", 2.6, 1, true)
}
```

Ketika kita mencoba membuat objek dari kelas Animal, akan terdapat eror berikut:

**Cannot create an instance of an abstract class**


## Interfaces
>> [UP](#daftar-isi)

Interfaces adalah konsep yang digunakan oleh suatu kelas untuk memperoleh sifat-sifat umum. Interfaces mirip dengan abstract class, tetapi tidak memiliki properti deklarasi dan fungsi yang dideklarasikan tanpa implementasi. Tujuan dari interface adalah untuk diimplementasikan oleh sebuah kelas. Kelas yang mengimplementasikan sebuah interface diharuskan untuk melakukan override terhadap seluruh properti dan fungsi yang ada di interface, serta memberikan implementasi untuk setiap fungsi yang didefinisikan dalam interface tersebut.

Proses pembuatan sebuah interface mirip dengan pembuatan kelas. Umumnya, penamaan interface diawali dengan huruf **I** yang kapital. Meskipun hal ini tidak menjadi keharusan dalam sintaksis, namun ini adalah praktik terbaik dalam penamaan interface. Tujuannya adalah agar lebih mudah membedakan interface dengan kelas-kelas lainnya. Berikut ini adalah contoh pembuatan sebuah interface:

```
interface IFly {
    fun fly()
}
```

Proses implementasi sebuah interface pada kelas dilakukan dengan cara yang sama seperti melakukan pewarisan (extends) terhadap sebuah kelas super atau induk. Untuk memberikan pemahaman yang lebih jelas, mari kita buat sebuah kelas burung yang mengimplementasikan interface `IFly`:

```
class Bird : IFly {
 
}
```

Setelah menyelesaikan penulisan kode tersebut, kita akan mendapati sebuah error. Pesan error tersebut menyatakan **`"class Bird is not abstract and does not implement abstract member"`**. Artinya, kita harus mengimplementasikan sebuah anggota abstrak (abstract member), yang dalam kasus ini adalah sebuah fungsi abstrak yang terdapat dalam `IFly`. Untuk mengatasi error tersebut, kita perlu melakukan override terhadap fungsi yang ada di `IFly`.

```
class Bird : IFly {
    override fun fly() {
        println("I flying without wings")
    }
}
```

Untuk menambahkan sebuah properti pada interface, kita cukup menuliskannya seperti pada kelas namun tanpa melakukan inisialisasi nilai:

```
interface IFly {
    fun fly()
    val numberOfWings: Int
}
```

Sama seperti fungsi, kita juga diharuskan melakukan override properti. Overriding properti bisa dilakukan pada sebuah konstruktor kelas seperti berikut:

```
class Bird(override val numberOfWings: Int) : IFly {
 
    override fun fly() {
        if(numberOfWings > 0) println("Flying with $numberOfWings wings")
        else println("I'm Flying without wings")
    }
}
```

### Anonymous Clas

Seperti yang dapat disimpulkan dari namanya, "anonymous" mengacu pada kelas yang tidak memiliki nama. Alih-alih mendefinisikan sebuah kelas dengan menggunakan kata kunci `"class"`, Anda dapat langsung mendefinisikan isi dari kelas tersebut dengan menggunakan kata kunci `"object"`.

Supaya lebih paham, perhatikan contoh kode di bawah ini.

```
interface IFly {
    fun fly()
    val numberOfWings: Int
}
 
class Bird(override val numberOfWings: Int) : IFly {
    override fun fly() {
        if(numberOfWings > 0) println("Flying with $numberOfWings wings")
        else println("I'm Flying without wings")
    }
}
 
fun flyWithWings(bird: IFly) {
    bird.fly()
}
fun main() {
    flyWithWings(Bird(2))
}
```

Nah, sekarang kita coba ubah kode tersebut dengan menggunakan anonymous class.

```
interface IFly {
    fun fly()
    val numberOfWings: Int
}
 
fun flyWithWings(bird: IFly) {
    bird.fly()
}
 
fun main() {
    flyWithWings(object : IFly {
        override fun fly() {
            if(numberOfWings > 0) println("Flying with $numberOfWings wings")
            else println("I'm Flying without wings")
        }
        override val numberOfWings: Int
            get() = 2
    })
}
```

Perhatikan bahwa kita tidak membuat kelas Bird lagi, melainkan langsung mendefinisikan isi dari kelas tersebut menggunakan kata kunci `"object"`. Jika diperhatikan, memang tidak ada nama yang diberikan untuk objek yang dibuat ini, dan itulah yang disebut sebagai Anonymous Class.

Anda akan sering menemui konsep ini saat memasuki dunia pemrograman Android, di mana Anda perlu menjalankan perintah tertentu saat terjadi suatu aksi, misalnya ketika tombol ditekan. Proses semacam ini juga sering disebut sebagai listener atau callback.

```
myButton.setOnClickListener(object : OnClickListener{
    override fun onClick(p0: View?) {
        //melakukan perintah tertentu
    }
})
```


## Import dan Packages
>> [UP](#daftar-isi)

Semua elemen dalam Kotlin, seperti kelas dan fungsi, dikelompokkan dalam sebuah **package**. Package digunakan untuk mengelompokkan kelas, fungsi, dan variabel yang memiliki fungsionalitas yang serupa. Untuk menggunakan kelas, fungsi, atau variabel yang berada dalam suatu package, kita perlu menuliskan alamat package secara lengkap. Sebagai contoh, jika kita ingin menggunakan kelas `Random`, kita harus menuliskannya sebagai berikut:

```
val someInt = kotlin.random.Random(0).nextInt(1, 10)
```

Dalam contoh tersebut, terlihat bahwa kelas `Random` berada dalam package **kotlin.random**. Namun, apakah kita perlu menuliskan alamat package yang panjang seperti itu setiap kali kita ingin menggunakan sebuah kelas? Tentu tidak. Untuk mengurangi panjang kode tersebut, kita dapat mengimpor (import) package dari kelas `Random`. Dengan cara ini, kita tidak perlu menuliskan alamat package yang panjang berulang-ulang.

### Importing Package

Untuk mengimpor sebuah package yang berisi kelas, fungsi, atau variabel, kita hanya perlu menggunakan kata kunci `"import"` dan kemudian menuliskan alamat spesifiknya seperti:

```
import packagename.ClassName
import packagename.functionName
import packagename.propertyName
```

Karena kelas Random berada pada package kotlin.random, maka penulisannya menjadi seperti ini:

```
import kotlin.random.Random
```

Setelah kita mengimpor kelas `Random` dengan alamat package-nya, kita dapat langsung menggunakan kelas `Random` tanpa perlu menuliskan seluruh alamat package-nya. Ini tentu akan menghemat waktu dalam penulisan kode.

```
import kotlin.random.Random
 
val someInt = Random(0).nextInt(1, 10)
```

Pada umumnya, sebuah package akan berisi banyak kelas, fungsi, dan variabel. Sebagai contoh, kita akan menggunakan beberapa fungsi dan variabel matematika yang terdapat dalam package **kotlin.math**, sebagai berikut:

```
import kotlin.math.PI
import kotlin.math.cos
import kotlin.math.sqrt
 
fun main(){
    println(PI)
    println(cos(120.0))
    println(sqrt(9.0))
}
 
/*
Output:
    3.141592653589793
    0.8141809705265618
    3.0
*/
```

Kita juga dapat mengganti nama sebuah kelas, fungsi atau variabel yang kita import dengan menggunakan alias yang direpresentasikan dengan kata kunci `as`.

```
import kotlin.math.cos as cosinus
import kotlin.math.sqrt as akar
 
fun main(){
    println(PI)
    println(cosinus(120.0))
    println(akar(9.0))
}
 
/*
Output:
    3.141592653589793
    0.8141809705265618
    3.0
*/
```

Penggunaan kata kunci `"as"` biasanya digunakan ketika kita menggunakan kelas, fungsi, atau variabel yang memiliki nama yang sama tetapi berada dalam package yang berbeda. Tujuannya adalah untuk menghindari ambiguitas.

Seperti yang kita ketahui sebelumnya, pada package **kotlin.math** terdapat banyak fungsi dan variabel yang dapat kita gunakan. Kita bisa melihat pada completion suggestion berikut:

![Class](https://d17ivq9b7rppb3.cloudfront.net/original/academy/20190430105930df0777754ce4a43b248a8741114970a1.png)

Kita dapat mengimpor seluruh kelas, fungsi dan variabel yang berada pada suatu package dengan menggunakan tanda  `*` pada akhir package tersebut.

```
import kotlin.math.*
 
fun main(){
    println(PI)
    println(cos(120.0))
    println(sqrt(9.0))
}
 
 
/*
Output:
    3.141592653589793
    0.8141809705265618
    3.0
*/
```


## Membuat Package Baru
>> [UP](#daftar-isi)

Seperti yang telah dijelaskan sebelumnya, package adalah suatu wadah yang mengelompokkan kelas (kelas pada tingkat package), fungsi (fungsi pada tingkat package), atau variabel (variabel pada tingkat package) yang memiliki fungsi yang serupa. Kami juga telah mempelajari cara mengimpor kelas, fungsi, atau variabel yang terdapat dalam suatu package. Namun, kami belum mengetahui proses pembuatan package itu sendiri. Oleh karena itu, dalam pembahasan kali ini, kami akan menjelaskan bagaimana membuat sebuah package dalam bahasa Kotlin.

Idealnya sebuah package pada Kotlin dituliskan dengan awalan nama domain perusahaan yang dibalik. Contoh, **com.amoled**. Kemudian diikuti dengan nama package yang akan digunakan.

Untuk membuat sebuah package kita perlu membuat folder package pada berkas proyek. Perhatikan **Project Tool Window** yang terdapat pada IntelliJ Idea. Klik kanan pada folder **src** kemudian arahkan pada menu **New > package**.

![Membuat Package](https://d17ivq9b7rppb3.cloudfront.net/original/academy/2019043011134425ee315acb2e1317ad4eabcb273045d2.gif)

Setelah itu ketikkan nama package yang akan kita buat, misalnya **com.amoled.oop.utils**:

Perlu diingat, penamaan package selalu dituliskan dengan **flatcase**, tanpa garis bawah dan dipisahkan dengan titik.

Dengan menekan tombol **“OK”** maka kita berhasil membuat sebuah package folder pada proyek aplikasi kita. Maka struktur proyek akan menjadi seperti ini:

Kemudian, silakan membuat sebuah file di dalam package **utils**. Di sini, kita akan memberi nama file tersebut sebagai `MyMath.kt`. Buka file tersebut dan perhatikan baris kode yang dihasilkan oleh IntelliJ Idea. Seharusnya kita akan melihat baris kode berikut dalam file `MyMath.kt`.

```
package com.amoled.oop.utils
fun sayHello() = println("Hello From package com.amoled.oop.utils")
```

Kami telah membuat sebuah fungsi `sayHello()` pada tingkat package. Untuk mengakses fungsi tersebut, kita dapat secara eksplisit menuliskan alamat package. Silakan buat file Kotlin dengan nama `Main.kt` di dalam package **com.amoled.oop**, lalu akses fungsi `sayHello()` yang berada di dalam package **com.amoled.oop.utils**.

```
fun main(){
    com.amoled.oop.utils.sayHello()
}
 
/*
Output:
    Hello From package com.amoled.oop.utils
*/
```

Atau kita dapat menggunakan fungsi tersebut dengan mengimpor package-level function tersebut.

```
package com.amoled.oop
 
import com.amoled.oop.utils.sayHello
 
fun main() {
    sayHello()
}
 
/*
Output:
    Hello From package com.amoled.oop.utils
*/
```

Untuk mendalami pemahaman tentang package, mari kita tambahkan beberapa fungsi dan variabel ke dalam package tersebut. Buka kembali file `MyMath.kt` dan tambahkan beberapa fungsi dan variabel yang akan kita gunakan di masa depan.

```
package com.amoled.oop.utils
 
fun sayHello() = println("Hello From package utils")
 
const val PI = 3.1415926535  // package level variable
 
fun pow(number: Double, power: Double) : Double {
    var result = 1.0
    var counter = power
    while (counter > 0) {
        result *= number
        counter--
    }
    return result
}
 
fun factorial(number: Double) : Double {
    var result = 1.0
    var counter = 1.0
    while (counter <= number) {
        result *= counter
        counter++
    }
 
    return result
}
 
fun areaOfCircle(radius: Double) : Double {
    return PI * 2 * radius
}
```

Panggil beberapa fungsi dan variabel yang sudah ditambahkan pada `MyMath.kt`.

```
package com.amoled.oop
 
import com.amoled.oop.utils.PI
import com.amoled.oop.utils.factorial
import com.amoled.oop.utils.pow
import com.amoled.oop.utils.sayHello
 
fun main() {
    sayHello()
    println(factorial(4.0))
    println(pow(3.0, 2.0))
    println(PI)
}
 
/*
output:
    Hello From package com.amoled.oop.utils
    24.0
    9.0
    3.1415926535
*/
```

Pada bagian awal kode, kita dapat melihat bahwa saat kita menggunakan sebuah fungsi atau variabel yang berada dalam suatu package, kita perlu mengimpor setiap fungsi atau variabel secara terpisah. Namun, jika kita ingin menggunakan seluruh fungsi atau variabel dalam package tersebut, kita dapat menggunakan tanda bintang `(*)` untuk mengimpor seluruh fungsi dan variabel dalam package tersebut. Perhatikan contoh kode berikut:

```agsl
package com.amoled.oop
 
import com.amoled.oop.utils.*
 
fun main() {
    sayHello()
    println(factorial(4.0))
    println(pow(3.0, 2.0))
    println(PI)
    println(areaOfCircle(13.0))
}
 
/*
output:
    Hello From package com.amoled.oop.utils
    24.0
    9.0
    3.1415926535
    81.681408991
*/
```

Dengan memanggil fungsi `areaOfCircle()`, kita menggunakan seluruh fungsi dan variabel yang terdapat di dalam package **com.amoled.oop.utils**. Oleh karena itu, kita dapat mengimpor package tersebut hanya dengan menggunakan tanda bintang `(*)`.


## Exception
>> [UP](#daftar-isi)

Kode yang baik adalah kode yang mampu mengatasi segala jenis kejadian yang dapat memiliki efek buruk pada aplikasi kita. Kejadian-kejadian tersebut dalam pemrograman dikenal sebagai **exception**. Salah satu konsekuensi terburuk yang dapat diakibatkan oleh exception adalah terhentinya aplikasi saat sedang berjalan. Kami seharusnya menghindari situasi seperti ini. Oleh karena itu, di sub-modul berikutnya, kita akan mempelajari cara menangani exception (Exception Handling) agar dapat mengatasi masalah tersebut.

### Apa itu Exception?

**Exception** adalah suatu kejadian yang dapat mengganggu jalannya suatu program. Dalam Kotlin, semua exception termasuk dalam kategori **Unchecked**, yang berarti exception terjadi karena kesalahan dalam kode yang kita tulis. Berikut ini beberapa contoh **Unchecked Exception** yang sering mengganggu jalannya program kita:

+ **ArithmeticException**

+ **NumberFormatException**

+ **NullPointerException**

**ArithmeticException** adalah sebuah exception yang terjadi ketika kita melakukan pembagian dengan nol. Berikut ini adalah contoh kode yang dapat menghasilkan **ArithmeticException**.

```
fun main() {
    val someValue = 6
    println(someValue / 0)
}
 
/*
output:
    Exception in thread "main" java.lang.ArithmeticException: / by zero
*/
```

**NumberFormatException** terjadi ketika terdapat kesalahan dalam format angka. Misalnya, ketika kita mencoba mengonversi sebuah nilai String menjadi Integer, tetapi nilai String tersebut tidak memiliki format angka yang benar. Hal ini akan menghasilkan **NumberFormatException**. Berikut ini adalah contoh kode untuk situasi tersebut:

```
fun main() {
    val someStringValue = "18.0"
    println(someStringValue.toInt())
}
 
/*
output:
    Exception in thread "main" java.lang.NumberFormatException: For input string: "18.0"
*/
```

Terakhir, ada **NullPointerException** atau **NPE**. Meskipun Kotlin memiliki fitur **Null Safety**, tetap saja **NPE** dapat terjadi. **NPE** terjadi ketika suatu variabel atau objek memiliki nilai **null**, padahal seharusnya objek atau variabel tersebut tidak boleh **null**. Berikut ini adalah contoh kasus yang dapat menyebabkan **NullPointerException**:

```
fun main() {
    val someNullValue: String? = null
    val someMustNotNullValue: String = someNullValue!!
    println(someMustNotNullValue)
}
 
/*
output:
    Exception in thread "main" kotlin.NullPointerException at MainKt.main(Main.kt:3)
*/
```


## Exception Handling
>> [UP](#daftar-isi)

Ada beberapa cara untuk mengimplementasikan **exception handling**. Salah satunya adalah menggunakan **try-catch**, **try-catch-finally**, dan **multiple catch**. Mari kita eksplorasi ketiga cara tersebut.

### try-catch

Salah satu metode untuk mengatasi exception adalah dengan menggunakan **try-catch**. Kode yang mungkin memunculkan exception ditempatkan dalam blok **try**, dan jika exception terjadi, maka blok **catch** akan dieksekusi. Berikut adalah cara penulisan **try-catch** dalam Kotlin:

```agsl
try {
    // Block try, menyimpan kode yang membangkitkan exception
} catch (e: SomeException) {
    // Block catch akan terpanggil ketika exception bangkit.
}
```

Dengan meletakkan kode dalam blok **try**, kita dapat melindungi kode kita dari exception. Jika exception terjadi, program tidak akan berhenti atau crash, melainkan akan melompat ke blok catch. Di blok **catch**, kita dapat menuliskan kode alternatif untuk menampilkan pesan error atau melakukan tindakan lain yang diperlukan.

```
fun main() {
    val someNullValue: String? = null
    lateinit var someMustNotNullValue: String
 
    try {
        someMustNotNullValue = someNullValue!!
        println(someMustNotNullValue)
    } catch (e: Exception) {
        someMustNotNullValue = "Nilai String Null"
        println(someMustNotNullValue)
    }
}
 
/*
output:
    Nilai String Null
*/
```

### try-catch-finally

Blok **finally** bersifat opsional. Blok **finally** akan selalu dieksekusi setelah program keluar dari blok **try** atau **catch**. Bahkan blok **finally** akan tetap dieksekusi saat terjadi exception yang tidak terduga. Exception yang tidak terduga dapat terjadi misalnya ketika kita menggunakan **NullPointerException** pada blok **catch**, tetapi exception yang terjadi sebenarnya adalah **NumberFormatException**.

coba kita ubah kode yang sebelumnya dengan menerapkan **finally**:

```
fun main() {
    val someNullValue: String? = null
    lateinit var someMustNotNullValue: String
 
    try {
        someMustNotNullValue = someNullValue!!
    } catch (e: Exception) {
        someMustNotNullValue = "Nilai String Null"
    } finally {
        println(someMustNotNullValue)
    }
}
 
/*
output:
    Nilai String Null
*/
```

Dengan menerapkan **finally**, fungsi `println()` cukup dituliskan pada blok **finally**.

### Multiple Catch

Dari contoh kode yang telah kita coba sebelumnya, kita telah menggunakan exception untuk menangani semua jenis exception yang terjadi, baik itu **NullPointerException** maupun **NumberFormatException**. Namun, sebenarnya pada blok catch kita dapat secara spesifik memilih jenis exception yang ingin ditangani. _Multiple catch_ memungkinkan penanganan exception lebih dari satu jenis exception. Hal ini sangat berguna ketika kita ingin menangani setiap jenis exception dengan penanganan yang berbeda. Berikut adalah contoh struktur kode yang menerapkan multiple catch:

```
try{
    // Block try, menyimpan kode yang membangkitkan exception
} catch (e: NullPointerException) {
    // Block catch akan terpanggil ketika terjadi NullPointerException.
} catch (e: NumberFormatException) {
    // Block catch akan terpanggil ketika terjadi NumberFormatException.
} catch (e: Exception) {
    // Block catch akan terpanggil ketika terjadi Exception selain keduanya.
}
finally {
    // Block finally akan terpanggil setelah keluar dari block try atau catch
}
```

Dari struktur kode di atas, kita dapat melihat terdapat 3 (tiga) blok **catch**. Block **catch** yang pertama menggunakan parameter **NullPointerException**, sehingga jika terjadi **NullPointerException** maka blok **catch** tersebut akan dieksekusi. Yang kedua block **catch** dengan parameter **NumberFormatException**, sehingga jika terjadi **NumberFormatException** maka blok tersebut yang akan dieksekusi. Dan yang terakhir blok **catch** dengan parameter **Exception**, blok ini akan menangani seluruh exception yang terjadi kecuali untuk dua exception yang telah ditentukan pada blok sebelumnya. 

berikut contoh kode yang sebelumnya kita buat dengan menggunakan multiple catch.

```
import kotlin.NumberFormatException
 
fun main() {
    val someStringValue: String? = null
    var someIntValue: Int = 0
 
    try {
        someIntValue = someStringValue!!.toInt()
    } catch (e: NullPointerException) {
        someIntValue = 0
    } catch (e: NumberFormatException) {
        someIntValue = -1
    } finally {
        when(someIntValue){
            0 -> println("Catch block NullPointerException terpanggil !")
            -1 -> println("Catch block NumberFormatException terpanggil !")
            else -> println(someIntValue)
        }
    }
}
 
/*
output:
    Catch block NullPointerException terpanggil!
*/
```

Output dari kode di atas menjelaskan bahwa blok **catch** dengan parameter **NullPointerException** akan terpanggil. Hal ini disebabkan oleh penugasan nilai **null** ke variabel `someStringValue`.

Namun, jika kita menginisialisasi nilai `someStringValue` dengan **"12.0"**, maka exception yang terjadi akan berupa **NumberFormatException**. Dalam hal ini, blok **catch** kedua akan terpanggil dan menghasilkan output berikut: **"Catch block NumberFormatException terpanggil!"**

Namun, jika kedua exception tersebut tidak terjadi, artinya nilai `someStringValue` berhasil diubah menjadi Integer, maka output yang dihasilkan adalah nilai Integer tersebut. Sebagai contoh, jika nilai `someStringValue` diinisialisasi dengan "12.", berikut adalah hasilnya: **12**.
















