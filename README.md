# Praktikum 1 : Dart Stream

## Soal 1

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
