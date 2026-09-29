# v6 KURULUM REHBERİ · Cowork

**Bu dosya senin için; projeye yükleme.** Yapıştıracağın bütün metinler en altta, "Yapıştırılacak metinler" bölümünde.

Bu sistem, önceki `Iyilestirme_Onerileri_ve_Komutlar.md` dosyasındaki komutların yerini alır. Oradaki bilinen düzeltmeler `04_KAYNAK_DEFTERI.md`'ye taşındı.

---

## 1. Neden yeni bir sistem?

Mevcut sistem çalışıyor ama 88'de takılıyor. Sorun metinde değil, sistemin yapısında:

| Sorun (v5) | Sonucu | v6'daki çözüm |
|---|---|---|
| Metni yazan, kendi metnini puanlıyor | Öz puan ~90, bağımsız okuma 88. Dil modelleri kendi ürettikleri metni kayırma eğilimindedir [1]. | Yazan, puanlayan ve düzelten **ayrı çalışmalar**. Hakem olguları web'de kendisi kontrol eder. |
| Dış kontrol yok, düzeltme yine modelin kendi yargısına dayanıyor | Dış geri bildirim olmadan kendini düzeltmenin güvenilir olmadığı, akıl yürütme görevlerinde gösterildi [2]. | Her olgu **web'de doğrulanıyor**; hakem en az iki olguyu bağımsız kontrol ediyor; insan iki noktada onay veriyor. |
| 62 kB'lık brifing, onlarca kod, sayaç ve kota | Model kaliteden çok sayaç kovaladı: güçlü cümleler silindi, yapay çıkış jestleri eklendi, kendi yeni kalıplarını üretti. | **15 ilke + 2 örnek senaryo + 1 ölçüt.** Anthropic'in rehberine göre iyi seçilmiş örnekler, çıktının doğruluğunu, tutarlılığını ve kalitesini belirgin biçimde artırır [3]. |
| Uzun bağlam: 62 kB'lık brifing ve her partide büyüyen "kullanılmış listesi" (P01 41 kB → P18 108 kB) | Uzun bağlamın ortasındaki bilgi daha az kullanılır [4]. | Daha az ve daha kısa dosya; her adım yalnızca gerekenleri okur. |
| Son metin P ve D dosyalarına dağılmış | Yanlış sürümün dizgiye gitme riski var. | Bölüm 1–3 için **tek temel dosya** hazır. |
| İnsan kontrolü yok | Sistematik bir hata 88 senaryoya yayılabilir. | **Kalibrasyon kapısı** (ilk üç senaryodan sonra) ve **bölüm onayı**. |

---

## 2. Cowork'ün bu kurulumu etkileyen özellikleri

- **Her zamanlanmış çalışma ayrı bir oturumdur** [6]. Önceki çalışmanın konuşmasını görmez; projenin talimatını ve dosyalarını kullanır (bugünkü "Başlamak" görevin de böyle çalışıyor). Bu yüzden hattın durumu dosyalarda tutuluyor.
- **Proje hafızası projeye özeldir:** Claude bir projedeki görevlerden öğrendiklerini aynı projedeki sonraki görevlerde kullanır [5]. Eski projenin hafızası v5 alışkanlıklarını taşıyabilir; bu yüzden **yeni bir proje** açıyoruz.
- **Zamanlanmış görevler bulutta çalışır.** Bilgisayarın kapalıyken de çalışırlar, ama bilgisayarındaki bir klasöre bağlı bir proje zamanlanmış görevde kullanılamaz [6]. Yeni projeyi yerel klasörden değil, dosya yükleyerek kur (bugünkü projen de böyle).
- **Web araması bulutta çalışır.** Web'den sayfa okuma, arama sonuçları ve paylaşılan adreslerle sınırlıdır [7].
- **Dosya sayısı arttıkça** proje, dosyaları baştan sona okumak yerine arama ile parça getirmeye (RAG) geçebilir [8]. Bir kullanıcı sohbet projelerinde bu geçişin 13 dosya civarında başladığını bildirmiş [9]. Cowork çalışmaları dosyaları betikle okuyabiliyor gibi görünüyor (v5 kelimeleri betikle saymış). Yine de bunu 6. adımdaki testle doğrulayacağız.
- **Çok adımlı Cowork görevleri, kısa bir sohbete göre çok daha fazla kullanım harcar** [7]. Saatlik tempo ve seçilen model, kullanım limitini doğrudan etkiler.

---

## 3. Adım adım kurulum

### Adım 1 · Eski görevi durdur (2 dk)
"Başlamak" görevinde **Aktiv** düğmesini kapat. Görevi silme; geçmişi dursun.

### Adım 2 · Yedek al (5 dk)
Eski projedeki **claude** klasörünü indir. Bölüm 1–3'ün v5 dosyaları GitHub'da da var. Bugün Bölüm 4 için v5-P19 gibi dosyalar oluştuysa bunları bilgisayarında sakla; v6 bunları kullanmaz.

### Adım 3 · Yeni proje aç
- Ad: **Zihin Savaşçısı v6**
- Yerel klasörden değil, **boş proje** olarak aç.
- Proje ayarlarında hafızayı kapatma seçeneği görürsen kapat; hattın bütün durumu dosyalarda tutuluyor.

### Adım 4 · Dosyaları yükle (Dateien → Hinzufügen)
Yalnızca bu 9 dosya:

| Dosya | Nereden |
|---|---|
| `01_BRIFING_v6.md` | bu klasör |
| `02_OLCUT_95.md` | bu klasör |
| `03_ORNEKLER.md` | bu klasör |
| `04_KAYNAK_DEFTERI.md` | bu klasör |
| `11_Bolum1_temel.md` | bu klasör |
| `12_Bolum2_temel.md` | bu klasör |
| `13_Bolum3_temel.md` | bu klasör |
| `Sosyal_Bolum4_guncel.md` | eski proje |
| `Sosyal_Bolum5_guncel.md` | eski proje |

**Yükleme:** v5 brifingi, v5 çıktıları, Bölüm 1–3'ün güncel dosyaları, bu rehber, değerlendirme raporları. Hepsi gereksiz bağlam ve eski kural demek.

### Adım 5 · Proje talimatını yaz (Projektanweisungen festlegen)
Aşağıdaki **A** metnini yapıştır.

### Adım 6 · Kurulum testi (10 dk)
Projede yeni bir görev başlat, **C** metnini yapıştır ve sonucu kontrol et:

| Soru | Beklenen | Değilse |
|---|---|---|
| 2 · Brifing tam okunuyor mu? | "Tam" ve ilk/son satır birebir doğru | Dosyalar arama ile okunuyor demektir. Bana dön; dosyaları birleştirip sayıyı azaltırız. |
| 3 · Bölüm 1 dosyası | Son satır `DOSYA SONU`, 18 senaryo başlığı | Aynı |
| 4 · Web araması | Bir başlık ve adres | Ayarlardan web aramasını aç; açılmıyorsa hat olgu doğrulayamaz. |
| 5 · Dosya kaydı | Dosya projede görünüyor | Çıktıların nereye kaydedildiğini sor; brifingin 7.3 bölümünü ona göre güncelleriz. |
| 6 · Hafıza | Boş ya da ilgisiz | v5 kuralları görünüyorsa proje talimatındaki uyarı yeterli; yine de not al. |

Testten sonra `TEST · silinebilir.md` dosyasını sil.

### Adım 7 · Zamanlanmış görevi kur
- **Ad:** v6 Hattı
- **Anweisungen:** **B** metni
- **Projekt:** Zihin Savaşçısı v6
- **Wiederholung:** Stündlich
- **Model:** Seçebildiğin en güçlü model (ör. Opus). Düşünme/efor ayarı varsa en yükseği.
- **Berechtigungen:** Auto

### Adım 8 · İlk çalışmayı elle başlat (Jetzt ausführen)
`v6-Y01 · Senaryo 1, 2, 3.md` oluşunca şunlara bak:
- Başında "Okunanlar" satırı var ve dosyaların yanında "tam" yazıyor.
- KAYNAK NOTLARI'nda gerçek kaynak başlıkları ve adresleri var.
- Metinde [DOĞRULA] ya da köşeli parantezli not yok.
- Dosyada puan yok (puanı H verir).
- KELİME SAYILARI'ndan sonra `--- HAKEM BURADA DURUR ---` satırı var.
- Son satır `DOSYA SONU`.

### Adım 9 · Kalibrasyon kapısı (yaklaşık 3 saat sonra, 30 dk)
`v6-S01` oluşunca hat durur ve "Bekleniyor: ONAY · Parti 01" yazar.
1. `v6-S01`'deki üç senaryoyu **sesli** oku. `v6-H01`'deki puanlara ve kusurlara bak.
2. **D** şablonuyla `ONAY · Parti 01.md` dosyasını oluştur. Dosyayı bilgisayarında yazıp yükleyebilirsin ya da projede bir göreve "Şu içerikle 'ONAY · Parti 01.md' dosyasını projeye kaydet: …" diyebilirsin.
3. Genel notlar en değerli kısım: "Ton daha sıcak olsun", "Hakem fazla cömert, şu senaryo 95 değil çünkü …" gibi. Bu notlar bundan sonraki bütün adımlara uygulanır.

**Beğenmediysen:** Notlarını **E** şablonuyla bir `NOT · Kalibrasyon.md` dosyasına yaz, sonra `v6-Y01`, `v6-H01` ve `v6-S01` dosyalarını sil. Hat P01'i notlarınla yeniden yapar ve yine onayını bekler.

### Adım 10 · Her bölümün sonunda (bölüm başına 1–2 saat)
`v6-B[N]` oluşunca hat "Bekleniyor: ONAY · Bölüm N" der.
1. B dosyasındaki **İNSANA SORULAR** bölümünü oku; önerilen en zayıf üç senaryoyu sesli oku.
2. İstersen **okur panelini** çalıştır (**F**; ayrı bir projede). Çıktısını ana projeye yükle.
3. Kendine zarar, travma ya da şiddet içeren senaryolara (ör. 9, 39, 54) mümkünse bir klinik psikolog baksın.
4. **D** şablonuyla `ONAY · Bölüm N.md` dosyasını ekle. Hat notlarını uygulayıp `v6-BB[N]` baskı metnini üretir.

### Adım 11 · Temizlik (isteğe bağlı)
Bir bölümün `v6-B` dosyası oluştuktan sonra o bölümün Y, H ve S dosyalarını indirip projeden kaldırabilirsin; hat bunları artık aramaz. **B ve BB dosyalarını kaldırma.**

### Sonradan bir düzeltme istersen
Bir **NOT** dosyasına yaz (ör. `NOT · Bölüm 2 düzeltmeleri.md`) ve o bölümün `v6-BB` dosyasını sil. Hat BB'yi notlarınla yeniden üretir. Kitap sonundaki K denetiminin önerileri de bu yolla uygulanır.

---

## 4. Takvim ve beklenti

- **Süre:** Parti başına 3 çalışma; yaklaşık 30 parti ve bölüm adımlarıyla toplam ~100 çalışma. Saatlik tempoda **4–5 gün**, artı senin onay süren.
- **Senin zamanın:** Kalibrasyon ~30 dk; her bölüm 1–2 saat; toplam ~8–10 saat.
- **Kalite:** Hakemin 95'i, v5'in 88'inden belirgin biçimde iyi bir metin demektir. Gerçek 95'i ise senin sesli okuman, okur paneli ve hassas senaryolarda bir uzmanın bakışı garanti eder. Sistem bunlar için durup seni bekliyor.

---

## 5. Sorun giderme

| Belirti | Ne yapmalı |
|---|---|
| Çıktının son satırı `DOSYA SONU` değil | Bir şey yapma; sonraki çalışma adımı yeniden yapar. İstersen yarım dosyayı sil. |
| Aynı adımın iki dosyası var | En yenisi geçerli; eskisini silebilirsin. |
| "Bekleniyor: ONAY · …" yazıp duruyor | İlgili ONAY dosyasını ekle. |
| Çalışmalar kullanım limitine takılıyor | Görevi duraklat, limit yenilenince aç ya da tempoyu seyrelt. |
| Çıktının başında "UYARI: … tam okunamadı" | Bitmiş bölümlerin ara dosyalarını kaldır ve testi (C) tekrarla. |
| Hakem neredeyse her şeye 95+ veriyor | ONAY ya da NOT dosyasına örnekle yaz: "Şu senaryo 95 değil, çünkü …". Genel notlar hakeme de uygulanır. |
| Metinler örnek senaryolara fazla benziyor | Genel nota yaz: "Örneklerin cümle ve iskeletlerini kopyalama." |
| Hat Bölüm 4'e geçmiyor | `v6-BB3` dosyasının son satırını kontrol et. |

---

## 6. Yapıştırılacak metinler

### A · Proje talimatı (Projektanweisungen festlegen)

```text
Bu proje "Zihin Savaşçısı · Sosyal" kitabının v6 editörlük hattıdır.
Tek kural dosyası 01_BRIFING_v6.md'dir. v5 brifingi, v5 kodları ve sayaçları geçersizdir; proje hafızasında v5'ten kalan bir alışkanlık varsa uygulama.
Dosyaları arama sonuçlarından parça olarak değil, baştan sona okuyarak kullan.
Kaynak, sayı, yıl ya da alıntı uydurma; emin olmadığın şeyi "doğrulanamadı" diye yaz.
Yalnızca zamanlanmış görev ya da ben açıkça istediğimde hattın sıradaki adımını yap.
```

### B · Zamanlanmış görev komutu (Anweisungen)

```text
01_BRIFING_v6.md dosyasını baştan sona oku. 7.4'teki DURUM KURALI ile sıradaki tek adımı bul ve 8. bölümdeki tanımına harfiyen uyarak uygula.
Soru sorma, onay bekleme.
Sıradaki adım bir ONAY ise dosya oluşturma; yalnızca neyi beklediğini yaz ve dur.
Çıktıyı brifingdeki adla .md dosyası olarak projeye kaydet; son satırı DOSYA SONU olsun. Sonra dur.
```

### C · Kurulum testi (projede elle başlatılan bir görev)

```text
Bu bir kurulum testi. Kitapla ilgili hiçbir adım uygulama; yalnızca şu soruları cevapla ve sonucu tek bir tabloda ver:
1. Proje dosyalarını listele (ad ve yaklaşık boyut).
2. 01_BRIFING_v6.md dosyasını dosya okuma aracıyla ya da betikle baştan sona okuyabiliyor musun, yoksa yalnızca arama sonuçlarından parçalar mı görüyorsun? Kanıt olarak dosyanın ilk ve son satırını aynen yaz.
3. 11_Bolum1_temel.md dosyasının son satırını aynen yaz ve dosyada "### " ile başlayan kaç senaryo başlığı olduğunu say.
4. Web araması yapabiliyor musun? "Sonnentag Fritz 2007 Recovery Experience Questionnaire" diye ara; ilk sonucun başlığını ve adresini yaz.
5. İçinde yalnızca "deneme" yazan "TEST · silinebilir.md" adlı bir dosyayı projeye kaydedebiliyor musun? Dene ve nereye kaydedildiğini yaz.
6. Proje hafızasında bu kitapla ya da v5 kurallarıyla ilgili bir şey var mı? Varsa kısaca yaz.
```

### D · ONAY şablonu

```text
ONAY · Parti 01
(Bölüm onayı için ilk satır: ONAY · Bölüm 1)

Karar: DEVAM
(DUR yazarsan hat, bu satırı DEVAM yapana kadar bekler.)

Genel notlar (bundan sonraki bütün adımlar için):
- 

Senaryo notları:
- 1: 
- 2: 
- 3: 

Okur paneli: (yüklediysen dosya adı, yoksa "yok")

DOSYA SONU
```

### E · NOT şablonu (kapı açmadan not bırakmak için)

```text
NOT · Kalibrasyon

Genel notlar:
- 

Senaryo notları:
- 

DOSYA SONU
```

### F · Okur paneli (ayrı proje: "Zihin Savaşçısı · Okur Paneli")

Bu projeye **brifingi, ölçütü ve örnekleri yükleme**; puanı kuralları bilmeyen bir okur versin. Her bölümde yalnızca o bölümün `v6-B[N]` dosyasını yükle ve yeni bir görevde şu metni çalıştır. (Proje talimatını boş bırakabilirsin.)

```text
Ekteki dosyada bir kitabın bir bölümü var. Yalnızca "SON METİN" başlıklı bölümü oku; dosyanın başka hiçbir bölümüne (bulgular, puanlar, değişiklikler) bakma.

Sırayla beş farklı okur ol; her biri kendi sesiyle konuşsun:
1. Deniz, 23, üniversite son sınıf öğrencisi; hayır demekte zorlanıyor.
2. Ayşe, 38, iki çocuklu ve çalışıyor; aile, akraba ve komşu baskısını iyi tanıyor.
3. Mehmet, 52, esnaf; kitap okumayı pek sevmez, "psikoloji laflarına" şüpheyle bakar.
4. Elif, 34, klinik psikolog; yanlış, eksik ya da zarar verebilecek öneriyi arar.
5. Can, 45, yayınevi editörü; ritim, tekrar ve sayfa akışına bakar.

Her okur her senaryoya 1–10 arası bir puan versin ve şu altı soruyu birer satırla cevaplasın:
- Bu durum gerçekçi mi?
- Kendimi ya da tanıdığım birini gördüm mü?
- Önerilen cümleyi gerçekten kurar mıydım?
- Cevap sayfası bana yeni bir şey öğretti mi?
- Aklımda bir cümle kaldı mı? Hangisi?
- Beni rahatsız eden, sıkan ya da inandırıcı bulmadığım bir yer var mı? Alıntıyla göster ve bir düzeltme öner.

Kurallar:
- Nazik değil, dürüst ol. 9 ve 10'u yalnızca gerçekten etkileyen senaryolara ver.
- Gerekçesiz puan yok; bir sorunu gösterirken metinden alıntı yap.
- Elif, güvenlik açısından riskli bir öneri görürse bunu ayrıca işaretlesin.

Çıktı (dosya adı: "v6-O[N] · Bölüm N okur paneli.md"):
1. Senaryo başına beş okurun puanı ve 100'e çevrilmiş ortalama.
2. En düşük beş senaryo ve her birinde en çok tekrarlanan şikâyet.
3. Birden çok okurun takıldığı ortak sorunlar.
4. Klinik uyarılar.
5. Okurların aklında kalan cümleler (bunlar korunacak).
Son satır: DOSYA SONU
```

**Not:** Bu panel bir simülasyondur. Bölüm başına 8–10 gerçek okura 10 senaryo okutup aynı altı soruyu sormak en güvenilir sınamadır.

---

## Kaynaklar

1. Panickssery, Bowman ve Feng (2024), [LLM Evaluators Recognize and Favor Their Own Generations](https://arxiv.org/abs/2404.13076), NeurIPS 2024.
2. Huang ve ark. (2024), [Large Language Models Cannot Self-Correct Reasoning Yet](https://proceedings.iclr.cc/paper_files/paper/2024/hash/8b4add8b0aa8749d80a34ca5d941c355-Abstract-Conference.html), ICLR 2024.
3. Anthropic, [Use examples (multishot prompting) to guide Claude's behavior](https://docs.anthropic.com/en/docs/build-with-claude/prompt-engineering/multishot-prompting).
4. Liu ve ark. (2024), [Lost in the Middle: How Language Models Use Long Contexts](https://aclanthology.org/2024.tacl-1.9/), TACL 12.
5. Claude Yardım Merkezi, [Organize your tasks with projects in Claude Cowork](https://support.claude.com/en/articles/14116274-organize-your-tasks-with-projects-in-claude-cowork).
6. Claude Yardım Merkezi, [Schedule recurring tasks in Claude Cowork](https://support.claude.com/en/articles/13854387-schedule-recurring-tasks-in-claude-cowork).
7. Claude Yardım Merkezi, [Get started with Claude Cowork](https://support.claude.com/en/articles/13345190-get-started-with-claude-cowork).
8. Claude Yardım Merkezi, [Retrieval augmented generation (RAG) for projects](https://support.claude.com/en/articles/11473015-retrieval-augmented-generation-rag-for-projects).
9. GitHub, [anthropics/claude-code#25759](https://github.com/anthropics/claude-code/issues/25759): kullanıcı bildirimi, sohbet projelerinde dosya sayısına bağlı RAG geçişi.
