# Arka

**Latihan yang dipandu pengasuh, dengan hasil sesi yang dapat ditelusuri.**

Arka adalah sistem latihan rehabilitasi motorik dan kognitif untuk panti jompo dan rumah sakit. Arka menghubungkan web app pengasuh, backend sesi yang otoritatif, dan perangkat ESP32 untuk menjalankan latihan fisik dengan aman serta menyimpan hasil yang berada dalam scope institusi.

Arka adalah alat bantu latihan dan pencatatan sesi. Arka bukan perangkat diagnosis, bukan alat penetapan terapi, dan bukan pengganti asesmen tenaga kesehatan.

## Mengapa Arka

Sesi latihan dengan perangkat fisik membutuhkan lebih dari sekadar tampilan permainan. Pengasuh perlu mengetahui bahwa perangkat siap, sesi dapat dihentikan dengan aman, input tidak dinilai oleh browser, dan hasil tersimpan tanpa mencampurkan identitas peserta ke firmware.

Arka menjaga satu alur yang jelas:

1. Institusi masuk dan memeriksa kesiapan perangkat.
2. Pengasuh memilih mode dan memasukkan identitas minimum peserta.
3. Backend mengikat perangkat ke preparation dan sesi secara eksklusif.
4. Peserta mengikuti instruksi melalui layar dan perangkat fisik.
5. Backend memfinalisasi hasil dan menyediakan riwayat privat peserta.

## Repositories

| Repository | Tanggung jawab |
| --- | --- |
| `Arka-FE` | React web app untuk landing page, autentikasi, onboarding, dashboard, dan alur sesi |
| `Arka-BE` | Express API untuk autentikasi, otorisasi, database, game runtime, device gateway, WebSocket, dan worker |

Firmware ESP32 serta dokumentasi produk dan arsitektur dikelola bersama source Arka. README dan konfigurasi aplikasi berada di masing-masing direktori implementasi.

## Technology Stack

| Layer | Teknologi |
| --- | --- |
| Web | React 19, Vite 8, TypeScript, Tailwind CSS 4 |
| API | Node.js, Express 5, TypeScript, Zod |
| Authentication | Better Auth dengan session cookie HTTP-only |
| Data | PostgreSQL, Prisma 7, Redis/Valkey |
| Realtime | WebSocket untuk browser dan device gateway |
| Device | ESP32 Arduino, PlatformIO, ArduinoJson |
| Local AI | Ollama privat untuk rangkuman nonklinis opsional |

## Prinsip Produk

- **Pengasuh tetap memegang kendali** — peserta selalu mengikuti sesi dengan pendamping.
- **Backend adalah sumber kebenaran** — browser tidak memulai timer, menilai input, atau memfinalisasi hasil.
- **Privasi minimum** — firmware tidak menerima nama, kode peserta, cookie, atau credential pengguna.
- **Fail-safe** — disconnect, fault, timeout, dan command stale tidak boleh membuat actuator tetap aktif atau menghasilkan skor palsu.
- **Bukan klaim klinis** — skor dan rangkuman hanya mendeskripsikan sesi permainan.

