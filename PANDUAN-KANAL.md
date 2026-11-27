# Menghubungkan akun sosial

Isi kredensial di Coolify lalu redeploy. Di portal developer, daftarkan URL callback lengkap dengan menggabungkan PUBLIC_URL dan path di tabel. Misalnya https://sosial.example.com/integrations/social/threads. Buka dashboard Postiz, pilih Add Channel, pilih platform, lalu izinkan akses akun tujuan.

| Kanal | Variabel di Coolify | Path callback | Uji pertama |
|---|---|---|---|
| Telegram | TELEGRAM_TOKEN | Melalui bot | Jadikan bot admin channel uji. Kirim /connect beserta kode dari dashboard ke channel itu, lalu jadwalkan pesan teks. |
| Instagram langsung | INSTAGRAM_APP_ID, INSTAGRAM_APP_SECRET | /integrations/social/instagram-standalone | Pilih login Instagram langsung dan jadwalkan satu foto. |
| Instagram via Facebook | FACEBOOK_APP_ID, FACEBOOK_APP_SECRET | /integrations/social/instagram | Pilih akun profesional yang terhubung ke Page dan uji satu foto. |
| Facebook Page | FACEBOOK_APP_ID, FACEBOOK_APP_SECRET | /integrations/social/facebook | Pilih Page yang Anda kelola dan uji teks. |
| Threads | THREADS_APP_ID, THREADS_APP_SECRET | /integrations/social/threads | Hubungkan profil Threads dan uji teks. |
| Discord | DISCORD_CLIENT_ID, DISCORD_CLIENT_SECRET, DISCORD_BOT_TOKEN_ID | /integrations/social/discord | Izinkan bot pada server uji dan pilih channel yang mengizinkan bot mengirim pesan. |
| LinkedIn profil | LINKEDIN_CLIENT_ID, LINKEDIN_CLIENT_SECRET | /integrations/social/linkedin | Hubungkan profil dan uji posting teks. |
| TikTok | TIKTOK_CLIENT_ID, TIKTOK_CLIENT_SECRET | /integrations/social/tiktok | Hubungkan akun uji lalu unggah video pendek. |
| YouTube | YOUTUBE_CLIENT_ID, YOUTUBE_CLIENT_SECRET | /integrations/social/youtube | Aktifkan YouTube Data API v3 di project Google, lalu uji video dengan visibilitas privat. |
| X | X_API_KEY, X_API_SECRET | /integrations/social/x | Beri aplikasi akses tulis dan uji posting teks. |
| Pinterest | PINTEREST_CLIENT_ID, PINTEREST_CLIENT_SECRET | /integrations/social/pinterest | Pilih board uji dan unggah satu gambar. |

Jika login gagal dengan redirect mismatch, cocokkan URL lengkap termasuk HTTPS dan path. Jika login berhasil tetapi posting ditolak, periksa izin publikasi aplikasi dan status akses akun uji di portal platform. Untuk diagnosis jadwal, lihat log postiz dan temporal pada menit yang sama dengan waktu terbit.

Referensi implementasi versi paket: https://github.com/gitroomhq/postiz-app/tree/v2.26.0/libraries/nestjs-libraries/src/integrations/social
