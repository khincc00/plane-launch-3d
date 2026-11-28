# Plane Launch 3D

Game web 3D: luncurkan pesawat pakai ketapel, upgrade bagiannya, dan terbang sejauh mungkin. Tanpa iklan.

**Main:** https://khincc00.github.io/plane-launch-3d/

- 7 level, setiap level memakai satu pesawat dari aset 3D: Kertas (origami) → Kardus (low poly) → Mainan Kayu (biplan) → Mainan RC → Biplan Ultralight (WW1) → Jet Bisnis → Jet Penumpang (A320). Jarak tiap level 1.000 m sampai 8.000 m.
- Peta dibangun dari potongan aset yang dibongkar lalu digabung per tile: hutan pinus (bioma rumput) dan blok kota (bioma kota). Canyon dan laut tetap prosedural.
- Fisika dengan data pesawat nyata, diskalakan ke ukuran model: berat, lift ½ρv²S·CL, drag CD0 + CL²/πeAR, stall, dorong, angin profil ketinggian + hembusan, thermal, dan kerapatan udara turun dengan ketinggian. Tanpa autopilot: pitch diatur pemain.
- Pesawat dibongkar jadi bagian (badan, sayap, ekor, sirip, mesin, roda, baling-baling). Level 1 hanya bodi; upgrade memasang bagian satu per satu. Upgrade sayap, mesin, ketapel, roket, dan bonus koin.
- Kontrol: tarik ketapel dengan mouse/jari. ← → untuk belok, ↑ ↓ untuk pitch, Spasi untuk roket.

## Mode Live TikTok

Tombol **📡 Live** (atau *Atur Gift* di garasi) membuka pengaturan gift. Ada 5 preset **NAIK** dan 5 preset **TURUN**. Setiap preset punya nama, jumlah koin, angkat %, laju %, dan durasi. Gift dicocokkan dengan jumlah koinnya. Gift beruntun (×N) menumpuk efeknya, maksimal ×10.

Sumber event gift yang diterima:
- **WebSocket**: isi URL di panel, atau buka dengan `?ws=wss://...`. Format JSON yang dikenali: `{event:"gift",data:{giftName,diamondCount,repeatCount,repeatEnd,giftType,nickname}}` (TikFinity/TikTok-Live-Connector), atau JSON sederhana `{type:"gift",gift:{name,coins},user:{nickname},count}`.
- **postMessage**: dari halaman induk, kalau game dipasang dalam iframe.
- **BroadcastChannel** `plane-launch-live`.
- **Tes manual di konsol browser**: `planeGift(koin, jumlah, "Nama", "user")`.

**🔗 Salin link overlay** membuat link berisi semua preset dan URL. Tempel link itu di Browser Source OBS atau TikTok Live Studio.

Isi proyek: `index.html` + folder `assets/` (`assets/planes/p1–p7.glb`, `assets/map/kota.glb`, `assets/map/hutan.glb`). Three.js dimuat dari CDN. Karena aset dimuat lewat fetch, jalankan lewat server statis (mis. GitHub Pages), bukan dibuka langsung dari file.
