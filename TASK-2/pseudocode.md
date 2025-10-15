Öğrenci Ad-Soyad: Ebubekir Yılmaz
Öğrenci No: 250541051
BAŞLA
sepet = boş
toplam = 0
indirim = 0
kargo = 0

YAZ "Giriş yap veya misafir olarak devam et?"
OKU kullanıcı_durumu
EĞER kullanıcı_durumu = "giriş" İSE
 OKU kullanıcı_adı, şifre
 EĞER doğrulama başarılı İSE
  YAZ "Giriş başarılı."
 DEĞİLSE
  YAZ "Giriş başarısız, misafir olarak devam ediliyor."
 BİTİR EĞER
BİTİR EĞER

DÖNGÜ (true)
 OKU ürün_id
 EĞER ürün_id = 0 İSE
  ÇIK DÖNGÜ
 DEĞİLSE
  OKU adet
  EĞER stok_yeterli(ürün_id, adet) İSE
   sepete_ekle(ürün_id, adet)
   YAZ "Ürün sepete eklendi."
  DEĞİLSE
   YAZ "Yetersiz stok."
  BİTİR EĞER
 BİTİR EĞER
BİTİR DÖNGÜ

YAZ "Sepetiniz:"
GÖSTER sepet

YAZ "İndirim kodu var mı? (E/H)"
OKU cevap
EĞER cevap = "E" İSE
 OKU kod
 EĞER kod_geçerli(kod) İSE
  indirim = uygula_indirim(kod)
  YAZ "İndirim uygulandı."
 DEĞİLSE
  YAZ "Kod geçersiz veya süresi dolmuş."
 BİTİR EĞER
BİTİR EĞER

OKU adres
kargo = hesapla_kargo(toplam)
EĞER toplam ≥ 1000 İSE
 kargo = 0
 YAZ "Ücretsiz kargo uygulandı."
BİTİR EĞER

toplam = ürün_toplam - indirim + kargo
YAZ "Sepet toplamı:", toplam

YAZ "Ödeme yöntemi seç (KART/HAVALE/KAPIDA)"
OKU odeme_tipi

EĞER odeme_tipi = "KART" İSE
 OKU kart_bilgileri
 EĞER kart_geçerli(kart_bilgileri) İSE
  YAZ "Ödeme başarılı."
 DEĞİLSE
  YAZ "Kart hatası, ödeme başarısız."
 BİTİR EĞER
DEĞİLSE EĞER odeme_tipi = "HAVALE" İSE
 YAZ "IBAN bilgisi gönderildi."
DEĞİLSE EĞER odeme_tipi = "KAPIDA" İSE
 YAZ "Kapıda ödeme seçildi."
BİTİR EĞER

EĞER ödeme başarılı İSE
 sipariş_olustur()
 YAZ "Sipariş başarıyla oluşturuldu."
DEĞİLSE
 YAZ "Sipariş başarısız oldu."
BİTİR EĞER

YAZ "Yeni alışveriş yapmak ister misiniz? (E/H)"
OKU yanit
EĞER yanit = "E" İSE
 TEKRAR başa dön
DEĞİLSE
 YAZ "Ziyaretiniz için teşekkürler."
 ÇIK
BİTİR EĞER

BİTİR
