<div align="center">

# 💣 Mayın Tarlası — Retro Edition

**Windows 95 estetiği × Modern web mühendisliği**

React 18 · Web Audio API · Portable HTML

<br>

![HTML5](https://img.shields.io/badge/HTML5-E34F26?style=for-the-badge&logo=html5&logoColor=white)
![React](https://img.shields.io/badge/React_18-20232A?style=for-the-badge&logo=react&logoColor=61DAFB)
![JavaScript](https://img.shields.io/badge/JavaScript-F7DF1E?style=for-the-badge&logo=javascript&logoColor=black)
![CSS3](https://img.shields.io/badge/CSS3-1572B6?style=for-the-badge&logo=css3&logoColor=white)

<br>

[🎮 Oyna](#kurulum) · [📸 Ekran Görüntüleri](#ekran-görüntüleri) · [⚙️ Özellikler](#özellikler) · [🏗️ Mimari](#teknik-mimari)

</div>

---

## Hakkında

Klasik Windows Mayın Tarlası oyununun, modern web teknolojileriyle sıfırdan yazılmış tam fonksiyonel bir rekreasyonudur. Tek bir `index.html` dosyasında çalışır — sunucu, build adımı veya bağımlılık kurulumu gerekmez.

## Özellikler

### 🎮 Oyun Motoru
- **İlk Tıklama Koruması** — İlk tıklanan hücre ve 8 komşusu asla mayın olmaz; mayınlar ilk tıklamadan sonra yerleştirilir
- **BFS Flood Fill** — Stack overflow riski olmayan kuyruk tabanlı algoritma ile boş alan açma
- **Chording** — Açık sayılı hücreye tıklayarak (sol veya orta tık) komşu hücreleri toplu açma
- **Win/Loss Detection** — Kapalı hücre sayısı = mayın sayısı → kazanç; mayına basma → tüm mayınlar görünür

### 🎛️ Konfigürasyon
| Zorluk | Grid | Mayın |
|--------|------|-------|
| Başlangıç | 9×9 | 10 |
| Orta | 16×16 | 40 |
| Uzman | 30×16 | 99 |
| **Özel** | **9–60 × 9–60** | **1–989** |

### 🎨 İki Tema
- **Neon (Koyu)** — Koyu mavi-mor arka plan, neon parıltılı sayılar, glow efektleri
- **Win95 (Gri)** — Klasik Windows 95 estetiği: `inset/outset` 3D border'lar, mavi başlık çubuğu, `#c0c0c0` zemin

### 🔊 Ses Efektleri (Web Audio API)
Tüm sesler prosedürel olarak üretilir — harici dosya gerektirmez:
- Hücre açma: kısa, tatmin edici tık + micro bass thump
- Flood fill: yükselen cascade melodisi
- Bayrak koyma/kaldırma: metalik tık
- **Patlama**: 5 katmanlı sinematik ses — derin bass boom + distorted crunch + beyaz gürültü şarapnel + tiz crack + gecikmeli echo boom
- Kazanma: C-E-G-C arpej fanfar
- Sağ üstte 🔊/🔇 toggle ile açılıp kapanabilir

### ✨ Vuruş Hissiyatı
- Hover'da scale + glow efekti
- Tıklamada scale-down basılma hissi
- Açılan hücrelerde bounce animasyonu
- Bayrak dikme spring animasyonu
- Patlama: ekran sarsıntısı + kırmızı flash + parçacık sistemi
- Kazanma: altın flash + konfeti parçacıkları

### 📐 Responsive Tasarım
- Grid, ekranın tamamına dinamik olarak yayılır
- Genişlik öncelikli boyutlandırma — büyük gridlerde yanlarda boşluk kalmaz
- Dikey taşma durumunda scroll desteği
- Pencere boyutu değiştiğinde otomatik yeniden hesaplama

## Kurulum

```bash
# Repoyu klonla
git clone https://github.com/Lucadron/Mine-Sweeper.git

# index.html dosyasını tarayıcıda aç
# Windows
start index.html

# macOS
open index.html

# Linux
xdg-open index.html
```

Hepsi bu kadar. Sunucu yok, `npm install` yok, build yok.

## Kontroller

| Eylem | Kontrol |
|-------|---------|
| Hücre aç | Sol tık |
| Bayrak koy/kaldır | Sağ tık |
| Chording | Açık sayılı hücreye sol tık veya orta tık |
| Yeni oyun | 😊 butonuna tıkla veya "Yeni Oyun" butonu |
| Tema değiştir | 🌙/☀️ butonu |
| Ses aç/kapat | 🔊/🔇 butonu |

## Teknik Mimari

### Teknoloji
- **React 18** — CDN üzerinden, production build
- **Babel Standalone** — Tarayıcıda JSX transpilation
- **Web Audio API** — Prosedürel ses sentezi
- **CSS Variables** — Tema sistemi

### Performans Optimizasyonları
- `React.memo` ile hücre memoization — yalnızca değişen hücreler render edilir
- `useMemo` ile grid hesaplama ve stil önbellekleme
- `useCallback` ile event handler referans kararlılığı
- 60×60 (3600 hücre) gridde sorunsuz çalışır

### Algoritma Karmaşıklığı
| İşlem | Karmaşıklık |
|-------|-------------|
| Mayın yerleştirme | O(W×H) |
| Flood Fill (BFS) | O(W×H) en kötü, O(k) ortalama |
| Komşu sayımı | O(W×H) |
| Win check | O(W×H) |
| Tek tıklama (ortalama) | O(k) where k ≪ N |

### Dosya Yapısı
```
Mine-Sweeper/
├── index.html    # Tüm uygulama — tek dosya, sıfır bağımlılık
├── README.md
└── LICENSE
```

## Lisans

MIT License — detaylar için [LICENSE](LICENSE) dosyasına bakın.

---

<div align="center">

**Lucadron** tarafından 💣 ile yapıldı

</div>
