# Bir Hadis Bir Gün · senaryo formatı ve KURALLAR

Kanal: **@birhadis.birgun** · her akşam **20:30** · ses **Gemini Iapetus** (tempo 0.95) · 45–55 sn dikey Reels.
Görsel: yüzsüz, sinematik, stilize 3D çizim (FLUX.2-klein, `kanal/ayar.py`), uhrevi ney benzeri fon müziği, sonda kaynaklı hadis kartı.

## 1. Doğruluk kuralları (en önemlisi: tek hata kanalı bitirir)
- **Sadece Kur'an ve SAHİH (ya da Tirmizî'nin "hasen sahih" dediği) hadis.** Zayıf, mevzu, "garîb" rivayet YOK.
  Bilinen tartışmalı rivayetler (ör. İbn Mes'ûd'un "beş şey" versiyonu) kullanılmaz; aynı anlamın sahih versiyonu seçilir.
- Her hadis/ayet için **en az 2 güvenilir kaynak** (hadeethenc.com, Diyanet Hadislerle İslam, hadis portalları, kaynak kitap no):
  kitap + bab/numara + râvi yazılır, `kaynaklar` alanına URL'leriyle eklenir. Ayetlerde **Diyanet meali** esas.
- Hadis cümlesi ekrana ve sese **anlamı bozulmadan, kaynağa sadık** yazılır; kısaltılırsa anlam değişmemeli.
- **Fetva/fıkıh hükmü YOK** (haram mı, caiz mi, nasıl kılınır, mezhebe göre değişen konular). Diyanet ile çelişen hiçbir şey yok.
- Tartışmalı "Kur'an sayı mucizesi" iddiaları, siyaset, mezhep/cemaat tartışması, başka dinleri küçümseme YOK.
- Korkutarak değil, umut + sorumlulukla anlat (ahiret konularında da). Kimseyi yargılama; "biz" dili.

## 2. Görsel kurallar
- Peygamberler, sahabe, ehl-i beyt, melekler **ASLA çizilmez, sembolle bile kişileştirilmez.** Hz. Peygamber'den sadece söz aktarılır.
- Tüm figürler **yüzsüz** (motor stili zaten zorlar). Erkekler başı açık/sade kıyafet; başörtüsü sadece kadın olarak tarif edilen figürde.
- İnsan olmayan sahnelere `"insan": false` ekle (ayrı "boş sahne" stili kullanılır, model figür eklemez) ve prompt'a "no people" yaz.
- Şehir/sokak/pencere manzarası arka planında: "plain modern apartment blocks only in the background, no domes, no spires, no towers, no religious buildings" ekle (model arka plana kilise/haç koyabiliyor; 11 Kasım'da 001'de yakalandı). Cami gerekiyorsa sadece tarif edilen hilalli cami.
- Kişi sayısını açık yaz ("ONE single…", "two … men"). Camiler: "dome topped by a golden crescent finial, no crosses".
- Yazı/hat/levha isteme. Mushaf gösterilecekse saygılı (örtülü, rahlede, yazı görünmeden). Kan, yara, şiddet yok.

## 3. Bölüm yapısı (episodes/NNN_slug.json)
- 8 sahne, toplam 80–95 kelime (≈45–55 sn).
  1. **Kanca** (0–3 sn): "sen"e dönük soru ya da çarpıcı tek cümle ("Kıyamet günü hiç kimse yerinden kıpırdayamayacak.").
  2–4. Günlük hayattan somut sahne (trafik, maaş günü, telefon, aile, komşu…).
  5. **Hadis/ayet** cümlesi, `"yer": "Buhârî, Edeb 76 · Müslim, Birr 107"` etiketiyle.
  6–7. Uygulama: bugün ne yapabilirim? (küçük, somut).
  8. Kapanış: kısa dua ya da paylaşma çağrısı ("… bir kardeşine gönder").
- Alanlar: `id, slug, title (2–3 kelime), seed (benzersiz), characters {}, scenes[{text, prompt, yer?, sicak?, sis?, insan?}],
  hisse (son kart: hadisin/ayetin kendisi), kaynak (kartta görünen kısa kaynak), kart_baslik ("HADİS-İ ŞERİF" / "ÂYET-İ KERÎME"),
  caption, hashtags (TAM 5, sonuncusu #birhadisbirgün), kaynaklar [URL + not]`.
- caption: 1. satır kısa merak cümlesi + emoji; boş satır; 1–2 cümle + izleyiciye kişisel soru; boş satır;
  "Kaynak: …"; boş satır; "Her akşam bir hadis, bir gün. Takip et 🤍".
- `say` gerekirse okunuş için (Arapça kelimeleri Türkçe okunuşla yaz; ses modeli yabancı yazıyı okuyamaz).

## 4. Bölüm türleri (karışım)
- **Bir Hadis, Bir Gün** (ana tür, haftada 4–5): yukarıdaki yapı.
- **Kur'an'da gerçekte ne yazıyor?** (haftada 1): bilinen bir yanlış/eksik bilgiyi ayet + Diyanet mealiyle düzeltme. `kart_baslik: "ÂYET-İ KERÎME"`.
- **Benimle birlikte** (haftada 1–2, çizimsiz motion grafik; motoru hazırlanıyor): sahih kaynaklı kısa dua/zikir, okunuş + anlam + sayaç,
  sonda "kaydet, her gün tekrar et".

## 5. Örnek hesaplardan dersler
`docs/rakip_dersleri.md` (islamimasyon, bir_kissa, ayetvekainat). Metinlerini, seri adlarını ve görsel kimliklerini ASLA kopyalama.
