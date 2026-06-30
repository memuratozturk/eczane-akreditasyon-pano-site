# Eczane Akreditasyon Panosu — Üyelik Sitesi

Hastane eczaneleri için **TÜSKA** ve **SKS Hastane (Sürüm 6.1) – İlaç Yönetimi (SİY)** akreditasyon
hazırlık panosu. Tanıtım sayfası herkese açıktır; panonun tamamı **üyelik (erişim kodu)** ile açılır.

## Nasıl çalışır?

- `index.html` — herkese açık tanıtım + **Giriş / Üye ol** paneli + ödeme talimatı (KVKK onaylı form).
- `pano.enc.json` — panonun **AES‑256‑GCM** ile şifrelenmiş hâli. Doğru **erişim kodu** olmadan açılamaz.
- Üye, erişim kodunu girer → içerik tarayıcıda çözülür → pano açılır (kod cihazda saklanır, çevrimdışı çalışır).
- `yonetici.html` — yöneticiye özel araç: içeriği güncellemek / erişim kodunu değiştirmek için yeni
  `pano.enc.json` üretir.

## Satış akışı (manuel)

1. Ziyaretçi "Üye ol" formunu doldurur → talep size **WhatsApp/e‑posta** ile ulaşır, ödeme talimatı görünür.
2. Ödeme size ulaşınca → kişiye **erişim kodunu** iletirsiniz.
3. Kişi kodu girer → pano açılır.

## Kurulum / düzenleme

`index.html` içindeki `CFG` bloğunu kendi bilgilerinizle doldurun:

```js
const CFG = {
  fiyat:    "₺499",
  whatsapp: "905XXXXXXXXX",   // ülke kodu + numara, + ve boşluk yok
  email:    "ornek@eposta.com",
  odeme: { ad: "AD SOYAD", iban: "TR.. ....", papara: "" }
};
```

Erişim kodunu değiştirmek / içeriği güncellemek için `yonetici.html` aracını kullanın.

## Önemli notlar

- ⚖️ **KVKK:** Form, açık rıza onayı içerir. Kişisel verileri yalnızca talep değerlendirmesi ve iletişim için kullanın.
- 🧾 **Vergi/fatura:** Gelirin mevzuata uygun şekilde faturalandırılması sizin sorumluluğunuzdadır.
- 🔐 **Güvenlik:** İçerik gerçek şifreleme ile korunur; erişim kodu paylaşılmamalıdır. Kod sızarsa
  `yonetici.html` ile içeriği yeni kodla yeniden şifreleyin.
- 🩺 Pano bir **hazırlık/eğitim aracıdır**; bağlayıcı resmî metin için TÜSKA SAS ve SKS Hastane (Sürüm 6.1) esastır.

## Lisans

Tescilli — bkz. [LICENSE](LICENSE). Tüm hakları saklıdır.
