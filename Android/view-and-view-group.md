> ## View dan View Group
>> [Back](https://github.com/StudyClubUnida/AMOLED/blob/main/Android/Modul%20Android.md)

<h1 align="center">
  <img src="https://github.com/Study-Club-Unida/AMOLED/blob/main/Android/Assets/view_viewgroup.jpeg" width="400"></img>
</h1>

- **_View_** adalah komponen dasar yang ditampilkan di layar dan dapat digunakan untuk berinteraksi dengan pengguna. Contoh komponen turunan View meliputi `TextView`, `Button`, `ImageView`, `RadioButton`, `Checkbox`, dan lainnya.
- **_ViewGroup_** adalah jenis View khusus yang berfungsi sebagai wadah bagi View lainnya dan mengatur tata letaknya.
- **_LinearLayout_** digunakan untuk menyusun komponen-komponen di dalamnya secara horizontal (berjajar) atau vertikal (bertumpuk).
- **_RelativeLayout_** digunakan untuk menempatkan komponen secara fleksibel berdasarkan posisi relatif terhadap komponen lain atau terhadap induknya. Contohnya, komponen A berada di sebelah kanan komponen B atau komponen A berada di tengah induknya.
- **_FrameLayout_** digunakan untuk menyusun komponen secara bertumpuk, di mana komponen yang lebih baru akan menutupi komponen yang lebih lama.
- **_TableLayout_** digunakan untuk mengatur komponen dalam bentuk baris dan kolom, mirip dengan tabel.
- **_ConstraintLayout_** adalah layout default dan direkomendasikan dalam XML. Layout ini memungkinkan Anda menyusun tampilan yang kompleks hanya dalam satu lapisan hierarki, menghasilkan performa dan rendering yang lebih baik dibandingkan dengan nested layout (layout di dalam layout). Fitur-fitur `ConstraintLayout` meliputi:

    - **_Relative Positioning:_** Memungkinkan penempatan komponen relatif terhadap komponen lain.
    - **_Center Positioning & Bias:_** Mengatur posisi tengah komponen menggunakan persentase, dengan nilai default 50%.
    - **_Baseline Alignment:_** Menyejajarkan teks pada komponen yang berbeda.
    - **Guideline:** Membuat garis bantu tak terlihat untuk membantu penempatan komponen.
    - **Barrier:** Mirip dengan Guideline, tetapi posisinya dapat mengikuti komponen lain.
    - **Chain:** Mengatur sekelompok komponen secara linear dengan beberapa gaya:
        - **Spread:** Komponen tersebar secara merata (default).
        - **Spread inside:** Komponen pertama dan terakhir menempel pada batas rantai, sisanya tersebar merata.
        - **Weighted:** Komponen dengan "match constraint" akan membagi ruang yang tersedia.
        - **Packed:** Komponen dikelompokkan bersama.

- **_ScrollView_** memungkinkan konten di dalamnya digulir secara vertikal atau horizontal. Penting diingat bahwa **_ScrollView_** hanya boleh berisi satu ViewGroup sebagai layout utamanya.
- Untuk menambahkan gambar ke drawable, cukup salin dan tempel gambar dari file explorer ke folder drawable. Pastikan memilih folder drawable (bukan drawable-v24) agar gambar kompatibel dengan semua versi Android.
- Nama file di dalam folder drawable harus menggunakan _huruf kecil_ dan _garis bawah_ (_) saja.
- Untuk mengganti ikon aplikasi, klik kanan pada folder **res**, pilih **New** → **Image Asset**. Pada _Icon Type_, pilih **Launcher Icons (Adaptive and Legacy)**, lalu pilih gambar yang diinginkan pada Path, dan klik **Next** → **Finish**. Ikon akan disimpan di folder mipmap dalam berbagai ukuran kepadatan (mdpi, hdpi, xhdpi, xxhdpi, dan xxxhdpi).
- **_Layout Inspector_** membantu menganalisis hierarki dan properti tampilan dalam aplikasi.
- Menggunakan "_Start_" dan "_End_" untuk margin lebih baik daripada "_Right_" dan "_Left_" karena mendukung tampilan bahasa yang berbeda, baik yang dibaca dari kiri ke kanan (LTR) seperti bahasa Inggris maupun yang dibaca dari kanan ke kiri (RTL) seperti bahasa Arab.


