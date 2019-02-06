# aplikasi pendataan siswa di SMA Negeri 1 Tanjungpandan
aplikasi ini buat untuk memenuhi tugas bear pada mata kuliah e-comerce lanjut. dan hasil dari project ini adalah aplikasi pendataan siswa di SMA negeri 1 Tanjungpandan
# installing laravel
disini saya menjelaskn cara menginstal laravel dengan cara Copy Fresh Laravel. cara ini bisa digunakan untuk mendapatkan fresh laravel dari composer orang lain. contohnya caranya adalah dengan mengcopy satu folder fresh instal laravel orang lain keperangkat kamu, dengan cara kamu harus mengaktifkan Apache dan MySQL pada xampp cotrol panel terlebih dahulu, dan kemudian mencopy project yang kamu copy ke folder htdocts yang berada didalam folder xampp (xampp/htdocts), kemudian akses laravel yang kamu copy di browser seperti contoh http://localhost/10515052_UAS_ECOM/public  
# cara integrasi Laravel menggunakan Template Admin LTE2.3.11
untuk mengintegrasikan laravel ini dilperlukan template AdminLTE 2.3.11 dengan cara mendownload pada link https://codeload.github.com/almasaeed2010/AdminLTE/zip/v2.3.11.
caranya yaitu : 
1. buat folder assets di dalam folder public laravel kamu (yang kamu copy paste di htdocts). copy folder dist, bootstrap, dan plogins dari template AdminLTE ke folder kamu (yang tadi di download).
2. buat folder baru dengan nama templates pada folder resources/view di laravel kamu.
3. didalam folder templates buat file dengan nama header.blade.php dan footer.blade.php.
4. buat folder baru dengan nama kelas pada folder resources/views di laravel kamu.
5. didalam folder kelas, bual file dengan nama index.blade.php
6. buka folder AdminLTE-2.3.11 kamu, kemudian cari file blaank.html di dalam folder pages/examples
7. kemudian buka editor (kalau saya menggunakan notepad++) kemudian copy line 1-391 dan paste pada file templates/header.blade.php yang tadi kamu buat. copy line 392-432 pada file index.blade.php, dan copy line 433-654 kemudian paste pada file templates/footer.blade.php 
8. didalam file templates/header.blade.php pada baris 21 tambahkan @stack('style') yang digunakan untuk menyimpan potongan script dari hasil @push pada baris 394 tambahkan @yield('content') yang digunakan untuk menyimpan potongan script dari hasil @section. pada baris 396 tambahkan @include yang digunakan untuk menyisipkan file lain.
9. didalam file kelas/index.blade.php tambahkan pada baris pertama @extends ('templates/header') yang digunakan untuk melakukan extends ke file yang dituju, @section('content') yang digunakan untuk membedakan block section yang nanti akan disimpan pada bagian @yield dan baris terakhir tambahkan @endsection
10. pada templates/header.blade.php lakukan find and replace menganti semua link asset ke folder yang sudah kita copy tadi. find what :../.. replace with {{asset(assets')}} lakukan hal yang sama pada tempaltes/footer.blade.php
11. buka commend prompt (dengan ara tekan shift+klik kanan di sembarang tempat, pilih open windows command windows here)di folder belajarlaravel, buat controller baru menggunakan artisan dengan syntax > php artisan make:controller KelasController. jika berhasil maka akan muncul fime KelasController.php do folder app/Http/Controllers
12. buka file app/Http/ControllersKelasController.php pada line 9 tambahkan syntax public funcion index(){return view('kela/index');}
13.buka file routes/web.php, ubah routes yang sudah ada menjadi Route =::get(/','KelasController@index');
14. akses browser kalian dengan alamat url sesuai dengan yang sudah kalian instal di awal maka template adminLTE 2.3.11 telah terintegrasi ke laravel anda.
# membuat crud 
dalam pembahasan ini akan dijelaskan bagaimana membaca data dari database dengggan menggunakan Laravel dan Eloquent . Eloquent adalah fitur dari Laravel yang memungkinkan dita memanggil data dari database dalam bentuk entity Object tanpa syntax My SQL. dalam embuatan database MySQL nya menggunakan fitur imigration dari Laravel. Migration ini membantu wb artisan dalam mendefinisikan table (DDL) dalam bentuk syntax PHP.Tutorial Make Simple CRUD (Create, Read, Updata, dan Delete) dapat di akses di link berikut : https://drive.google.com/file/d/1AmexPu9OEQEz1cHfvVOHHIx3-47ml-Jm/view?usp=sharing
# Eloquent Relationship
bagaimana membuat relasi dua tabel menggunakan Eloquent. dengan menggunakan Eloquent ini kalian tidak perlu lagi membuat syntax query Join join. caranya dengan :
1. membuat imigration table t_kelas
2. Buat menu pada sidebar, modifikasi sidebar pada file resources/views/siswa/header.blade.php
3. buat model siswa
4. Buat controller SiswaController, CRUD nya sama saja seperti pada pembahasan sebelumnya diatas tentang KelasController.
5. Edit route pada web.php
6. Buat file resources/views/siswa/index.blade.php
7. buat file resources/views/siswa/form.blade.php
untuk membuat relasi dua arah menggunakan Eloquent lebih jelasnya dapat diakses pada link https://drive.google.com/file/d/1WpHAgdv4zVrgA-nV1u64Mbl31C65LyVC/view?usp=sharing
# Login
Tampilan Login
1. Langkah pertama kita buat dulu tampilan login nya. Masih menyimpan file
AdminLTE kan? Buka AdminLTE-2.3.11/pages/examples/login.html.
2. Buat file baru di resources/views/login.blade.php
3. Copy isi dari login.html ke login.blade.php
4. Sama seperti file template pada pembahasan awal, Find & Replace
5. Modifikasi tambah feedback, form action, field name dan tambahkan token
(Line 36, 38, 39, 42, 46 dan 53)
6. Edit routes/web.php

Membuat Migration Table Login
Untuk melakukan login kita memerlukan tabel t_login. Gunakan artisan untuk
membuat migrationnya.
1. Buka command prompt, >php artisan make:migration create_table_user
2. Edit file migration nya
3. Lakukan migrate dengan membuka command prompt dan ketik >php artisan migrate
4. Table t_login akan tercipta otomatis. Lihat hasilnya di phpMyAdmin

Membut Model User
Untuk Login, model nya cukup berbeda. Laravel sudah menyediakan Model nya
dengan nama User pada folder app, tinggal kita modifikasi saja.

Membuat User Admin melalui Seeder

Nah, untuk membuat user adminnya, kita coba lewat database seeder ya. Langkah-
langkahnya adalah sebagai berikut:

1. Buka command prompt, ketik >php artisan make:seed LoginSeeder
2. Edit file Seeder tersebut
3. Jangan lupa edit juga database/seeds/DatabaseSeeder.php
4. Lakukan db seed pada command prompt > php artisan db:seed

Modifikasi LoginController
Modifikasi file app/Http/Controllers/Auth/LoginController.php
(Line 28, Line 40-48) Coba buka web browser kamu dan akses alamat http://localhost/belajarLaravel, maka
akan otomatis muncul halaman login.Masukkan username admin dan password admin, maka akan langsung ke halaman
utama.Jika username/password salah akan muncul feedback pesan error.

Membuat Tombol Logout
Setelah berhasil login, kita coba buat tombol logout nya. Ikuti langkah berikut:
1. Buka file resources/views/templates/header.blade.php
2. Edit line 173
3. Coba logout, jika berhasil kamu akan diarahkan lagi ke halaman login

untuk lebih lengkapnya silahkan akses link dibawah ini :
https://drive.google.com/file/d/1wLjs3QIaYI3o9mIikLBJOluA_7QTm6rQ/view?usp=sharing
