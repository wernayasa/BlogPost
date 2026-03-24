Menampilkan Keterangan Tanggal dan Waktu Update atau Pembaruan Artikel Postingan di Blogger dengan Metadata Bawaan Template Blogger tanpa JavaScript.  

[![custom lastupdated date blogger](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgAB_-rNUK5kCTd7tHftzJ5zIhEhyphenhyphenUjmUwdmq692MqNVrjhV92Z0GXVVOq7VS6lAFstWnu3OhpDvy0Fg4j7OfIrYZrfLfkmp5fu26oXZaW_uqkF9Z9Pj_TJJsV_OIAU0xYNgRl_JWGFqSk/w400-h301-rw/custom-date-lastupdated-blogger.png "custom lastupdated date blogger")](https://blogger.googleusercontent.com/img/b/R29vZ2xl/AVvXsEgAB_-rNUK5kCTd7tHftzJ5zIhEhyphenhyphenUjmUwdmq692MqNVrjhV92Z0GXVVOq7VS6lAFstWnu3OhpDvy0Fg4j7OfIrYZrfLfkmp5fu26oXZaW_uqkF9Z9Pj_TJJsV_OIAU0xYNgRl_JWGFqSk/)

Menampilkan keterangan waktu pembaruan atau update terakhir sebuah postingan di Blogger sendiri memiliki beberapa keuntungan; jika terdeteksi oleh mesin pencari, contoh Google, maka kesempatan artikel atau postingan tersebut menempati hasil pencarian teratas akan meningkat, karena Google sendiri memprioritaskan artikel yang diperbarui secara berkala. Sehingga tidak ada salahnya memberikan keterangan waktu pembaruan terakhir pada metadata postingan di antara Penulis dan waktu publikasi postingan tersebut.  
  
Cara lama menampilkan keterangan waktu pembaruan di metadata Blogger dengan template adalah melalui Javascript, yang mana keterangan waktu tersebut berformat ISO8601 (Pola : `YYYY-MM-DDThh:mm:ssTZD`) dan memanfaatkan Javascript untuk mengubahnya menjadi format waktu standard (Pola : `hh:mm - DD MMMM YYYY`). Nah, kabar baik bagi pengguna template Blogger baru dengan keterangan Layout Versi 2 dan Widget Versi 3, karena pada template tersebut sudah disediakan syntax untuk memanggil dan memodifikasi format keterangan waktu tersebut sesuai keinginan.  
  
Sebelum melangkah ke tahap pemasangannya, alangkah baiknya mengenal format penulisan waktu standard menurut ISO8601 yang Blogger pakai.  

### Penjelasan Singkat Tentang ISO8501

Mengutip dari Wikipedia \[1\], Standard ISO8601 adalah suatu standar internasional yang mengatur pertukaran data yang terkait dengan tanggal dan waktu. Sehingga risiko kesalahpahaman sewaktu dilakukan pertukaran data melintasi batas negara bisa dihilangkan serta untuk menghindari kebingungan dan galat atau kerugian lain yang mungkin ditimbulkan darinya.  
Di bawah ini dijelaskan mengenai isi dari setiap istilah pemformatan yang ada di ISO8601.

    YYYY-MM-DDThh:mm:ssTZD

*   `YYYY`: Menampilkan tahun
*   `MM`: Menampilan bulan
*   `DD`: Menampilkan hari
*   `hh`: Menampilkan jam (dalam format 24-jam)
*   `mm`: Menampilkan menit
*   `ss`: Menampilkan detik
*   `TZD`: Menampilkan keterangan selisih waktu dengan GMT

### Format Penanggalan dengan ISO8601 di Blogger

#### Tanggal Publikasi Pertama

Syntax dasar untuk menampilkan tanggal publikasi dengan format standard ini adalah sebagai berikut:

    <time expr:datetime="data:post.date.iso8601">
      <data:post.date/>
    </time>

Syntax di atas memiliki keluaran sebagai berikut:

    <time datetime="2020-05-30T20:48:00T+07:00">
      2020-05-30 20:48
    </time>

Nah, untuk memodifikasi keluaran tersebut menjadi pola seperti `30/05/2020` atau sesuai keinginan, maka format standard tersebut diubah menjadi seperti ini:

    <time expr:datetime="data:post.date.iso8601">
      <b:eval expr='format(data:post.date, "dd/MM/YYYY")'/>
    </time>

Syntax di atas memiliki keluaran sebagai berikut:

    <time datetime="2020-05-30T20:48:00T+07:00">
      30/05/2020
    </time>

#### Tanggal Pembaruan / Update Terakhir

Sedangkan syntax untuk menampilkan keterangan waktu pembaruan terakhir pada postingan Blogger dengan format standard atau default adalah sebagai berikut:

    <time expr:datetime="data:post.lastUpdated.iso8601">
      <data:post.lastUpdated/>
    </time>

Syntax di atas memiliki keluaran seperti di bawah ini:

    <time datetime="2020-05-31T20:48:00T+07:00">
      2020-05-31 20:48
    </time>

Untuk dapat melakukan perubahan format penulisan tanggal tersebut sesuai keinginan, bisa menggunakan contoh syntax seperti ini:

    <time expr:datetime="data:post.lastUpdated.iso8601">
      <b:eval expr='format(data:post.lastUpdated, "dd/MM/YYYY")'/>
    </time>

Syntax di atas memiliki keluaran sebagai berikut:

    <time datetime="2020-05-31T20:48:00T+07:00">
      31/05/2020
    </time>

Catatan, kedua keluaran di atas dapat berbeda tergantung pengaturan format penanggalan yang diterapkan dari dashboard Blogger.

#### Referensi Syntax pada Format Penanggalan

Nah, setelah memahami syntax, susunan syntax, dan keluarannya melalui contoh kode di atas, berikut dilampirkan referensi kode yang bisa digunakan untuk merubah keterangan waktu yang ada pada template Blogger tanpa harus menggunakan JavaScript. Referensi ini dikutip dari Repositori GitHub yang dikelola oleh Mas Hermawan Yogi \[2\].

Waktu

Simbol

Contoh Keluaran

Keterangan

Tahun

`YY`

`17`

Tahun, 2 digit

`YYYY`

`2017`

Tahun, 4 digit

Bulan

`M`

`1`, `11`

Bulan, minimum 1 digit

`MM`

`01`, `11`

Bulan, 2 digit

`MMM`

`Jan`, `Nov`

Bulan, 3 karakter

`MMMM`

`January`, `November`

Bulan, nama panjang

`MMMMM`

`J`, `N`

Bulan, karakter pertama

Pekan

`w`

`1`, `11`

Pekan dalam Tahun, minimum 1 digit

`ww`

`01`, `11`

Pekan dalam Tahun, 2 digit

`W`

`4`

Pekan dalam Bulan, 1 digit

Hari / Tanggal

`d`

`1`, `11`

Tanggal dalam Bulan, minimum 1 digit

`dd`

`01`, `11`

Tanggal dalam Bulan, 2 digit

`D`

`1`, `55`, `362`

Tanggal dalam Tahun, minimum 1 digit

`DD`

`01`, `55`, `362`

Tanggal dalam Tahun, minimum 2 digit

`DDD`

`001`, `055`, `362`

Tanggal dalam Tahun, minimum 3 digit

`F`

`3`

Hari ke-X dari Bulan. Contoh; Selasa ke-3 dari Bulan.

`E`

`M`, `T`

Nama hari dari Pekan. 1 karakter

`EE`

`Mo`, `Tu`

Nama hari dari Pekan. 2 karakter

`EEE`

`Mon`, `Tue`

Nama hari dari Pekan. 3 karakter

`EEEE`

`Monday`, `Tuesday`

Nama panjang hari dari Pekan.

Waktu dalam Hari

`aaaa`

`AM`, `PM`

Namanya mungkin berbeda tergantung regional.

`bbbb`

`Morning`, `Afternoon`, `Evening`

`BBBB`

Jam

`h`

`1`, `11`

Jam \[1-12\], minimum 1 digit

`hh`

`01`, `11`

Jam \[1-12\], 2 digit

`H`

`1`, `21`

Jam \[0-23\], minimum 1 digit

`HH`

`01`, `21`

Jam \[0-23\], 2 digit

Menit

`m`

`1`, `59`

Menit, minimum 1 digit

`mm`

`01`, `59`

Menit, 2 digit

  
  
Demikian artikel singkat tentang cara menampilkan keterangan tanggal dan waktu terkait kapan postingan blogger tersebut pertama kali dipublikasikan dan kapan terakhir kali postingan tersebut diperbarui, beserta referensi format penulisan tanggal dan waktu yang memungkinkan untuk ditampilkan. Semoga bermanfaat.  
  
Reference:  
\[1\] https://id.wikipedia.org/wiki/ISO\_8601  
\[2\] https://github.com/bloggerpack/blogger-snippets/blob/master/blog-posts-gadget-v2/date.md
