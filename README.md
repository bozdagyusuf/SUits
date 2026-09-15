# SUits

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](LICENSE)

Sabancı Üniversitesi ders programı planlayıcısı. Derslerini kesin / olsa iyi / belki
diye işaretlersin, SUits tüm ders–recitation kombinasyonlarını tarayıp çakışmasız ve
en derli toplu programı bulur.

Tek dosyalık statik site — sunucu, veritabanı, build adımı yok.
`index.html` her şeyi içeriyor.

## Ne yapar

- Sabancı kataloğundaki **472 dersin tamamı** (Fall 2026-2027) içinde arama, ders havuzu oluşturma
- **Ön koşul** ve **kontenjan** bilgisi ders kartlarında görünür
- **Bölüm seçimi** — 12 bölüm ve 22 giriş dönemi için müfredat yüklenir; dersler
  `Zorunlu / Core / Area / Üniversite / Free` olarak etiketlenir
- Bu dönem seçtiklerinin **kategori dağılımı** (kaç zorunlu / core / area / üniversite /
  free) ve **toplam kredisi** en üstte özetlenir
- Aramada kategoriye göre süzme (ör. "bana uygun tüm area elective'ler")
- **Hoca kısıtı** — birden fazla hocayla açılan derslerde "bu dersi X'ten alayım"
  dersin; çözücü yalnız o hocanın section'larını dener
- **Kayıtlı planlar** — Plan A / Plan B diye kaydedip aralarında geçiş yaparsın;
  havuz, seçim, sabitlenen section'lar ve tercihler plana dahildir
- **Paylaşılabilir bağlantı** — planını tek tıkla linke çevirirsin; havuz, seçim,
  sabitlenen section'lar ve tercihler linkte taşınır. Telefonuna at, arkadaşına gönder.
  Site zaten açıkken gelen bir link tıklandığında tarayıcı sayfayı yeniden yüklemez,
  yalnız adresin `#` kısmı değişir; SUits bunu da dinler ve programı yükler
- **Duvar kâğıdı** — programını telefon duvar kâğıdı olarak indirirsin: gün gün
  kartlar (**Ajanda**) ya da haftalık **Tablo** biçimi; ders kodu, saat aralığı ve
  derslik; 8 yumuşak arka plan rengi, 3 telefon boyutu, saat ve bildirimler için
  üstte boşluk. Bölüm seçiliyse ders kategorisi (Zorunlu / Core / Area / Üniversite /
  Free) de yazılabilir
- **Tabloyu indir** — programın yatay A4 tablosu tek dosya olarak iner
  (2339 × 1654 piksel, 200 dpi PNG): beyaz zemin, gün sütunları, saat sütunu,
  renkli ders blokları (kod, saat aralığı, derslik, hoca), sağda ders + CRN
  listesi, altta tek satırda bütün CRN'ler. Sayfayı yazıcıya göndermez, görüntü
  üretir; WhatsApp'a atmak ya da duvara basmak için hazır. Manuel modda o anda
  elle kurduğun program çıkar. Ctrl+P ile yazdırmak isteyene sitenin kendi temiz
  çıktı sayfası da duruyor
- **Hoca adları** ders kartlarında ve tablo ipuçlarında görünür
- **Seviye filtresi** — 100 / 200 / 300 / 400 / 500+ ile 472 dersi hızla daraltırsın
- **Zaman tercihleri** — "10:40'tan önce ders olmasın", "17:30'dan sonra bitmesin",
  "Cuma boş kalsın" dersin; çözücü bunlara uyar
- İstediğin gün **boş kalamıyorsa sessizce yok sayılmaz**: gün kırmızıya döner ve
  nedeni yazar, altına da bunun yerine hangi günlerin boş yapılabileceğini listeler.
  Neden dört ayrı durumu ayırt eder: dersin her section'ında o gün var; sabitlediğin
  section o güne düşüyor; seçtiğin hoca yalnız o gün ders veriyor; ya da dersler tek
  tek olur ama birlikte yerleşmez
- Birden çok gün istediğinde **tutulabilenler tutulur**: "Pzt + Sal" birlikte olmuyorsa
  Pazartesi gerçekten boş kalır, yalnız Salı elenir ve ikisinin neden birlikte
  olmadığı yazılır
- **Saat aralığı** da aynı şekilde: aralığa hiç sığmayan dersler adıyla listelenir,
  geri kalan dersler aralıkta tutulur ve seçtiğin ders setinin tamamının sığdığı
  en dar aralık önerilir
- **Section değiştirme** — herhangi bir dersi A section'ından B'ye açılır menüden
  alırsın; sabitlediğin section korunur, geri kalanı yeniden çözülür
- Seçtiğin dersler için **bütün section kombinasyonlarını** dener; önce çakışmayı,
  sonra boş gün / ders arası boşluk / kampüste geçen süreyi optimize eder.
  Arama çakışma bütçesini sıfırdan başlatıp artırır, yani çakışmasız bir dizilim
  varsa yaprak sınırına takılmadan bulunur
- **Saati girilmemiş (TBA) section'lar** programa sokulmaz: aynı türde saati belli
  section varsa TBA olan elenir. Yoksa çözücü hiçbir saati doldurmadıkları için
  onları tercih ediyor, program olduğundan az saatli görünüyordu
- Recitation, discussion ve lab'ları dersin parçası sayar — ayrı ders olarak değil,
  ama programda ve çakışma hesabında gösterir
- Hangi ders çiftlerinin **hiçbir kombinasyonda** bir arada alınamadığını gösterir
- **Üç seviye: kesin / olsa iyi / belki** — havuz üç gruba ayrılır ve liste de öyle
  görünür. Her satırdaki üç bölmeli anahtarla istediğin seviyeye tek dokunuşta
  geçersin; sırayla tıklayıp döndürmek yok.
  *Kesin* dersler her programa girer, otomatik seçimden asla düşmez ve elle
  çıkarılamaz. *Olsa iyi* kesinin yumuşak hâlidir: aynı sayıda ders veren programlar
  arasında öne geçer, ama onu tutmak programı küçültecekse düşebilir. *Belki*
  dersleri yalnız yer kalırsa eklenir. Grup başlıkları o gruptan kaçının programa
  girdiğini yazar, sonuç satırında da programın kaç kesin + kaç olsa iyi + kaç belki
  dersinden oluştuğu görünür
- **Sıralama kuralı** — otomatik seçim şu sırayla karar verir: (1) kesin derslerin
  hepsi, (2) en çok ders, (3) eşit ders sayısında en çok "olsa iyi" dersi, (4) en
  yüksek kredi, (5) program kalitesi (boş gün, ders arası boşluk, kampüste geçen
  süre). Yani "olsa iyi" hiçbir zaman ders sayısından feragat ettirmez; bunu isteyen
  dersi kesin işaretler. Gerçek veriyle doğrulanmış örnek: ACC 301 hem ARA 510 hem
  BIO 635 ile çakışıyor. "Olsa iyi" iken program 4 derste kalır ve ACC 301 girmez;
  "kesin" iken ACC 301 girer ve program 3 derse iner
- **Çakışmanın çözüm yolları** — çakışmasız bir program kurulamıyorsa SUits yalnız
  "bir kısıtı gevşet" demiyor: olası tek hamleleri (bir dersi belki yapmak, bir
  hoca kısıtını kaldırmak, bir section kilidini açmak, saat/boş gün tercihlerini
  bırakmak) tek tek deneyip **yalnızca gerçekten işe yarayanları** düğme olarak
  sunar. Tıklayınca hamle uygulanır ve program çakışmasız hâle gelir. Tanının
  adım ve süre bütçesi var, hesap ekranı bekletmemek için çizimden sonra yapılır
- **Manuel mod** — üstteki *Otomatik / Manuel* anahtarıyla tek tıkta SUchedule tarzı
  tamamen elle çalışan bir ekrana geçersin. Soldaki listeden istediğin section'a
  tıklarsın, program anında güncellenir, çakışan section kırmızı görünür. Otomatik
  modda oluşan program manuel moda olduğu gibi taşınır
- **Section önizlemesi** — manuel modda bir section'ın üstüne fareyle geldiğinde
  "bunu seçersem programım ne olur" sorusunun cevabı tabloda beliriyor: o section
  kesik çerçeveli ve soluk olarak yerine oturur, geri kalan program söner, çakışma
  doğacaksa hücre kırmızıya döner ve başlıkta kaç saat çakışacağı yazar. Fare
  çekilince her şey eski hâline döner, seçim değişmez. Dokunmatikte kapalı
- **Manuel listede program hep ekranda** — section listesi 7000 piksele çıkıp sayfayı
  uzatıyor, aşağı indikçe program görüş alanından çıkıyordu. Liste artık kendi içinde
  kayıyor; sağdaki program yerinde duruyor. Sol panelin yapışma noktası da üst barın
  gerçek yüksekliğine göre hesaplanıyor, panelin üstü artık barın altında kalmıyor
- **Section kilidi** — herhangi bir section'ın yanındaki kilit simgesiyle onu
  sabitlersin ("bu dersi arkadaşımla X section'ından alacağım"); çözücü bir daha
  o section'ı değiştirmez
- **Hata ekranı** — kullanıcının ayarları birbiriyle çeliştiğinde program sessizce
  bozulmaz, üstte kırmızı bir kutu çıkar ve çözüm düğmesi sunar. Kilitlenen
  section'lar birbiriyle çakışıyorsa (hangi ikilinin çakıştığı adıyla yazılır) ve
  kesin ders sayısı ders sayısı tavanını (10) geçiyorsa bu kutu çıkar
- **Dört kavram, tek anlam** — havuz / mavi tik / seviye / sayı aralığı birbirine
  karışmasın diye hepsinin işi tek cümleyle yazılı (havuz listesinin başında ve
  rehberde): **havuz** aday derslerdir, **mavi tik** o dersin şu an programda
  olduğunu gösterir, **kesin / olsa iyi / belki** otomatik kurulumun önceliğidir,
  **ders sayısı aralığı** ise programın büyüklüğünü sınırlar. Tikin üstüne
  gelince "bu ders programda, tıkla çıkar" gibi bir ipucu da çıkar
- **Ders ve kredi aralığı** — "4 ile 6 ders, 12 ile 18 kredi" dersin.
  **Üst sınır sert ve her yerde aynı:** elle tikleme, kesin işaretleme, manuel mod
  ve çözücü aynı sınıra uyar. Eskiden manuel modda sınır hiç işlemiyordu (2 ders
  sınırıyla 6 ders seçilebiliyordu) ve kesin işaretleme sınırı sessizce aşıyordu.
  Kesin ders sayısı sınırı geçerse **sınır ona yükselir** ve bu yazılır; sınır
  tavandayken (10) hata ekranı devralır. **Alt sınır dilektir:** o kadar ders
  çakışmasız yerleşmiyorsa SUits boş dönmez, en iyi programı kurar ve "alt sınırın
  4 ders ama bu havuzdan en fazla 1 ders yerleşiyor" diye yazar. Eskiden bu
  durumda "havuzda çakışmasız hiçbir ikili bile yok" diyordu, oysa tek dersli
  program kurulabiliyordu. SU kredisi BannerWeb verisinden gelir
- **Hiçbir ders sessizce düşmüyor** — sınır bir işi engellediğinde ekranda sarı bir
  satır çıkar, nedenini yazar ve tek tıkla çözümü önerir ("Üst sınırı 4 yap",
  "Kredi sınırını 6 yap"). Sınırı küçültünce önce **belki** dersleri düşer, sonra
  **olsa iyi**; kesin ders asla düşmez, düşenler adıyla yazılır ve "sınırı 6 yapıp
  geri al" düğmesiyle geri gelir. Eskiden seçim listenin sonundan kesiliyordu ve
  kesin işaretlenmiş bir ders bile programdan sessizce çıkabiliyordu
- **Aynı kural her yoldan geçerli** — elle tik, kesin işaretleme, manuel mod, sınır
  değiştirme, kayıtlı plan, paylaşılan bağlantı ve eski `localStorage` kaydı: her
  çizimde iki değişmez kural zorlanıyor (kesin dersler programda, seçim üst sınırı
  aşmıyor), bozuk bir kayıt geldiğinde de düşen dersler yazılıyor
- Otomatik kurulum **tiklerde ne değiştiğini söyler**: "Tikler yenilendi · eklendi:
  ME 301, POLS 799 · çıkarıldı: LIT 540". Elle kurduğun programı bu düğmenin
  sessizce değiştirmesi, karışıklığın en büyük kaynağıydı
- Otomatik seçim aralığın içinde önce en çok dersi, aynı ders sayısında en yüksek
  krediyi hedefler; aralığa oturan çakışmasız kombinasyon yoksa bunu söyler
- Otomatik seçim, hangi derslerin alınacağını ve her dersin hangi section'ını
  kullanacağını **tek aramada birlikte** çözer ve yalnızca çakışmasız dizilim üretir.
  Hedef ders sayısı yüksekten başlayıp iner, her hedefin kendi süre dilimi vardır;
  8-10 derslik havuzlarda eski sürüm süreyi tek hedefte tüketip olduğundan küçük bir
  program öneriyordu
- Saat ve boş gün tercihi varsa önce tercihlere birebir uyan bir plan aranır; aynı
  ders sayısına ulaşabiliyorsa o kazanır. Ulaşamıyorsa ders sayısı tercihin önüne
  geçer ve fark uyarı olarak yazılır
- Bir program önerildiğinde havuzdan **hangi derslerin neden dışarıda kaldığı** yazılır
- Havuzdan ders çıkarmak tek tık: satırdaki × , aramada eklenmiş dersin üstüne
  tıklama, ya da başlıktaki **Temizle** ile hepsi birden
- Seçilen section'ların CRN'lerini tek tıkla kopyalar
- **Ferah havuz listesi** — ders satırı üç sessiz katman: kimlik (kod, kategori,
  section sayıları, kaldır), ad, ve ayrıntı (ön koşul, hoca menüsü, seviye anahtarı).
  Eskiden her ayrıntı ayrı bir rozetti; yan yana beş rozet satırı 104-155 piksele
  çıkarıyor ve listede aynı anda yalnız 3 ders görünüyordu. Şimdi satırlar 89-100
  piksel, aynı ekranda 5-8 ders görünüyor, hiçbir genişlikte taşma yok
- **Overload uyarısı** — programın toplam kredisi 20'yi geçerse sonuç satırında ve
  havuz sayacında sarı bir uyarı çıkar: bu program için overload onayı gerekebilir
- **Katlanabilir paneller** — her panelin başlığındaki ok düğmesiyle panel kapanır.
  Soldaki panel **yatay** kapanır: sütun 352 pikselden 44 piksele iner, başlık dikey
  durur ve kazanılan yer haftalık programa gider (program 816 pikselden 1124 piksele
  çıkıyor). Dar ekranda tek sütuna düşüldüğü için orada dikey kapanır. Üstteki plan ve
  tercih kutusu 135 pikselden 45'e iner. Aynısı manuel liste, haftalık program,
  alternatifler, section listesi ve çakışma matrisi için de geçerli. Hangi panelin
  kapalı olduğu `dk-fold` ile hatırlanır. Başlıktaki diğer düğmeler (Temizle,
  kilitleri aç) katlamayı tetiklemez. Düğme 28 × 28 piksel, çerçeveli ve yuvarlak
  köşeli bir kutu içinde SVG chevron: yönü hareketi gösteriyor (sağ panellerde
  açıkken yukarı, kapalıyken aşağı; sol panelde açıkken sola, kapalıyken sağa).
  Başlıktaki uzun ipucu metni artık düğmenin altına girmiyor (metin kısalıyor,
  düğmenin negatif kenar boşluğu kaldırıldı); üstteki kutuda ok için satırların
  sağında 48 piksel yer ayrıldı (eskiden `:first-child` düğmenin kendisine
  denk geldiği için o boşluk hiç uygulanmıyordu ve ok Paylaş / Duvar kâğıdı
  düğmelerinin üstüne biniyordu)
- **Arama motoru için** — sayfa başlığı, açıklama, canonical ve robots etiketleri;
  `WebApplication` JSON-LD yapısal verisi (Sabancı Üniversitesi varlığına bağlı);
  Open Graph ve Twitter etiketleri (`og.png` ile paylaşım önizlemesi); marka
  satırında ve footer'daki tanım metninde üniversite adı görünür metin olarak geçer.
  Gizli metin ya da anahtar kelime doldurma yok. Depoda ayrıca `sitemap.xml` ve
  `robots.txt` var
- **Mobil için ayrı görünüm** — telefonda haftalık tablo yerine gün gün ajanda
  listesi; havuz paneli katlanabilir
- **Dokunmatikte doğru geri bildirim** — fare imleciyle çalışan "havuzdaki dersin
  üstüne gel, kırmızı × ile çıkar" görünümü artık yalnız gerçek imleçte
  (`@media (hover: hover) and (pointer: fine)`). Telefonda `:hover` son dokunulan
  satırda takılı kaldığı için, eklenen ders kırmızı × gösteriyor, kullanıcı
  "eklenmedi" sanıp tekrar basınca dersi siliyordu. Aynı kural havuz satırındaki
  vurgu, "kesin yap" çerçevesi ve manuel moddaki section çerçevesi için de geçerli
- **Kullanım rehberi** — site ilk açıldığında 9 adımlık kısa ve görsel bir tanıtım
  çıkar: SUits'in ne yaptığı, havuz, kesin/olsa iyi/belki, ders-kredi aralığı, otomatik
  çözüm, tercihler, section kilidi, manuel mod ve paylaşma. Her adımın çizimi SVG
  olarak sayfanın içinde üretilir; dış dosya yoktur, `file://` ile de çalışır.
  Bir kez gösterilir (`dk-guide` kaydı), sonra üst bardaki **?** düğmesiyle her an
  yeniden açılır; ok tuşları, Esc ve nokta göstergesiyle gezinilir. TR ve EN
- **Sınırlar her yoldan doğrulanır** — ders/kredi aralığı seçim kutusundan, eski
  bağlantıdan, kayıtlı plandan ya da bozuk `localStorage` kaydından geçersiz gelemez;
  `normalizeRanges()` her çizimde değerleri geçerli aralığa çeker ve üst bardaki
  kutuları aynı değere getirir. Önceden boş bir seçim kutusu limiti 0 yapabiliyordu:
  üst barda "1" görünüyor, hedef "0-0 ders" oluyor ve hata ekranı kapanmıyordu
- **Çakışan bloklar üst üste binmiyor** — duvar kâğıdının **Tablo** biçiminde ve A4
  çıktısında aynı saatte iki section varsa, o sütun şeritlere bölünür ve her blok
  kendi şeridine oturur (`layoutDay()`, bağlı bileşen + şerit ataması). Çakışması
  olmayan blok tam genişlikte kalır. Eskiden ikisi aynı dikdörtgene çiziliyor ve
  yazılar okunmuyordu
- **Türkçe / İngilizce** dil seçeneği (üstteki TR·EN düğmesi, tarayıcı diline göre otomatik başlar)
- Açık/koyu tema, mobil uyumlu, çevrimdışı çalışır. Dosyayı indirip çift tıklayarak
  (`file://`) açtığında da her şey çalışır: veriler gömülü, rehberin çizimleri sayfanın
  içinde üretiliyor, konsola tek bir hata bile düşmüyor

## GitHub Pages ile yayınlama (ücretsiz, ~3 dakika)

1. [github.com](https://github.com) → **New repository**.
   İsim: `suits`, **Public**, **Create repository**.
2. Açılan sayfada **uploading an existing file** bağlantısına tıkla.
   `index.html` ve `README.md` dosyalarını sürükle bırak, **Commit changes**.
3. **Settings → Pages** → *Source*: `Deploy from a branch`,
   *Branch*: `main` + `/ (root)` → **Save**.
4. 1–2 dakika sonra site yayında:
   `https://KULLANICI-ADIN.github.io/suits/`

Sonradan bir şey değiştirmek istersen depodaki `index.html`'i aç, kalem simgesine
bas, düzenle, commit et — site kendiliğinden güncellenir.

### Alternatifler

| Yöntem | Nasıl | Notlar |
|---|---|---|
| **Netlify Drop** | [app.netlify.com/drop](https://app.netlify.com/drop) adresine klasörü sürükle | Hesap bile gerekmiyor, anında link |
| **Cloudflare Pages** | Depoyu bağla veya klasörü yükle | Hızlı CDN, ücretsiz |
| **Vercel** | Web arayüzünden yükle | Statik site olarak algılar |

### Kendi alan adın

Hepsi ücretsiz alt alan adı veriyor (`...github.io`, `...netlify.app`). Kendi alan
adını bağlamak istersen barındırma panelinde **Custom domain** bölümünden ekleyip
alan adı sağlayıcında bir CNAME kaydı oluşturman yeterli.

## Veri nereden geliyor

Sayfa açılır açılmaz **içine gömülü** kopyayla çalışmaya başlar — internet olmasa
da açılır. Arka planda sırayla şunları dener, ilk sağlam yanıtı kullanır:

1. **`data.json`** — sitenin yanındaki dosya (koyarsan öncelik onda)
2. **[bannerweb-fetch](https://omerrifat.github.io/bannerweb-fetch/)** — Sabancı'nın
   kendi BannerWeb sisteminden her gün otomatik çekilen veri. Ön koşul, kontenjan,
   ECTS, kredi ve hoca bilgisini de taşır
3. **[SUchedule](https://github.com/mustafacani/suchedule)** — yedek kaynak; dosya
   adındaki sürüm numarasını GitHub API ile kendi bulur
4. Hiçbiri olmazsa gömülü kopyada kalır

Başlıktaki rozet hangisinin kullanıldığını ve gömülü verinin tarihini gösterir;
tıklayınca yeniden dener. Gelen veri "makul mü" diye kontrol edilir — bozuk
gelirse yok sayılır. Başarılı sonuç 12 saat önbelleğe alınır.

Üç veri biçimini de tanır: gömülü sıkıştırılmış biçim, bannerweb-fetch dizisi ve
SUchedule'ın `{courses, instructors, places}` biçimi.

### Neden Sabancı'nın sitesine doğrudan bağlanmıyor

Tarayıcıdan mümkün değil: SUIS (Banner) yanıtlarında `Access-Control-Allow-Origin`
başlığı yok, JSON değil HTML döndürüyor ve `robots.txt` otomatik erişime kapalı.
Doğru çözüm veriyi sunucu tarafında çekmek — bannerweb-fetch tam olarak bunu yapıyor,
GitHub Actions ile her gün BannerWeb'i tarayıp JSON olarak yayınlıyor. SUits de o
yayını kullanıyor.

## Müfredat verisi

Bölüm seçimi [SUrriculum](https://beficent.github.io/surriculum/) projesinin
yayınladığı `courses/<giriş-dönemi>/<bölüm>.jsonl` dosyalarını kullanır. Bunlar
ders programında değil müfredatta bulunan bilgiyi taşır: her dersin o bölüm için
hangi kategoriye saydığı. Dosya ilk seçimde indirilir ve tarayıcıda 7 gün saklanır.

**En güncel giriş döneminin (202601) müfredatı sayfaya gömülüdür** — 12 bölümün
tamamı için, ~16 KB. Yani bölüm seçimi internet olmadan da, dosyayı doğrudan
tarayıcıda açtığında da çalışır. Farklı bir giriş dönemi seçersen SUits canlı
veriyi çeker; ulaşamazsa gömülü kopyaya döner ve bunu söyler.

Desteklenen bölümler: BIO, CS, DSA, ECON, EE, IE, MAN, MAT, ME, PSIR, PSY, VACD.

## Veriyi güncelleme

Gömülü kopyayı tazelemek için `index.html` içindeki `const RAW=` satırını yeni
veriyle değiştir. Ya da deponun köküne bir `data.json` koy — site onu gömülü
kopyaya tercih eder, `index.html`'e hiç dokunmana gerek kalmaz.

## Sınırlar

- Ders section'ı ile recitation/discussion grubunun **aynı harfte olması** kuralı
  yalnız `LETTER_SUBJECTS` listesindeki derslerde uygulanır (şu an SPS, ECON, FIN).
  Kural her derste geçerli değil: IF 100'ün 3 ders section'ı varken recitation
  harfleri A'dan N'ye gidiyor, NS 101'in A-H section'larının yalnız A-D recitation'ı
  var. Listeye ders eklense bile veri iki yönlü tutarlı değilse kural o derste
  kendiliğinden devre dışı kalır.
- Ön koşul listesi kaynakta "şunlardan biri" anlamında tutuluyor (EE 303 →
  EE 202 **veya** EL 202). SUits de öyle yorumluyor; kesin durumu SUIS'ten teyit et.
- Kayıt öncesi CRN'leri SUIS'ten teyit et.
- Ön koşullar BannerWeb'den geldiği gibi aktarılıyor; eş koşul (corequisite) alanı
  kaynakta tutarsız olduğu için kullanılmıyor.

## Lisans

Bu proje **AGPL-3.0** lisanslıdır — bkz. [LICENSE](LICENSE).

Ders verisi [bannerweb-fetch](https://github.com/omerrifat/bannerweb-fetch)
projesinden geliyor; o proje AGPL-3.0 lisanslı ve sahibi verinin bu koşulla
kullanılmasını istedi. SUits de aynı lisansı benimsiyor: kaynak kodu herkese açık,
projeyi alıp değiştiren de kaynağını açık tutmak zorunda.

Müfredat verisi [SUrriculum](https://github.com/beficent/surriculum) (GPL-3.0),
yedek ders verisi SUchedule (MIT, © Adnan Burak Ayaz) —
[özgün depo](https://github.com/aburakayaz/suchedule), verinin güncel tutulduğu
[çatal](https://github.com/mustafacani/suchedule). AGPL-3.0, GPL-3.0 ile uyumludur.

## Teşekkür

[omerrifat/bannerweb-fetch](https://github.com/omerrifat/bannerweb-fetch),
[beficent/surriculum](https://github.com/beficent/surriculum),
[aburakayaz/suchedule](https://github.com/aburakayaz/suchedule) (SUchedule'ın
özgün hâli) ve [mustafacani/suchedule](https://github.com/mustafacani/suchedule)
(veriyi güncel tutan çatal) — bu araç onların topladığı veri olmadan çalışmazdı.
