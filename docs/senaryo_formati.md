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

---

## 13 Kasım: İLK 3 SANİYE kuralları (ZORUNLU, diğer kurallarla çelişirse bu geçerli)

Veri: 8 kanalda izleyici ortalama 5-13 sn'de kaydırıyor. Instagram videoyu önce küçük bir test grubuna gösteriyor; izlenme süresi, sona kadar izlenme ve DM ile gönderilme iyi değilse yaymıyor. Reels izleyicisi ~1,4 sn'de karar veriyor ve izlemelerin yarısından fazlası ses kapalı başlıyor.

**Motor ne yapıyor (otomatik):** 0. saniyede ekranda büyük kanca yazısı (~3 sn) + ilk 0,8 sn hızlı zoom. Yazı bölümdeki `"kanca_yazi"` alanından gelir; yoksa açıklamanın (caption / instagram_caption) ilk satırından, o da uzunsa ilk cümlesinden. Bu yüzden:
- Her bölüme `"kanca_yazi"` ekle: en fazla 8 kelime, sessizken tek başına merak uyandıran cümle (cevabı vermeden). Seslendirilen ilk cümleyle aynı olmak zorunda değil ama aynı merakı açsın. (Son Mola'da bu alan sahne içindedir ve 2-3 kelimedir; orada mevcut kural geçerli.)
- Açıklamanın ilk satırı da kısa ve merak uyandıran olsun (yedek kanca yazısı olarak kullanılıyor).

**Kanca puanlama (yazdıktan sonra her bölüm için):** İlk seslendirilen cümleyi ve kanca_yazi'yi şu 5 türe göre 1-5 puanla, kendine sor: "Akışta kaydırırken 1,5 sn'de durur muydum?"
1. Ortak dert: izleyicinin yaşadığı ama dile getirmediği bir sıkıntı (Reels'te en güçlüsü)
2. Merak boşluğu: kapanması için izlemek gereken bir soru/boşluk
3. İddialı/ters köşe cümle: doğru ama şaşırtıcı, karşı çıkılası bir iddia
4. Kalıp kırma: beklenmedik bir giriş
5. Görsel şok: ilk karede açıklama isteyen bir görüntü
En yüksek puan 4'ün altındaysa ilk cümleyi yeniden yaz. Selamlama, giriş, "bugün size … anlatacağım", tarih/yer ile başlamak YASAK; en çarpıcı an ilk cümlede. Doğruluk kuralları aynen geçerli (abartı/uydurma yok).

**Gönderilme (DM) sebebi:** Instagram'da yeni kişilere ulaştıran en güçlü sinyal videonun DM ile birine gönderilmesi. Her bölümün SON seslendirilen cümlesi (ya da kapanış kartı alt yazısı), izleyicinin videoyu belirli birine göndermesi için doğal bir sebep versin; TEK cümle, dilenmeden: "Bunu her ay sonu batan arkadaşına gönder.", "Bunu gece yolculuğu seven birine gönder." Açıklamadaki tek çağrı kuralı aynen kalır (bu cümle videonun içinde).
