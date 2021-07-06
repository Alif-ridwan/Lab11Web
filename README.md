# Lab11Web

Nama    : M. Alif Ridwan Hanafi

NIM     : 311910801

Kelas   : Ti. 19. B1

Sebelum memulai menggunakan Framework Codeigniter, perlu dilakukan konfigurasi pada webserver. Beberapa ekstensi PHP perlu diaktifkan untuk kebutuhan pengembangan Codeigniter 4. Dengan cara di bawah ini :

![image](https://user-images.githubusercontent.com/81422149/122703721-678cf200-d27c-11eb-9749-d1b62fdd4057.png)

Hapus tanda ; (titik koma) pada bagian extension yang akan diaktifkan.

<img width="960" alt="1" src="https://user-images.githubusercontent.com/81422149/122704023-fac62780-d27c-11eb-8584-d299b4a8aa34.png">

# Instalasi Condelgniter

- Codeigniter dapat didownload dari website https://codeigniter.com/download
- Extrak file zip Codeigniter ke direktori htdocs/Lab11_ci
- Ubah nama direktory framework-4.x.xx menjadi ci4
- Buka browser dengan alamat http://localhost/Lab11_ci/ci4/public/

![image](https://user-images.githubusercontent.com/81422149/122707447-403a2300-d284-11eb-939b-e8dc7f272c5b.png)

Codeigniter menyediakan CLI, untuk mengaksesnya buka terminal lalu arahkan ke direktori project yang akan dibuat. Kemudian jalankan perintah php spark untuk memanggil CLI codeigniter.

<img width="960" alt="3" src="https://user-images.githubusercontent.com/81422149/122705033-1af6e600-d27f-11eb-9e05-9833a29de538.png">

Codeigniter juga menyediakan mode debugging/development yang dapat menampilkan error/kesalahan dalam kode program. Cara mengaktifkannya dengan mengubah nama file env menjadi .env kemudian buka filenya dan ubah nilai CI_ENVIRONMENT menjadi development.

<img width="454" alt="4" src="https://user-images.githubusercontent.com/81422149/122705343-b5efc000-d27f-11eb-81c9-e4f6f404fb30.png">
![5](https://user-images.githubusercontent.com/81422149/122706127-67dbbc00-d281-11eb-990c-5bce6951f8d4.jpg)


# Langkah 1 - Membuat Route

Router terletak pada file app/config/Routes.php
Untuk mengetahui route yg ada atau telah berjalan dapat menggunakan perintah php spark routes

![image](https://user-images.githubusercontent.com/81422149/122706860-fdc41680-d282-11eb-840c-3dc844424b50.png)

Selanjutnya mencoba akses route yang telah dibuat dengan mengakses http://localhost/8080
Terjadi error file not found dikarenakan tidak ada file/page untuk halaman ini.

![image](https://user-images.githubusercontent.com/81422149/122707676-af177c00-d284-11eb-89d0-bc5e7580f016.png)


# Langkah 2 - Membuat Controller

Membuat file page.php di dalam direktori Controller (/app/Controllers)

![image](https://user-images.githubusercontent.com/81422149/122708041-6b714200-d285-11eb-97ae-011f2b2dd400.png)

Kemudian refresh browser maka halaman sudah dapat diakses dan menampilkan hasilnya.

![6](https://user-images.githubusercontent.com/81422149/122708243-e89cb700-d285-11eb-9880-114e55581b35.jpg)

- Menambahkan method baru pada controller page.
- Method ini dapat diakses dengan menggunakan alamat: http://localhost:8080/page/tos

<img width="681" alt="7" src="https://user-images.githubusercontent.com/81422149/122708443-6660c280-d286-11eb-9e94-081b6cbf4ba1.png">


# Langkah 3 - Membuat View

Membuat file about.php di dalam direktori View (/app/view/about.php)

<img width="605" alt="9" src="https://user-images.githubusercontent.com/81422149/122708897-6a411480-d287-11eb-9e41-fae6b2a0bd27.png">
![10](https://user-images.githubusercontent.com/81422149/122708948-804ed500-d287-11eb-8962-c42dc0d5a358.jpg)

# Langkah 4 - Membuat Layout Web dengan CSS

- Buat file css pada direktori public dengan nama style.css (copy file dari praktikum lab4_layout).
- Kemudian buat folder template pada direktori view, lalu buat file header.php dan footer.php.

header.php

![11](https://user-images.githubusercontent.com/81422149/122709094-c86df780-d287-11eb-8686-52a2f9b6ef0b.jpg)

footer.php

![12](https://user-images.githubusercontent.com/81422149/122709142-df144e80-d287-11eb-9d1c-5ed69edc4bad.jpg)

- Kemudian ubah file about.php (/app/view/about.php) seperti berikut.

<?= $this->include('template/header'); ?>
<h1><?= $title; ?></h1>
<hr>
<p><?= $content; ?></p>
<?= $this->include('template/footer'); ?>

refresh browser atau akses alamat http://localhost:8080/about

![13](https://user-images.githubusercontent.com/81422149/122709235-0e2ac000-d288-11eb-9b4e-85eab786edf4.jpg)

# Pertanyaan dan Tugas

Lengkapi kode program untuk menu lainnya yang ada pada Controller Page, sehingga semua link pada navigasi header dapat menampilkan tampilan dengan layout yang sama.

# Hasil tugas

Tampilan page about

![14](https://user-images.githubusercontent.com/81422149/122709315-429e7c00-d288-11eb-9005-44f37a381325.jpg)

Tampilan page artikel

![15](https://user-images.githubusercontent.com/81422149/122709374-5813a600-d288-11eb-8946-e9803cae2828.jpg)

Tampilan page kontak

![16](https://user-images.githubusercontent.com/81422149/122709431-7083c080-d288-11eb-8692-6920b4a9386a.jpg)

# Praktikum 12

Jalankan MySQL dan buat sebuah database sebagai berikut:

![17](https://user-images.githubusercontent.com/81422149/122709476-8a250800-d288-11eb-8418-1577d39a2589.jpg)

1 - Konfigurasi Database

Membuat konfigurasi hubungan ke database server dengan menggunakan file .env

![18](https://user-images.githubusercontent.com/81422149/122709550-b3de2f00-d288-11eb-823a-ddbee4813cbf.jpg)

2 - Membuat Model

Buat file baru pada direktori /app/Models dengan nama ArtikelModel.php dengan code di bawah ini

<?php
namespace App\Models;

use CodeIgniter\Model;

class ArtikelModel extends Model
{
    protected $table = 'artikel';
    protected $primaryKey = 'id';
    protected $useAutoIncrement = true;
    protected $allowedFields = ['judul', 'isi', 'status', 'slug', 'gambar'];
}

3 - Membuat Controller

Buat Controller baru dengan nama Artikel.php pada direktori /app/Controllers dengan code di bawah ini

<?php
namespace App\Controllers;

use App\Models\ArtikelModel;

class Artikel extends BaseController
{
    public function index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->findAll();
        return view('artikel/index', compact('artikel', 'title'));
    }
}

4 - Membuat View

Buat direktori baru dengan nama artikel pada direktori /app/Views, kemudian buat file baru dengan nama index.php dengan code di bawah ini

<?= $this->include('template/header'); ?>

<?php if($artikel): foreach($artikel as $row): ?>
<article class="entry">
    <h2><a href="<?= base_url('/artikel/' . $row['slug']);?>"><?=$row['judul']; ?></a></h2>
    <img src="<?= base_url('/gambar/' . $row['gambar']);?>" alt="<?=$row['judul']; ?>">
    <p><?= substr($row['isi'], 0, 200); ?></p>
</article>
<hr class="divider" />
<?php endforeach; else: ?>
<article class="entry">
    <h2>Belum ada data.</h2>
</article>
<?php endif; ?>

<?= $this->include('template/footer'); ?>

Lalu buka alamat http://localhost:8080/artikel untuk melihat hasilnya.

![19](https://user-images.githubusercontent.com/81422149/122709687-f1db5300-d288-11eb-8cd4-ab5c730186b7.jpg)

Tidak ada data yang ditampilkan karena database masih kosong. Tambahkan data pada database untuk ditampilkan datanya pada phpmyadmin

![20](https://user-images.githubusercontent.com/81422149/122709718-03bcf600-d289-11eb-81ff-bf9c64769237.jpg)

Maka akan muncul tampilan seperti ini ketika browser direfresh.

![21](https://user-images.githubusercontent.com/81422149/122709744-159e9900-d289-11eb-844a-7639c7a1d523.jpg)

5 - Membuat Tampilan Detail Artikel

Tampilan pada saat judul berita di klik maka akan diarahkan ke halaman yang berbeda. Tambahkan sebuah fungsi baru pada Controller Artikel /app/Controllers/Artikel.php dengan nama view(). dengan code dibawah ini

public function view($slug)
    {
        $model = new ArtikelModel();
        $artikel = $model->where([
            'slug' => $slug
        ])->first();

    // Menampilkan error apabila data tidak ada.
        if (!$artikel)
        {
            throw PageNotFoundException::forPageNotFound();
        }
        $title = $artikel['judul'];
        return view('artikel/detail', compact('artikel', 'title'));
    }

6 - Membuat View Detail

Buat file baru dalam folder artikel /app/Views/artikel/ dengan nama detail.php untuk menampilkan halaman detail dengan code dibawah ini

<?= $this->include('template/header'); ?>

<article class="entry">
    <h2><?= $artikel['judul']; ?></h2>
    <img src="<?= base_url('/gambar/' . $artikel['gambar']);?>" alt="<?=
    $artikel['judul']; ?>">
    <p><?= $artikel['isi']; ?></p>
</article>

<?= $this->include('template/footer'); ?>

7 - Membuat Route

Buka file Routes.php dalam folder /app/Config/ dan tambahkan routing untuk ke halaman detail artikel

$routes->get('/artikel/(:any)', 'Artikel::view/$1');

Maka akan tampil halaman dari artikel yang diklik

![22](https://user-images.githubusercontent.com/81422149/122709850-50083600-d289-11eb-96fe-84b65bb0ddf1.jpg)

8 - Membuat Menu Admin

Menu admin adalah untuk proses CRUD data artikel. Buat method atau fungsi baru pada Controller Artikel dengan nama admin_index() dengan code di bawah ini

public function admin_index()
    {
        $title = 'Daftar Artikel';
        $model = new ArtikelModel();
        $artikel = $model->findAll();
        return view('artikel/admin_index', compact('artikel', 'title'));
    }

Kemudian buat file admin_index.php dalam folder /app/Views/artikel/ untuk tampilan halaman admin dengan code dibawah

<?= $this->include('template/admin_header'); ?>

<table class="table">
    <thead>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>Aksi</th>
        </tr>
    </thead>
    <tbody>
    <?php if($artikel): foreach($artikel as $row): ?>
    <tr>
        <td><?= $row['id']; ?></td>
        <td>
            <b><?= $row['judul']; ?></b>
            <p><small><?= substr($row['isi'], 0, 50); ?></small></p>
        </td>
        <td><?= $row['status']; ?></td>
        <td>
            <a class="btn" href="<?= base_url('/admin/artikel/edit/' .$row['id']);?>">Ubah</a>
            <a class="btn-danger" onclick="return confirm('Yakin menghapus data?');" href="<?= base_url('/admin/artikel/delete/' .
            $row['id']);?>">Hapus</a>
        </td>
    </tr>
    <?php endforeach; else: ?>
    <tr>
        <td colspan="4">Belum ada data.</td>
    </tr>
    <?php endif; ?>
    </tbody>
    <tfoot>
        <tr>
            <th>ID</th>
            <th>Judul</th>
            <th>Status</th>
            <th>Aksi</th>
        </tr>
    </tfoot>
</table>

<?= $this->include('template/admin_footer'); ?>

Kemudian tambahkan routing untuk menu admin sebagai berikut:

![23](https://user-images.githubusercontent.com/81422149/122709936-76c66c80-d289-11eb-8f48-9915df256aeb.jpg)

Menu admin dapat diakses dengan alamat http://localhost:8080/admin/artikel

![24](https://user-images.githubusercontent.com/81422149/122709977-8645b580-d289-11eb-8f88-7d98f8e4560c.jpg)

9 - Menambah Data Artikel

Tambahkan fungsi/method baru pada Controller Artikel dengan nama add() dengan code di bawah ini

 public function add()
    {
        // validasi data.
        $validation = \Config\Services::validation();
        $validation->setRules(['judul' => 'required']);
        $isDataValid = $validation->withRequest($this->request)->run();
    
        if ($isDataValid)
        {
            $artikel = new ArtikelModel();
            $artikel->insert([
                'judul' => $this->request->getPost('judul'),
                'isi' => $this->request->getPost('isi'),
                'slug' => url_title($this->request->getPost('judul')),
            ]);
            return redirect('admin/artikel');
        }
        $title = "Tambah Artikel";
        return view('artikel/form_add', compact('title'));
    }

Kemudian buat view untuk form tambah dengan nama form_add.php dalam folder (/app/Views/artikel/) dengan code di bawah ini

<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>
<form class="tambah" action="" method="post">
    <p>
        <input type="text" name="judul">
    </p>
    <p>
        <textarea name="isi" cols="50" rows="10"></textarea>
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>

<?= $this->include('template/admin_footer'); ?>

Dan di bawah ini adalah tampilannya

<img width="882" alt="25" src="https://user-images.githubusercontent.com/81422149/122710114-d6bd1300-d289-11eb-9ee3-47596010fbdd.png">

10 - Mengubah Data

Tambahkan fungsi/method baru pada Controller Artikel dengan nama edit() dengan code dibawah

public function edit($id)
    {
        $artikel = new ArtikelModel();
        // validasi data.
        $validation = \Config\Services::validation();
        $validation->setRules(['judul' => 'required']);
        $isDataValid = $validation->withRequest($this->request)->run();
        
        if ($isDataValid)
        {
            $artikel->update($id, [
                'judul' => $this->request->getPost('judul'),
                'isi' => $this->request->getPost('isi'),
            ]);
            return redirect('admin/artikel');
        }
        
        // ambil data lama
        $data = $artikel->where('id', $id)->first();
        $title = "Edit Artikel";
        return view('artikel/form_edit', compact('title', 'data'));
    }

Kemudian buat view untuk form tambah dengan nama form_edit.php dalam folder /app/Views/artikel/ dengan code di bawah ini

<?= $this->include('template/admin_header'); ?>

<h2><?= $title; ?></h2>
<form action="" method="post">
    <p>
        <input type="text" name="judul" value="<?= $data['judul'];?>" >
    </p>
    <p>
        <textarea name="isi" cols="50" rows="10"><?=$data['isi'];?></textarea>
    </p>
    <p><input type="submit" value="Kirim" class="btn btn-large"></p>
</form>

<?= $this->include('template/admin_footer'); ?>

Dan di bawah ini adalah tampilannya

![26](https://user-images.githubusercontent.com/81422149/122710194-010ed080-d28a-11eb-8169-88410234deba.jpg)

11 - Menghapus Data

Tambahkan fungsi/method baru pada Controller Artikel dengan nama delete() dengan code dibawah

public function delete($id)
    {
        $artikel = new ArtikelModel();
        $artikel->delete($id);
        return redirect('admin/artikel');
    }


# Pertanyaan dan Tugas

Selesaikan programnya sesuai Langkah-langkah yang ada. Anda boleh melakukan improvisasi.

# Jawab/Hasil

Admin_header.php

<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title><?= $title; ?></title>
    <link rel="stylesheet" href="<?= base_url('/adminstyle.css');?>">
</head>
<body>
    <div id="container">
    <header>
        <h1>Halaman Admin</h1>
    </header>
    <nav>
        <a href="<?= base_url('/admin/artikel');?>" class="active">Dashboard</a>
        <a href="<?= base_url('/artikel');?>">Artikel</a>
        <a href="<?= base_url('/admin/artikel/add');?>">Tambah Artikel</a>
    </nav>
    <section id="wrapper">

Admin_footer.php

    <footer>
        <p>&copy; 2021 - Universitas Pelita Bangsa</p>
    </footer>
    </div>
</body>
</html>

Hasil run

Menambahkan artikel baru

![27](https://user-images.githubusercontent.com/81422149/122710397-5ba82c80-d28a-11eb-945c-851877ae2cdd.jpg)
![28](https://user-images.githubusercontent.com/81422149/122710467-7f6b7280-d28a-11eb-8b98-d739fc94baf4.jpg)

Menghapus artikel

![29](https://user-images.githubusercontent.com/81422149/122710501-901be880-d28a-11eb-955d-c305433336ea.jpg)
![30](https://user-images.githubusercontent.com/81422149/122710523-9dd16e00-d28a-11eb-8364-4aabdbf16f3d.jpg)

Mengedit artikel

![31](https://user-images.githubusercontent.com/81422149/122710560-b3df2e80-d28a-11eb-8e29-5a59abb6c6fd.jpg)
![32](https://user-images.githubusercontent.com/81422149/122710545-aa55c680-d28a-11eb-8b6a-0edd60105266.jpg)


# Praktikum 13

1. Membuat Tabel User :

![image](https://user-images.githubusercontent.com/81422149/123727145-67fc3d00-d8bb-11eb-944a-5139c3ade688.png)

2. Membuat Model User :

![image](https://user-images.githubusercontent.com/81422149/123727183-76e2ef80-d8bb-11eb-9363-ba0549b51a1a.png)

3. Membuat Controller User :

![image](https://user-images.githubusercontent.com/81422149/123727219-83ffde80-d8bb-11eb-9867-35f25ccbb1f0.png)

4. Membuat View Login :

![image](https://user-images.githubusercontent.com/81422149/123727260-924dfa80-d8bb-11eb-90f9-4c17fb53b24c.png)

5. Membuat Database Seeder :

- jalankan pada CLI php spark make:seeder UserSeeder
- edit file Database/Seeds/UserSeeder.php :

![image](https://user-images.githubusercontent.com/81422149/123727318-a98ce800-d8bb-11eb-8081-a3e89590af07.png)

- lalu jalankan lagi CLI php spark db:seed UserSeeder

Hasil Output :

![image](https://user-images.githubusercontent.com/81422149/123727385-c0333f00-d8bb-11eb-8990-942b15293d14.png)

dan ketika isi email,password maka muncul pada halaman portal admin :

![image](https://user-images.githubusercontent.com/81422149/123727410-ca553d80-d8bb-11eb-972b-83b8ee979037.png)

6. Menambahkan Auth Filter :

![image](https://user-images.githubusercontent.com/81422149/123727456-dccf7700-d8bb-11eb-9c98-95686a62636a.png)

7. Konfigurasi file app/Config/Filters.php :

![image](https://user-images.githubusercontent.com/81422149/123727481-e822a280-d8bb-11eb-8ec1-a0117b9abbe2.png)

8. dan konfigurasi app/Config/Routes.php :

![image](https://user-images.githubusercontent.com/81422149/123727532-fc669f80-d8bb-11eb-98f1-7f2e97c5c072.png)

hasil outputnya :

![image](https://user-images.githubusercontent.com/81422149/123727557-04beda80-d8bc-11eb-8362-4b0741dd98ce.png)

9. Fungsi Logout :

![image](https://user-images.githubusercontent.com/81422149/123727587-10aa9c80-d8bc-11eb-8a3f-29cc4acc17e5.png)


# Tugas Praktikum 14

1. Membuat Pagenation :

<img width="819" alt="1" src="https://user-images.githubusercontent.com/81422149/124549773-d7dd6b00-de59-11eb-95dc-25482846c9df.png">

2. Membuat Pencarian :
    
<img width="788" alt="2" src="https://user-images.githubusercontent.com/81422149/124550034-428ea680-de5a-11eb-8be3-ded2811276ca.png">

3. Upload Gambar :
    
<img width="789" alt="3" src="https://user-images.githubusercontent.com/81422149/124550074-563a0d00-de5a-11eb-8fd3-0f3ea2bccf5c.png">
