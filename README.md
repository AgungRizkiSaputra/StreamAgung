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
