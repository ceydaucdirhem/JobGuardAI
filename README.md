# JobGuard AI — "Is This Job Legit?"

AI destekli iş ilanı dolandırıcılık dedektörü. İş ilanı metnini yapıştırın, Claude
metni analiz edip bir güvenlik puanı, risk dağılımı, şüpheli sinyaller ve şirket
bilgisi tahmini üretsin.

## Kurulum

Node.js (v18+) kurulu olmalı.

```bash
npm install
npm run dev
```

Terminalde çıkan adresi (genelde `http://localhost:5173`) tarayıcıda açın.

## Kullanım

1. Uygulama açıldığında sağ üstteki **"Anahtar Ekle"** butonuna tıklayıp kendi
   Anthropic API anahtarınızı girin ([console.anthropic.com/settings/keys](https://console.anthropic.com/settings/keys)
   adresinden alabilirsiniz). Anahtar yalnızca tarayıcı hafızasında tutulur,
   hiçbir yere kaydedilmez.
2. Ana sayfadaki kutuya bir iş ilanı metni yapıştırın ve **"İlanı Analiz Et"**'e
   tıklayın.
3. Sonuç ekranında dört sekme arasında gezinin: Genel Bakış, Detaylı Analiz,
   Şirket Bilgisi, Ham Rapor.
4. Sol kenar çubuğundaki saat simgesiyle geçmiş taramalarınıza (oturum
   boyunca, hafızada tutulur) göz atabilirsiniz.

## Prodüksiyon derlemesi

```bash
npm run build
npm run preview
```

`dist/` klasörü herhangi bir statik hosting'e (Vercel, Netlify, GitHub Pages
vb.) yüklenebilir.

## Proje yapısı

```
jobguard-ai/
├── index.html                 Vite giriş noktası
├── package.json
├── vite.config.js
├── src/
│   ├── main.jsx                React kök render
│   ├── App.jsx                 Görünüm yönlendirme / durum yönetimi
│   ├── index.css                Global stiller
│   ├── lib/
│   │   ├── theme.js             Renk paleti ve yardımcı fonksiyonlar
│   │   └── analyze.js           Anthropic API çağrısı + prompt şeması
│   └── components/
│       ├── Icons.jsx            Basit satır içi SVG ikon seti
│       ├── Common.jsx           Card, Pill, Logo, Gauge
│       ├── Landing.jsx          Ana sayfa (hero + yapıştırma kutusu)
│       ├── Loading.jsx          Analiz sırasında yükleniyor ekranı
│       ├── AppShell.jsx         Kenar çubuğu + üst bar (sonuç/geçmiş ekranları için)
│       ├── HistoryView.jsx      Geçmiş taramalar listesi
│       ├── ResultView.jsx       Sekme yönlendirme (Genel Bakış/Detaylı/Şirket/Ham)
│       ├── ApiKeyModal.jsx      API anahtarı giriş modalı
│       └── tabs/
│           ├── OverviewTab.jsx
│           ├── DetailedTab.jsx
│           ├── CompanyTab.jsx
│           └── RawTab.jsx
```

## Not

Bu bir demo/prototip uygulamasıdır. "Şirket Bilgisi" sekmesindeki veriler
gerçek bir domain/whois sorgusuna değil, yalnızca modelin ilan metninden
çıkardığı tahminlere dayanır — başvurmadan önce şirketi bağımsız olarak
doğrulamanız önerilir.
