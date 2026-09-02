# Store Bot

Bot Telegram dengan **Rich Message** (Bot API 10.1+), **Premium Emoji**, Create Panel Pterodactyl, Deploy Token, dan Cek Info.

Siap dijalankan di **Pterodactyl** Node.js 20–23.

---

## Fitur

### Create Panel Pterodactyl
| Command | Keterangan | Akses |
|---------|------------|--------|
| `/1gb` … `/20gb nama,id` | Buat user + server sesuai plan | Premium / Owner |
| `/unli nama,id` | Unlimited CPU / Disk / RAM | Owner |
| `/cadp nama,id` | Create Admin Panel | Owner |

### Deploy Token Bot (via GitHub)
| Command | Keterangan | Akses |
|---------|------------|--------|
| `/deploy TOKEN` | Validasi, simpan lokal, **push ke file GitHub** | Premium / Owner |
| `/deldeploy @username_bot` | Hapus lokal + dari file GitHub | Premium / Owner |
| `/cekdeploy` | List semua token + meta | **Owner only** |

Set di `settings.js` / env: `GITHUB_TOKEN`, `GITHUB_OWNER`, `GITHUB_REPO`, `GITHUB_FILE_PATH` (default `deployed-bots.txt`).

### Cek Informasi
| Command | Keterangan |
|---------|------------|
| `/cekid` | ID + info pengirim |
| `/cekinfo @username` / `id` | Info user |

### Lainnya
- `/start` `/menu` — Menu utama (Rich Message + Premium Emoji)
- `/tqto` — Thanks To + developer
- Tombol berwarna (`style`) — Bot API 9.4

---

## Role

| Role | Akses |
|------|--------|
| **Owner** | Semua fitur |
| **Premium** | Create panel (sampai max plan), cek info |
| **User** | `/cekid`, `/cekinfo`, `/tqto`, menu |

Atur di `settings.js`: `OWNER`, `PREMIUM`, `PREMIUM_MAX_PLAN`.

---

## Instalasi

1. Upload ke server (egg Node.js 20–23).
2. Set env / `.env`:
   ```env
   BOT_TOKEN=token_botfather
   PTERO_URL=https://panel.kamu.com
   PTERO_API_KEY=ptla_xxx
   ```
3. Edit `settings.js` — isi `OWNER`, `NEST_ID`, dan `EGG_ID` (egg NodeJS kamu).
   Startup / docker image / env **otomatis diambil dari egg** — tidak perlu diisi ulang.
4. `npm install && npm start`

### Premium Emoji
File `emojiprem.js` berisi mapping emoji → custom emoji ID.
Dipakai lewat `emoji('🚀')` yang menghasilkan tag `<tg-emoji emoji-id="...">🚀</tg-emoji>`.

**Syarat:** Owner bot punya Telegram Premium agar custom emoji tampil di private/group/supergroup.

---

## Struktur

```
├── index.js
├── settings.js
├── emojiprem.js      # Master emoji premium
├── caprem.js         # Contoh caption style (referensi)
├── package.json
└── utils/
    ├── richMessage.js
    ├── pterodactyl.js
    ├── database.js
    └── role.js
```

---

## Catatan

- DC ID & tanggal akun **tidak tersedia** via Bot API.
- Pastikan ada allocation kosong di node Pterodactyl.
- Rich Message fallback ke pesan biasa jika API gagal.
# token1