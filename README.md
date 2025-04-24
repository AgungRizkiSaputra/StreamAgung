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

<img src="https://github.com/AgungRizkiSaputra/StreamAgung/blob/main/image/GIFP1soal4.gif"  width="200px" height="100">
