# Bir Hadis Bir Gün (@birhadis.birgun)

Her akşam 18:00'de, kaynağı belirtilmiş sahih bir hadisi (ya da ayeti) günlük hayattan bir sahneyle anlatan 45–55 sn'lik Reels.
Yüzsüz sinematik yapay zekâ çizimleri, Gemini **Iapetus** sesi, uhrevi fon müziği. Motor Kıssadan Hisse ile ortaktır
(`engine/`); kanala özel görünüm `kanal/ayar.py` içindedir.

## Nasıl çalışır
- **Hazırla** (`hazirla.yml`): sıradaki bölümün sahnelerini çizer (`python -m kanal.ciz`), seslendirip birleştirir
  (`python -m kanal.video`) ve `hazir-<id>` sürümüne koyar (~40 dk). Paylaşımdan sonra otomatik başlar.
- **Günlük paylaşım** (`gunluk-paylasim.yml`, 20:22 TR): hazır olan sıradaki bölümü Instagram'a yükler, `state/posted.json`'a yazar.
- **Yayın kilidi:** `assets/yayinda` dosyası yoksa HİÇBİR şey paylaşılmaz.
- **İstatistik** (`istatistik.yml`), **Bağlantı testi** (`baglanti-testi.yml`).

## Secret'lar (kullanıcı ekler; sohbete asla yapıştırılmaz)
`IG_ACCESS_TOKEN` (sonmola-bot sistem kullanıcısı anahtarı), `GEMINI_API_KEY`, isteğe bağlı `IG_USER_ID`.

## Kurallar
Tüm içerik ve görsel kuralları: `docs/senaryo_formati.md`. Örnek hesap dersleri: `docs/rakip_dersleri.md`.
