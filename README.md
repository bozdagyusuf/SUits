# SUits

[![License: AGPL v3](https://img.shields.io/badge/License-AGPL_v3-blue.svg)](LICENSE)

Sabancı Üniversitesi ders programı planlayıcısı. Aday derslerini seçersin,
SUits tüm ders–recitation kombinasyonlarını tarayıp çakışmasız ve en derli toplu
programı bulur.

Tek dosyalık statik site — sunucu, veritabanı, build adımı yok.
`index.html` her şeyi içeriyor.

## Ne yapar

- Sabancı kataloğundaki **472 dersin tamamı** (Fall 2026-2027) içinde arama, aday havuzu oluşturma
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
  sabitlenen section'lar ve tercihler linkte taşınır. Telefonuna at, arkadaşına gönder
- **Duvar kâğıdı** — programını telefon duvar kâğıdı olarak indirirsin: gün gün
  kartlar (**Ajanda**) ya da haftalık **Tablo** biçimi; ders kodu, saat aralığı ve
  derslik; 8 yumuşak arka plan rengi, 3 telefon boyutu, saat ve bildirimler için
  üstte boşluk. Bölüm seçiliyse ders kategorisi (Zorunlu / Core / Area / Üniversite /
  Free) de yazılabilir
- **Yazdır** — sitenin kendi hazırladığı temiz bir çıktı sayfası: haftalık tablo,
  ders/CRN/saat/derslik/hoca listesi ve kopyalanabilir CRN satırı
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
- **Ders ve kredi aralığı** — "4 ile 6 ders, 12 ile 18 kredi" dersin. Maksimumlar
  sert sınır (üstüne çıkacak seçim engellenir), minimumlar otomatik seçimin hedefi.
  SU kredisi BannerWeb verisinden gelir, bölüm seçmene gerek yok
- Otomatik seçim aralığın içinde önce en çok dersi, aynı ders sayısında en yüksek
  krediyi hedefler; aralığa oturan çakışmasız kombinasyon yoksa bunu söyler
- Havuzdan ders çıkarmak tek tık: satırdaki × , aramada eklenmiş dersin üstüne
  tıklama, ya da başlıktaki **Temizle** ile hepsi birden
- Seçilen section'ların CRN'lerini tek tıkla kopyalar
- **Mobil için ayrı görünüm** — telefonda haftalık tablo yerine gün gün ajanda
  listesi; havuz paneli katlanabilir
- **Türkçe / İngilizce** dil seçeneği (üstteki TR·EN düğmesi, tarayıcı diline göre otomatik başlar)
- Açık/koyu tema, mobil uyumlu, çevrimdışı çalışır

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
yedek ders verisi [SUchedule](https://github.com/mustafacani/suchedule) (MIT).
AGPL-3.0, GPL-3.0 ile uyumludur.

## Teşekkür

[omerrifat/bannerweb-fetch](https://github.com/omerrifat/bannerweb-fetch),
[beficent/surriculum](https://github.com/beficent/surriculum) ve
[mustafacani/suchedule](https://github.com/mustafacani/suchedule) — bu araç
onların topladığı veri olmadan çalışmazdı.
