# SUits

Sabancı Üniversitesi ders programı planlayıcısı. Aday derslerini seçersin,
SUits tüm ders–recitation kombinasyonlarını tarayıp çakışmasız ve en derli toplu
programı bulur.

Tek dosyalık statik site — sunucu, veritabanı, build adımı yok.
`index.html` her şeyi içeriyor.

## Ne yapar

- Sabancı kataloğundaki **471 dersin tamamı** içinde arama, aday havuzu oluşturma
- Seçtiğin dersler için **bütün section kombinasyonlarını** dener; önce çakışmayı,
  sonra boş gün / ders arası boşluk / kampüste geçen süreyi optimize eder
- Ders section'ı harfliyse (A, B) recitation grubunun da aynı harfle başlaması
  kuralına uyar
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
2. **SUchedule deposu** — güncel `data-vXX.min.json`. Dosya adındaki sürüm
   numarasını GitHub API ile kendi bulur, elle güncelleme gerekmez
3. Hiçbiri olmazsa gömülü kopyada kalır

Başlıktaki rozet hangisinin kullanıldığını ve gömülü verinin tarihini gösterir;
tıklayınca yeniden dener. Gelen veri "makul mü" diye kontrol edilir — bozuk
gelirse yok sayılır. Başarılı sonuç 12 saat önbelleğe alınır.

İki veri biçimini de tanır: gömülü sıkıştırılmış biçim ve SUchedule'ın ham
`{courses, instructors, places}` biçimi.

### Neden Sabancı'nın kendi sitesinden çekilmiyor

Denendi, tarayıcıdan mümkün değil. Ders programı SUIS (Banner) üzerinde ve
yanıtlarında `Access-Control-Allow-Origin` başlığı yok — başka bir alan adındaki
sayfanın oradan veri çekmesini tarayıcı engelliyor; sitenin nerede barındığı bunu
değiştirmiyor. Ayrıca JSON değil, form gönderimiyle üretilen HTML döndürüyor ve
`robots.txt` otomatik erişime kapalı.

Bu yüzden zincir SUchedule verisine dayanıyor ve **her koşulda gömülü kopyaya
düşüyor** — yani site hiçbir durumda boş açılmıyor.

## Veriyi güncelleme

Gömülü kopyayı tazelemek için `index.html` içindeki `const RAW=` satırını yeni
veriyle değiştir. Ya da deponun köküne bir `data.json` koy — site onu gömülü
kopyaya tercih eder, `index.html`'e hiç dokunmana gerek kalmaz.

## Sınırlar

- Ön koşul (prerequisite) bilgisi bu veride yok.
- Kontenjan/doluluk bilgisi yok — sadece saat çakışması hesaplanıyor.
- Veri SUchedule'ın topladığı kataloğa dayanıyor; kayıt öncesi CRN'leri
  SUIS'ten teyit et.

## Teşekkür

Ders verisi [SUchedule](https://github.com/mustafacani/suchedule) projesinden
geliyor.
