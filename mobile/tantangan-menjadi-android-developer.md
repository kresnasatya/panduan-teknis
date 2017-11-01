# Tantangan menjadi Android Developer

## Narasi
Sekitar 1 minggu lalu, saya bersama teman-teman saya mengadakan workshop membuat aplikasi Android menggunakan Android Studio. Studi kasus yang kami buat sederhana yakni membuat aplikasi [pemesanan tiket](https://github.com/wdharmana/CinemaTix). Bahasa pemrograman yang dipakai adalah Java dan target peserta adalah mahasiswa yang baru masuk bangku perkuliahan. Sebagian besar mereka belum terbiasa dengan bahasa pemrograman dan merupakan tantangan tersendiri untuk membuat **TODO** sesederhana mungkin agar mereka mengerti.

## Tantangan pertama (Workshop)
Saat workshop berlangsung muncul beberapa tantangan diantaranya:
1. Spesifikasi laptop peserta. Rata-rata yang saya temukan laptop peserta seperti laptop kantoran. Layaknya RAM mulai 2GB - 4GB dengan Hard disk drive bukan Solid state drive dan dengan OS Windows (OS bukan masalah terlalu besar di bagian ini (mungkin)). Bagi anda seorang developer mobile dengan spesifikasi laptop tersebut harus membuat anda **ekstra bersabar** ketika membuka IDE seperti Android Studio. Ditambah dengan mendownload library saat membuat project dan mengunduh sesuatu menggunakan **Gradle** yang kadang terasa *lie-fi* bagi saya. Ditambah pula menjalankan emulator murni dari Android yang disediakan oleh Android Studio dengan spesifikasi laptop di atas (Saat ini anda bisa mencoba Nox emulator sebagai emulator yang ringan untuk men-test aplikasi Android anda).
2. Peserta belum paham dengan bahasa pemrograman Java. Saya rasa ini perlu dimaklumi karena latar belakang peserta adalah mahasiswa yang baru masuk perkuliahan alias maba dengan lulusan SMA / SMK. Jika anda lulusan SMK anda beruntung karena anda sudah pernah berhadapan dengan bahasa pemrograman.
Jika anda ingin belajar bahasa pemrograman Java silahkan cari di Udacity [Intro Java Programming](https://classroom.udacity.com/courses/ud282) & [Object Oriented Java](https://classroom.udacity.com/courses/ud283). Ingat yang namanya belajar hal baru itu tidak gampang, jadi harap bersabar. :)
3. Sebagian peserta belum menginstall tools untuk membuat aplikasi Android (JDK, Android SDK, Android Studio dan emulator) dan belum mencoba mengetest apakah Android Studio berjalan dengan baik dengan mencoba membuat Hello World Application pertama kali. Jadi, waktu workshop semakin lama selesainya.

## Solusi
1. Silahkan ikut gerakan [Indonesia Android Kejar](https://events.withgoogle.com/indonesia-android-kejar/) yang terbagi menjadi 3 level (Beginner, Intermediate dan Advance). 
2. Bagi anda yang ingin menjadi seorang Android developer, mari sisihkan uang saku anda untuk mengganti spare part laptop anda (RAM diupgrade ke 8 GB dan ganti ke SSD 256 GB **bukan** 128 GB) atau mengganti ke laptop baru seperti Macbook Pro atau Macbook Air. *Jangan sisihkan uang saku anda hanya untuk membeli gadget yang aduhai tetapi laptop anda masih kantoran.*. Untuk processor laptop saya sarankan Intel mulai dari core i3 - core i7 yang mulai dari tahun 2014. Kenapa tahun 2014? Karena saya menggunakan laptop dengan core i3 generasi keempat, RAM 8 GB dan SSD 128 GB (silahkan upgrade SSD ke 256 GB karena *128 GB* itu tidak cukup demi kenyamanan anda)
3. Mari bergabung di komunitas atau media pembelajaran untuk berdiskusi tentang hal-hal teknis yang anda alami saat mendevelop program. Rekomendasi saya: [Code Android Indonesia](https://web.facebook.com/groups/codeandroidin), [Bali Android Developers](https://web.facebook.com/groups/331528353933101),
[CodePolitan](https://www.codepolitan.com/) 

## Tantangan kedua (developer)
Bagi anda seorang Android developer yang sudah berpengalaman pastinya ingin memberikan aplikasi kepada pengguna dengan kriteria seperti berikut:
1. UI yang sesuai dengan OS mobile pengguna
2. UX yang benar-benar UX
3. Menyesuaikan layar mulai dari phone sampai tablet.
4. Size aplikasi anda relatif kecil (5 - 10 MB) << poin krusial.

Untuk memenuhi hal tersebut anda harus:
1. Mempersiapkan senjata canggih anda (laptop yang sesuai / melampaui kriteria disertai dengan smartphone anda untuk testing yang sesungguhnya).
2. Mempelajari bahasa pemrograman. Android (Java / Kotlin), iOS (Objective C / Swift).
3. Dan hal-hal lain yang belum saya ketahui.

Biasanya pada poin kedua merupakan momok sebagian besar dari anda. Karena, saya amati banyak yang ingin semacam shortcut untuk mempelajari 1 bahasa seperti JavaScript untuk menciptakan aplikasi di iOS dan Android. Bisa saja anda menggunakan Ionic (WebView yang dibungkus dengan cordova) atau React Native yang disediakan facebook. Namun, apakah benar-benar mampu melampaui real UX dari yang menggunakan 1 bahasa untuk 1 platform (Java/Kotlin X Android) (Objective C/Swift)? Saya mendapatkan sebuah artikel menarik yakni [WORA, Write Once Run Away](https://android.jlelse.eu/why-we-are-not-cross-platform-developers-fd7ef70e976d) sebagai bahan pertimbangan bagi anda belum memutuskan menggunakan Ionic, React Native atau pure Native.

## Tantangan (End User)
1. User Budget > Smartphone > Storage. Kita tidak tahu seberapa besar penyimpanan internal di smartphone user dan bisa jadi mereka tidak bisa mendowload aplikasi kita karena internal storage mereka terbatas atau ukuran aplikasi yang kita buat besar. Meskipun bisa di root atau bisa diatur untuk diarahkan ke penyimpanan eksternal namun tidak semua Android OS dan vendor memberi perlakuan seperti itu.

## Solusi (End User)
1. Anda bisa mencoba Android Instant Apps, membuat kodingan anda rapi dengan MVP dan menggunakan Kotlin. Mengapa Kotlin? Karena saya lihat kodingan yang dituliskan dengan Kotlin lebih sedikit dibanding Java, sehingga menaikkan kemungkinan ukuran aplikasi anda semakin kecil.
2. Atau anda bisa menggunakan Progressive Web Apps. :)