# Module 10: Asynchronous Programming Reflection

## Experiment 1.2: Understanding how it works

Setelah saya menambahkan println!("Azka Computer: hey hey"); tepat setelah spawner.spawn(...), output "hey hey" muncul lebih dulu karena baris itu masih dijalankan secara langsung oleh main. Sementara itu, blok async yang di-spawn belum langsung dieksekusi, melainkan hanya dimasukkan ke antrean executor. Karena executor baru mulai bekerja saat executor.run() dipanggil, pesan "howdy!" muncul sesudah "hey hey", lalu "done!" tampil terakhir setelah TimerFuture selesai menunggu sekitar dua detik.
