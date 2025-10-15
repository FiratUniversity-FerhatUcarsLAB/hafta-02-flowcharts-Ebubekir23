Öğrenci Ad-Soyad: Ebubekir Yılmaz
Öğrenci No:250541051
## E-TİCARET SEPET VE ÖDEME SİSTEMİ PSEUDOCODE

BAŞLA  
&nbsp;&nbsp;sepet = boş  
&nbsp;&nbsp;toplam = 0  
&nbsp;&nbsp;indirim = 0  
&nbsp;&nbsp;kargo = 0  

&nbsp;&nbsp;YAZ "Giriş yap veya misafir olarak devam et?"  
&nbsp;&nbsp;OKU kullanıcı_durumu  
&nbsp;&nbsp;EĞER kullanıcı_durumu = "giriş" İSE  
&nbsp;&nbsp;&nbsp;&nbsp;OKU kullanıcı_adı, şifre  
&nbsp;&nbsp;&nbsp;&nbsp;EĞER doğrulama başarılı İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Giriş başarılı."  
&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Giriş başarısız, misafir olarak devam ediliyor."  
&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;BİTİR EĞER  

&nbsp;&nbsp;DÖNGÜ (true)  
&nbsp;&nbsp;&nbsp;&nbsp;OKU ürün_id  
&nbsp;&nbsp;&nbsp;&nbsp;EĞER ürün_id = 0 İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ÇIK DÖNGÜ  
&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OKU adet  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EĞER stok_yeterli(ürün_id, adet) İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;sepete_ekle(ürün_id, adet)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Ürün sepete eklendi."  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Yetersiz stok."  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;BİTİR DÖNGÜ  

&nbsp;&nbsp;YAZ "Sepetiniz:"  
&nbsp;&nbsp;GÖSTER sepet  

&nbsp;&nbsp;YAZ "İndirim kodu var mı? (E/H)"  
&nbsp;&nbsp;OKU cevap  
&nbsp;&nbsp;EĞER cevap = "E" İSE  
&nbsp;&nbsp;&nbsp;&nbsp;OKU kod  
&nbsp;&nbsp;&nbsp;&nbsp;EĞER kod_geçerli(kod) İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;indirim = uygula_indirim(kod)  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "İndirim uygulandı."  
&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Kod geçersiz veya süresi dolmuş."  
&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;BİTİR EĞER  

&nbsp;&nbsp;OKU adres  
&nbsp;&nbsp;kargo = hesapla_kargo(toplam)  
&nbsp;&nbsp;EĞER toplam ≥ 1000 İSE  
&nbsp;&nbsp;&nbsp;&nbsp;kargo = 0  
&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Ücretsiz kargo uygulandı."  
&nbsp;&nbsp;BİTİR EĞER  

&nbsp;&nbsp;toplam = ürün_toplam - indirim + kargo  
&nbsp;&nbsp;YAZ "Sepet toplamı:", toplam  

&nbsp;&nbsp;YAZ "Ödeme yöntemi seç (KART/HAVALE/KAPIDA)"  
&nbsp;&nbsp;OKU odeme_tipi  

&nbsp;&nbsp;EĞER odeme_tipi = "KART" İSE  
&nbsp;&nbsp;&nbsp;&nbsp;OKU kart_bilgileri  
&nbsp;&nbsp;&nbsp;&nbsp;EĞER kart_geçerli(kart_bilgileri) İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Ödeme başarılı."  
&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Kart hatası, ödeme başarısız."  
&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;DEĞİLSE EĞER odeme_tipi = "HAVALE" İSE  
&nbsp;&nbsp;&nbsp;&nbsp;YAZ "IBAN bilgisi gönderildi."  
&nbsp;&nbsp;DEĞİLSE EĞER odeme_tipi = "KAPIDA" İSE  
&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Kapıda ödeme seçildi."  
&nbsp;&nbsp;BİTİR EĞER  

&nbsp;&nbsp;EĞER ödeme başarılı İSE  
&nbsp;&nbsp;&nbsp;&nbsp;sipariş_olustur()  
&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Sipariş başarıyla oluşturuldu."  
&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Sipariş başarısız oldu."  
&nbsp;&nbsp;BİTİR EĞER  

&nbsp;&nbsp;YAZ "Yeni alışveriş yapmak ister misiniz? (E/H)"  
&nbsp;&nbsp;OKU yanit  
&nbsp;&nbsp;EĞER yanit = "E" İSE  
&nbsp;&nbsp;&nbsp;&nbsp;TEKRAR başa dön  
&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Ziyaretiniz için teşekkürler."  
&nbsp;&nbsp;&nbsp;&nbsp;ÇIK  
&nbsp;&nbsp;BİTİR EĞER  

BİTİR
