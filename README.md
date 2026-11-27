# Plane Launch 3D

Game web 3D: luncurkan pesawat pakai ketapel, upgrade bagiannya, dan terbang sejauh mungkin. Tanpa iklan.

**Main:** https://khincc00.github.io/plane-launch-3d/

- 7 level, setiap level memakai satu pesawat (Kertas → Jet)
- Fisika terbang realistis (lift, drag, stall, angin, thermal)
- Upgrade sayap, mesin/baling-baling, ketapel, roket, dan bonus koin. Setiap upgrade mengubah bentuk pesawat.
- Kontrol: tarik ketapel dengan mouse/jari. ← → untuk belok, ↑ ↓ untuk pitch, Spasi untuk roket.

## Mode Live TikTok

Tombol **📡 Live** (atau *Atur Gift* di garasi) membuka pengaturan gift. Ada 5 preset **NAIK** dan 5 preset **TURUN**. Setiap preset punya nama, jumlah koin, angkat %, laju %, dan durasi. Gift dicocokkan dengan jumlah koinnya. Gift beruntun (×N) menumpuk efeknya, maksimal ×10.

Sumber event gift yang diterima:
- **WebSocket**: isi URL di panel, atau buka dengan `?ws=wss://...`. Format JSON yang dikenali: `{event:"gift",data:{giftName,diamondCount,repeatCount,repeatEnd,giftType,nickname}}` (TikFinity/TikTok-Live-Connector), atau JSON sederhana `{type:"gift",gift:{name,coins},user:{nickname},count}`.
- **postMessage**: dari halaman induk, kalau game dipasang dalam iframe.
- **BroadcastChannel** `plane-launch-live`.
- **Tes manual di konsol browser**: `planeGift(koin, jumlah, "Nama", "user")`.

**🔗 Salin link overlay** membuat link berisi semua preset dan URL. Tempel link itu di Browser Source OBS atau TikTok Live Studio.

Cukup satu file `index.html` (Three.js dari CDN).
