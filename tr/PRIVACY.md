# Gizlilik ilkesi — BabiBo

BabiBo, Le Phuong Trung tarafından geliştirilir.

_Son güncelleme: 18 Kasım 2026_

BabiBo, iPhone için kişisel finans uygulamasıdır. iPad uygulaması değildir.
Yayımlayan kişiler, defterinizi alan bir hizmet işletmez. BabiBo hesabı yoktur,
çözümleme yoktur, çökme raporu yoktur, reklam tanımlayıcısı yoktur ve kendiliğinden
veri gönderen bir üçüncü taraf SDK'sı yoktur.

Bazı özellikler veriyi cihazdan çıkarır: sizin seçtiğiniz bir şirkete ya da
özelliğin ulaşması gereken bir siteye. Bu sayfa neyin çıktığını, nasıl, neden,
kimin aldığını (yapay zeka sağlayıcısı dahil), ne kadar süre tutulduğunu ve
nasıl durduracağınızı ya da sileceğinizi söyler.

## Cihazda kalan

Defterin bildiği her şey — hesaplar, bakiyeler, işlemler, kategoriler,
bütçeler, varlıklar, fiş fotoğrafları ve bir fişten öğrenilmiş adlar —
uygulamanın kendi kabındaki bir veritabanı dosyasında, cihazınızda durur.

Bu dosya, cihaz yedeğine girer. iCloud Backup açıksa, şifreli bir kopya
telefonun geri kalanıyla birlikte gider. Bu kopya sizinle Apple arasındadır.
Biz okuyamayız.

Dosyayı istediğiniz zaman **Ayarlar → Veriler** bölümünden dışa aktarabilir ve
başka bir cihazdaki BabiBo'ya içe aktarabilirsiniz. Geri yüklenen kopya banka
oturumunu taşımaz: imza anahtarı onu oluşturan telefonda kalır ve bankayı yeni
telefonda yeniden bağlarsınız.

Uygulamayı silmek bu dosyayı siler. Buna kayıtlı bir Gemini API anahtarı,
öğrenilmiş ürün adları, kayıtlı fiyatlar ve önbellekteki logolar dahildir.

Bu veriyi reklam ya da izleme için kullanmayız ve bir kopyasını hiç almayız.

## Bankanız, Enable Banking üzerinden

İsteğe bağlıdır; iPhone, Mac ve sizin barındırdığınız bir sunucuda. Enable
Banking'e kendi uygulamanızı kaydedip bir banka bağlamadan hiçbir şey
gönderilmez.

**Ne.** Bakiyeler, ekstreler (işlemler) ve bankanın döndürdüğü hesap
tanımlayıcıları; banka gönderirse bir IBAN dahil.

**Nasıl.** Uygulama Enable Banking'e sorar, Enable Banking bankanıza sorar ve
yanıtı yerel dosyaya yazar. Uygulama kimliği ve özel anahtar cihazınızda
kalır. iPhone'da bir banka bağlandıktan sonra uygulama, iOS'tan sabah
uyandırılmasını ister — 07:15'i hedefler ve son altı saatte bir eşitleme
başardıysa çekmeyi atlar — sonra ekstreleri yeniden indirir. iOS bu saati yok
sayabilir. Çekme yalnızca BabiBo için Background App Refresh açıkken çalışır.

**Neden.** Defteri doldurmak için. Bildirimlere izin verdiyseniz, yeni işlemler
geldiğinde telefon bir özet de yayınlar. Bu bildirim cihazda oluşturulur. Bize
gönderilmez.

**Kim.** Enable Banking ve bankanız. Biz değil. Veriyle ne yaptıkları, kendi
koşullarına ve kayıt olurken ile bankayı onaylarken verdiğiniz onaya uyar.

**Ne kadar, ve nasıl durdurulur.** Uygulamadaki kopya, hesabı silene kadar
kalır. Bir hesabı silmek işlemlerini siler ve bu, o bağlantıdaki son hesapsa
bağlantıyı da siler; böylece sabah çekmesinin soracağı bir şey kalmaz. Enable
Banking ve banka, kendi koşullarının gerektirdiğini tutar. Onların kopyasını
silemeyiz. Onayı bankanızda ya da kaydettiğiniz Enable Banking uygulamasında
geri alın.

## Google Gemini

İsteğe bağlıdır ve yalnızca iPhone'dadır. **Ayarlar → Kasa fişleri** altına bir
anahtar kaydedene kadar istek yapılmaz.

**Ne.** Fişte basılı kısaltılmış ürün adları ve satıcının adı. Fotoğraf değil,
tutarlar değil, tarihler değil ve defterin geri kalanı değil. Bir sonraki istek,
telefonda duran kategori sözcüklerini gönderebilir — satıcı, tutar ya da tarih
olmadan « tavuk » gibi sözcükler — sabit bir ürün ailesi listesine
yerleştirilmeleri için.

**Nasıl.** [Google AI Studio](https://aistudio.google.com) adresinde bir anahtar
oluşturur ve Ayarlar'a kaydedersiniz. Uygulama ardından Google'ın Gemini
API'sini (`generativelanguage.googleapis.com`) bu anahtarla çağırır. Bir kez
yanıtlanmış bir etiket telefonda kalır ve yeniden gönderilmez.

**Neden.** Bir kasa kısaltmasını bir ürün adına ve bir kategoriye çevirmek için;
bunlar yerel dosyaya geri yazılır.

**Kim.** Oluşturduğunuz anahtara uygulanan Gemini API koşulları altında Google.
Metni biz almayız. Bu özelliğin yapay zeka sağlayıcısı Google'dır.

**Ne kadar, ve nasıl durdurulur.** Google, bu koşulların söylediğini tutar. Bu
süreyi biz belirlemeyiz ve kendi sunucumuzda bir kopyamız yoktur. Okuma, siz
uygulamayı silene kadar yerel veritabanında kalır. **Ayarlar → Kasa fişleri →
Retirer** anahtarı telefondan siler ve sonraki istekleri durdurur. Düğmenin
etiketi Retirer'dir. Telefonda duran okumaları silmez ve Google'ın aldığı şeyi
silmez. Google'ın anahtarı kabul etmesini durdurmak istiyorsanız anahtarı
Google AI Studio'da da silin ya da yenileyin.

## Yahoo Finance

**Ne.** `CW8.PA` gibi bir sembol. Bir menkul aradığınızda, yazdığınız metin.
Miktar değil, değer değil ve hesap adı değil.

**Nasıl.**

- iPhone'da defteri yenilemek, sembolü olan her varlık için Yahoo'dan bir fiyat
  ister. Bir sembolü kaydetmek hemen sorar. Arama alanı, aradığınızda sorar.
  Uygulama bunu sabahki arka plan çekmesinde yapmaz.
- Mac'te ve sizin barındırdığınız bir sunucuda Yahoo, fiyat sağlayıcısını
  Yahoo yaptığınızda kullanılır. Varsayılan kapalıdır ve bu sürümler o zaman
  fiyat isteği yapmaz.

İstek `query1.finance.yahoo.com` adresine gider. API anahtarı yoktur. Bağlantı,
her HTTPS isteği gibi ağ adresini ve bir user agent taşır. Uygulama ad ya da
hesap kimliği eklemez.

**Neden.** Bir fiyat göstermek ve iPhone'da yazdığınıza uyan kaydı bulmak için.

**Kim.** Yahoo. Biz değil.

**Ne kadar, ve nasıl durdurulur.** Fiyatlar yerel dosyaya yazılır ve siz
uygulamayı silene kadar kalır. Yahoo kendi kayıtlarını kendi gizlilik ilkesine
göre tutar. Bunları silebileceğimiz bir Yahoo hesabımız yoktur. iPhone'da o
varlık için sonraki fiyat isteklerini durdurmak üzere varlığı silin ve metnin
gönderilmesini istemiyorsanız arama yapmayın. Mac'te ve sunucunuzda fiyat
sağlayıcısını yeniden `none` yapın.

## Satıcı siteleri

Yalnızca iPhone. Varsayılan olarak açık.

**Ne.** Defterden hiçbir alan isteğe eklenmez. Uygulama `https://` ile
satıcının alan adını yükler, sonra o sayfanın adlandırdığı simgeyi yükler.
İstek, o adresi isteyen bir tarayıcıya benzer: adresin kendisi, telefonun ağ
adresi ve bir tarayıcı user agent. Çerezler ne saklanır ne gönderilir.

**Nasıl.** **Ayarlar → Kategoriler ve satıcılar → Satıcı logoları** açıkken ve
satıcının bilinen bir sitesi ya da sizin yazdığınız bir sitesi varken. Görüntü,
ilk gerektiğinde istenir.

**Neden.** O satıcının simgesini çizmek için. Başka bir şey için değil.

**Kim.** O satıcının sitesi ve onu barındıran. Bir logo hizmeti değil, ve biz
değil.

**Ne kadar, ve nasıl durdurulur.** Görüntü, iOS önbellekleri temizleyene ya da
siz uygulamayı silene kadar uygulamanın önbelleğinde durur. Kullanılabilir bir
simgesi olmayan bir site yedi gün boyunca yeniden sorulmaz. Sitenin kayıtları
sitenindir; biz silemeyiz. Yeni istekleri durdurmak için **Satıcı logoları**
seçeneğini kapatın.

## Kendi sunucunuz

İsteğe bağlıdır. BabiBo'yu işlettiğiniz bir sunucuya yöneltirseniz, uygulama
defteri orada okur ve yazar. O makine sizindir. Durdurmak için Ayarlar'daki
sunucu adresini kaldırın. Sunucunun o makinede sakladığını silin.

## Face ID

Uygulama kilidini açarsanız, BabiBo iOS'tan sizi doğrulamasını ister. iOS evet
ya da hayır der. Biyometriniz uygulamaya hiç ulaşmaz ve kimseye gönderilmez.

## Çocuklar

BabiBo çocuklara yönelik değildir.

## Değişiklikler

Bu ilkedeki her değişiklik
<https://github.com/LePhuongTrung/babobi-PRIVACY> adresine işlenir; geçmişi
açıktır.

Bu sayfa Türkçedir. Aynı ilkenin İngilizcesi kökteki PRIVACY.md dosyasıdır.
Uygulamanın diğer dilleri, dil kodunu taşıyan bir klasördedir.

## İletişim

Silecek bir BabiBo hesabı yoktur, çünkü biz hesap tutmayız. Uygulamayı silmek
yerel dosyayı siler. Bir alıcının elinde olan veri için, yukarıda o alıcının
bölümündeki yolu kullanın.

Sorular: <babibo.support@lephuongtrung.id.vn>
