# Türkçe Mikrocopy Bankası

Kural: fiil özneldir — sektörün ve sayfanın işine göre seçilir. "Gönder"/"Başla"/"Keşfet" her sayfaya uyan fiillerdir; her sayfaya uyan fiil hiçbir sayfaya ait değildir. Yasaklı kalıplar: BP21/BP23 (`banned-patterns.md`).

## CTA fiilleri — sektöre göre gerçek örnekler

| Bağlam | Zayıf (jenerik) | Güçlü (özneye ait) |
|---|---|---|
| Rezervasyon (kafe/atölye) | Kayıt ol | **Yerimi ayırt** · Cumartesi cupping'e yaz |
| Özel sipariş (zanaat) | İletişime geç | **Eskiz talep et** · Ölçüyü bırak |
| Deneme dersi (spor) | Hemen başla | **Deneme dersi ayırt** · İlk tırmanış bizden |
| Ürün/demo (SaaS) | Daha fazla bilgi | **Demo iste** · 20 dakikada gör |
| Abonelik (yayın) | Abone ol | **Aboneliği başlat** · Sayı 15 kapına gelsin |
| Dinleme/izleme (medya) | Keşfet | **Yeni çıkışı dinle** · Kataloğu karıştır |
| Menü/katalog | İncele | **Bu haftaki kavurmaya bak** · Rafı gör |

Desen: `[somut nesne] + [kullanıcının kendi eylemi]`. CTA, sistemin ne yapacağını değil kullanıcının ne alacağını söyler.

## Form etiketleri

- Etiketler görünür kalır (placeholder tek başına etiket değildir — erişilebilirlik + otomatik doldurma).
- Kısa ve alanın diliyle: "Ad Soyad", "E-posta", "Telefon numarası" — "Adınızı giriniz" değil.
- Zorunluluk işareti tutarlı (ya `*` ya "(isteğe bağlı)" — ikisi birden değil).
- Buton, formun vaadini taşır: "Gönder" yerine formun sonucunu söyleyen fiil ("Yerimi ayırt", "Eskiz talep et").

## Hata ve durum mesajları

- Suçlamasız, çözüm gösterir: ~~"Geçersiz giriş"~~ → "E-posta adresinde bir eksik var gibi — @ işaretinden sonrasını kontrol eder misin?"
- Başarı somut: ~~"İşlem başarılı"~~ → "Kayıt alındı — Cumartesi 11:00'de görüşürüz."
- Boş durumlar yönlendirir: ~~"Sonuç bulunamadı"~~ → "Bu filtreyle parça çıkmadı — ahşap türünü genişletmeyi dene."

## Ton kalibrasyonu

- Sen/siz kararı sektöre göre: zanaat/yerel/genç marka → sen; hukuk/finans/kurumsal/sağlık → siz. Sayfa içinde asla karışmaz.
- Türkçe karakterler her yerde tam (ğ ş ı İ ç ö ü) — font seçimi bunu garanti etmeli (font-pairings.csv TR notları).
- Ünlem enflasyonu yok: sayfa başına en fazla bir ünlem, o da gerçekten kazanılmışsa.
- Mikrocopy da tasarım malzemesidir: buton metni uzunluğu kompozisyonu etkiler — "Yerimi ayırt" (11 karakter) bir pill butona sığar, "Hemen ücretsiz kaydolmak için tıklayın" sığmaz.
