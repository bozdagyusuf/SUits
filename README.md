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
- Seçtiğin dersler için **bütün section kombinasyonlarını** dener; önce çakışmayı,
  sonra boş gün / ders arası boşluk / kampüste geçen süreyi optimize eder
- Recitation, discussion ve lab'ları dersin parçası sayar — ayrı ders olarak değil,
  ama programda ve çakışma hesabında gösterir
- Hangi ders çiftlerinin **hiçbir kombinasyonda** bir arada alınamadığını gösterir
- Ders limitine göre en iyi kombinasyonu otomatik bulur; o sayıda çakışmasız
  program yoksa ulaşılabilir en büyük sayıya iner
- Seçilen section'ların CRN'lerini tek tıkla kopyalar
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

## Veriyi güncelleme

Gömülü kopyayı tazelemek için `index.html` içindeki `const RAW=` satırını yeni
veriyle değiştir. Ya da deponun köküne bir `data.json` koy — site onu gömülü
kopyaya tercih eder, `index.html`'e hiç dokunmana gerek kalmaz.

## Sınırlar

- Ders section'ı ile recitation grubunun aynı harfle eşleşmesi kuralı
  (A dersi → A recitation) şu an **kapalı** — her derste geçerli olmadığı için.
  `index.html` içindeki `ENFORCE_GROUP_LETTERS` değerini `true` yapmak geri açar.
- Ön koşul (prerequisite) bilgisi bu veride yok.
- Kontenjan/doluluk bilgisi yok — sadece saat çakışması hesaplanıyor.
- Kayıt öncesi CRN'leri SUIS'ten teyit et.
- Ön koşullar BannerWeb'den geldiği gibi aktarılıyor; eş koşul (corequisite) alanı
  kaynakta tutarsız olduğu için kullanılmıyor.

## Lisans

Bu proje **AGPL-3.0** lisanslıdır — bkz. [LICENSE](LICENSE).

Ders verisi [bannerweb-fetch](https://github.com/omerrifat/bannerweb-fetch)
projesinden geliyor; o proje AGPL-3.0 lisanslı ve sahibi verinin bu koşulla
kullanılmasını istedi. SUits de aynı lisansı benimsiyor: kaynak kodu herkese açık,
projeyi alıp değiştiren de kaynağını açık tutmak zorunda.

Yedek veri kaynağı [SUchedule](https://github.com/mustafacani/suchedule) (MIT).

## Teşekkür

[omerrifat/bannerweb-fetch](https://github.com/omerrifat/bannerweb-fetch) ve
[mustafacani/suchedule](https://github.com/mustafacani/suchedule) — bu araç
onların topladığı veri olmadan çalışmazdı.
