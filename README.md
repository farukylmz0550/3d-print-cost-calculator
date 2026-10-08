# 3D Yazıcı Maliyet Hesaplayıcı

> 3D baskı alacaklarınızın gerçek maliyetini ve satış fiyatını hesaplayan tek dosyalık, internet gerektirmeyen bir araç.

Tarayıcınızda açın, sabit ayarlarınızı (filament fiyatı, elektrik, fire, kâr oranı, amorti) bir kez girin, profil olarak kaydedin. Sonra sadece her baskının ağırlığını ve süresini yazıp **Hesapla**'ya basın.

---

## Özellikler

| | |
|---|---|
| 🧮 **Şeffaf hesap** | Filament, elektrik ve amorti kalemleri ayrı ayrı gösterilir |
| 🏷️ **Maliyet ≠ kâr** | Üretim maliyeti (kâr hariç) ve kâr payı ayrı satırlarda; en altta satış fiyatı |
| 💾 **Profiller** | Sabit ayarlarınızı isim vererek kaydedin/yükleyin/silin — tarayıcıda saklanır |
| 📦 **Yedekleme** | Tüm profilleri JSON olarak dışa/içe aktarın |
| 🌍 **TR/EN** | Türkçe ve İngilizce arayüz, tek düğmeyle geçiş |
| 💱 **Para birimi** | ₺, $, €, £ — profil ile birlikte kaydedilir |
| 🌓 **İki tema** | Fine Porcelain × Burnt Ochre (açık) · Ink & Copper (koyu) |
| 🔒 **Gizlilik** | Veri hiçbir yere gönderilmez; sunucu, hesap, çerez yok |
| ⚡ **Tek dosya** | `index.html` — çift tıklayın, çalışır |

## Hesaplama

```
Filament        = baskı ağırlığı ÷ 1000 × filament fiyatı × (1 + fire%)
Elektrik        = (yazıcı gücü ÷ 1000) × baskı süresi × kWh fiyatı
Amorti          = sabit tutar
──────────────────────────────────────────────────────────────
Üretim maliyeti = filament + elektrik + amorti          (kâr hariç)
Kâr payı        = üretim maliyeti × kâr oranı %
Satış fiyatı    = üretim maliyeti + kâr payı
```

**Örnek:** 85 g PLA, 6,5 saat baskı; filament 650 ₺/kg, 150 W, elektrik 2,55 ₺/kWh, %5 fire, %30 kâr, 10 ₺ amorti →

| Kalem | Tutar |
|---|---:|
| Filament | 59,61 ₺ |
| Elektrik | 2,49 ₺ |
| Amorti | 10,00 ₺ |
| **Üretim maliyeti** | **72,10 ₺** |
| Kâr payı (%30) | 21,63 ₺ |
| **Satış fiyatı** | **93,73 ₺** |

## Kullanım

1. `index.html` dosyasını herhangi bir tarayıcıda açın.
2. **Sabit Ayarlar** bölümünü doldurun; **Para birimi**'ni seçin (₺ / $ / € / £).
3. **Baskı Bilgileri**'ne slicer'dan aldığınız ağırlığı ve süreyi girin, **Hesapla**'ya basın.
4. **Profiller** bölümünden ayar setinizi kaydedin; farklı malzemeler/fiyatlar için ayrı profiller tutun.
5. Yedeklemek için **Dışa aktar**, başka bir bilgisayara taşımak için **İçe aktar**.
6. Sağ üstteki **EN/TR** düğmesiyle arayüz dilini değiştirin.

## Tasarım

Arayüz, [Book Shelf](https://github.com/farukylmz0550/bookshelf-web) projesinin **UI Design Language** dokümanını izler:

- **Tema 1 — Fine Porcelain × Burnt Ochre:** `#FAF0E1` zemin, `#BB4F35` aksan; sıcak ve sakin
- **Tema 2 — Ink & Copper:** `#1D2020` zemin, `#C17A5E` aksan; koyu ve derin
- **Tipografi:** Noto Serif (başlıklar) · Noto Sans (arayüz) · Noto Sans Mono (sayısal değerler)
- **Geometri:** 4/8/12 px yarıçap ailesi, sade kenarlıklar, kısıtlı gölge

Bilinçli olarak **kaçınılan** şeyler: glassmorphism, gradient ağırlıklı "modern" şablonlar, generic SaaS dashboard görünümü, gereksiz kart yığını.

> İlke: *Clarity before decoration* — netlik, süslemeden önce gelir.

## Teknik

- Tek `index.html`; bağımlılık yok, derleme yok, sunucu yok
- Profiller `localStorage`'da; dil, tema ve para birimi tercihi de tarayıcıda kalır
- Sayı biçimleme dile göre değişir: `tr-TR` (72,10 ₺) / `en-US` (72.10 $)
- Noto fontları Google Fonts'tan yüklenir (bağlantı yoksa sistem fontlarına düşer, sayfa çalışmaya devam eder)
- `prefers-reduced-motion` desteği, klavye erişilebilirliği, `aria-live` sonuç güncellemesi

## Lisans

GPLv3 — bkz. [LICENSE](LICENSE).
