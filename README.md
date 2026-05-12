# Module 10: Asynchronous Programming (Timer) Reflection

## Experiment 1.2: Understanding how it works

Setelah saya menambahkan println!("Azka Computer: hey hey"); tepat setelah spawner.spawn(...), output "hey hey" muncul lebih dulu karena baris itu masih dijalankan secara langsung oleh main. Sementara itu, blok async yang di-spawn belum langsung dieksekusi, melainkan hanya dimasukkan ke antrean executor. Karena executor baru mulai bekerja saat executor.run() dipanggil, pesan "howdy!" muncul sesudah "hey hey", lalu "done!" tampil terakhir setelah TimerFuture selesai menunggu sekitar dua detik.

## Experiment 1.3: Multiple Spawn and removing drop

Saat drop(spawner) saya hapus, semua task yang sudah di-spawn tetap berjalan dan seluruh output masih muncul, tetapi program tidak selesai sendiri dan tetap tertahan di executor.run(). Ini terjadi karena channel pengirim masih dianggap aktif, jadi executor terus menunggu kemungkinan task baru dan tidak pernah keluar dari loop recv(). Setelah drop(spawner) dipasang lagi, executor bisa tahu bahwa tidak ada lagi task yang akan dikirim sehingga program berhenti dengan normal.

