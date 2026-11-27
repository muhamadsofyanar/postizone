# Penjadwal media sosial dengan Postiz
Paket deployment Postiz v2.26.0 berdasarkan https://github.com/coollabsio/coolify/blob/main/templates/compose/postiz.yaml . Docker menarik image aplikasi saat deploy.

1. Ekstrak ZIP dan upload docker-compose.yaml dan README.md ke root repository GitHub.
2. Arahkan DNS A subdomain pilihan ke IP VPS. Pastikan proxy Coolify dapat menerima trafik HTTP/HTTPS.
3. Buat Application dari repository GitHub di Coolify, pilih Docker Compose dan lokasi /docker-compose.yaml.
4. Di Environment Variables (runtime), isi PUBLIC_URL dengan URL lengkap seperti https://sosial.example.com tanpa garis miring akhir. Isi JWTSECRET_SECRET, POSTGRESQL_SECRET, REDIS_SECRET dengan tiga nilai acak berbeda. Untuk setiap nilai jalankan openssl rand -hex 32 secara terpisah. Simpan nilainya untuk deployment berikutnya.
5. Pada pengaturan domain service postiz masukkan https://sosial.example.com:5000 dengan nama domain Anda. Port 5000 menunjuk port internal aplikasi. Akses aplikasi melalui URL biasa tanpa port.
6. Deploy, tunggu seluruh service healthy, buka URL lalu daftarkan akun pertama. Untuk pemakaian pribadi set DISABLE_REGISTRATION=true dan redeploy.
7. Tambahkan kanal melalui dashboard. Untuk provider OAuth, buat aplikasi developer, daftarkan callback domain sendiri sesuai panduan provider di https://docs.postiz.com dan isi pasangan ID/secret yang sesuai di Coolify (nama variabel tersedia di docker-compose.yaml). Redeploy setelah perubahan. Untuk Telegram buat bot lewat BotFather, beri hak posting pada channel uji, lalu ikuti dialog koneksi Telegram.
8. Pilih zona waktu Asia/Jakarta di kalender jika tersedia, jadwalkan satu post ke kanal uji beberapa menit ke depan, lalu verifikasi waktu dan isi di kanal tujuan.

Jika halaman tidak terbuka, periksa DNS, domain service dan log postiz. Jika jadwal macet periksa log temporal, postgres dan temporal-elasticsearch. File unggahan dan database memakai named volume. Pertahankan volume saat redeploy, cadangkan sebelum upgrade. Kredensial diisi hanya melalui Coolify.

Lihat PANDUAN-KANAL.md untuk variabel, callback dan pengujian tiap kanal. File coolify.env.example dapat disalin sebagai acuan pengisian variabel runtime. Simpan nilai asli di Coolify.
