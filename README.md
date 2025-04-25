# Praktikum 1 : Dart Stream

### P1: Jawaban Soal 1

    @override
      Widget build(BuildContext context) {
        return MaterialApp(
          title: 'Stream Agung',
          theme: ThemeData(primarySwatch: Colors.deepPurple),
          home: const StreamHomePage(),
        );
      }

### P1: Jawaban Soal 2

    class ColorStream {
        final List<Color> colors = [
            Colors.blueGrey,
            Colors.amber,
            Colors.deepPurple,
            Colors.lightBlue,
            Colors.teal,
            // =================
            Colors.black,
            Colors.red,
            Colors.yellow,
            Colors.cyan,
            Colors.green,
        ];
    }

### P1: Jawaban Soal 3

- Keyword yield\* ini dipakai buat "ngalirin" semua data dari stream lain ke stream yang lagi kita buat, jadi semacam nerusin isi dari stream lain tanpa harus ngatur satu-satu.

- Maksud dari perintanya itu bikin aliran data (stream) yang setiap detiknya ngeluarin satu warna dari daftar colors, terus warna itu dipilih berdasarkan index yang muter-muter terus pakai t % colors.length biar tidak keluar dari batas array. Jadi, tiap detik dia bakal kirim warna berikutnya dari list, terus balik lagi ke awal kalau udah sampai akhir.

### P1: Jawaban Soal 4

<img src="https://github.com/AgungRizkiSaputra/StreamAgung/blob/main/image/GIFP1soal4.gif"  width="150px" >

### P1: Jawaban Soal 5

listen itu langsung nanggepin data yang masuk, cocok buat update UI secara real-time. Sedangkan await for nunggu data satu-satu secara berurutan dalam fungsi async, lebih cocok buat proses data yang butuh ketertiban.

# Praktikum 2 : Stream Controllers dan Sink

### P2: Jawaban Soal 6

- Langkah 8 berfungsi untuk membuat dan mengatur stream agar bisa nerima data (angka) secara real-time. Saat ada angka baru masuk ke stream, setState akan memperbarui UI untuk menampilkan angka terbaru lewat lastNumber.

- Langkah 10 berfungsi membuat angka acak dari 0 sampai 9, lalu mengirimkannya ke stream melalui method addNumberToSink, sehingga angka itu bisa langsung ditangkap oleh listener di Langkah 8. Jadi, Langkah 8 menangani penerimaan data, dan Langkah 10 mengirimkan datanya.

<img src="https://github.com/AgungRizkiSaputra/StreamAgung/blob/main/image/GIFP2soal6.gif"  width="150px" >

### P2: Jawaban Soal 7

- Langkah 13, dibuat fungsi addError() yang tugasnya ngirim error ke stream. Ini seperti mengirim sinyal bahwa terjadi kesalahan di aliran data.

- Langkah 15, fungsinya memicu error secara sengaja ke dalam stream.

Jadi intinya, Langkah 13 membuat cara untuk mengirim error ke stream, dan Langkah 15 menjalankan error tersebut lewat pemanggilan fungsi tadi.

# Praktikum 3 : Injeksi Data ke Stream

### P3: Jawaban Soal 8

- Langkah 1, dibuat variabel transformer yang bertipe StreamTransformer. Ini digunakan untuk ngubah data yang datang dari stream. Kata kunci late dipakai karena variabel ini baru akan diisi nilainya nanti, tapi dipastikan sudah terisi sebelum dipakai.

- Langkah 2, variabel transformer diisi dengan menggunakan StreamTransformer<int, int>.fromHandlers. Ini artinya kita bisa menentukan bagaimana data, error, dan penutupan stream akan ditangani. Misalnya, setiap data yang masuk akan dikalikan 10 sebelum diteruskan. Kalau ada error, bukan error yang diteruskan, melainkan nilai -1 yang dikirimkan. Setelah stream selesai, bagian sink akan ditutup.

- Langkah 3, transformer yang sudah dibuat diterapkan pada stream. Setelah itu, data yang sudah dimodifikasi oleh transformer didengarkan dengan listen(). Kalau ada data yang masuk, data itu akan disimpan ke dalam variabel lastNumber melalui setState, yang nantinya akan memicu pembaruan tampilan. Kalau ada error, nilai lastNumber akan diubah jadi -1. Jadi, data dari stream bisa diubah dulu sebelum ditampilkan dalam aplikasi.

<img src="https://github.com/AgungRizkiSaputra/StreamAgung/blob/main/image/GIFP3soal8.gif"  width="150px" >

# Praktikum 4 : Subscribe ke Stream Events

### P4: Jawaban Soal 9

- langkah 2, kita buat stream untuk mengalirkan angka secara terus-menerus. Kita ambil controller-nya, terus dengarkan stream-nya. Setiap kali ada angka baru masuk, simpan angka itu ke variabel lastNumber pakai setState() biar UI-nya ikut berubah.

- langkah 6, kita berhenti mendengarkan stream-nya dengan cara memanggil subscription.cancel(). Ini dilakukan saat tidak butuh data lagi, misalnya widget di-dispose.

- langkah 8, kita buat angka acak dari 0 sampai 9. Kalau stream controller-nya masih aktif, angka itu dikirim ke stream. Tapi kalau udah ditutup (closed), lastNumber di-set jadi -1 buat nunjukin kalau udah tidak ada data lagi yang bisa dikirim.

<img src="https://github.com/AgungRizkiSaputra/StreamAgung/blob/main/image/GIFP4soal9.gif"  width="150px" >

# Praktikum 5 : Multiple Stream Subscription

### P5: Jawaban Soal 10

Error ini muncul karena stream udah didengarkan lebih dari satu kali, dan Stream di Dart hanya bisa didengarkan satu kali secara default, kecuali itu adalah BroadcastStream.

### P5: Jawaban Soal 11

Karena disini melakuka dua kali subscription (listen) ke stream yang sama, tanpa perbedaan perilaku di keduanya.

- stream.listen akan menambahkan listener baru ke stream.

- Dan disini menambahkan 2 listener (subscription dan subscription2) yang keduanya melakukan hal yang sama menambahkan angka ke values.

Hasilnya, setiap kali ada data baru yang masuk ke stream, kedua listener akan nerima data tersebut dan memprosesnya, menyebabkan output yang berulang dua kali.

<img src="https://github.com/AgungRizkiSaputra/StreamAgung/blob/main/image/GIFP5soal11.gif" width="150px"
