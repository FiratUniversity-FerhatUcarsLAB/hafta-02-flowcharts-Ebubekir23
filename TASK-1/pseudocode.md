Öğrenci Ad-Soyad: Ebubekir Yılmaz
Öğrenci No: 250541051
## ATM PARA ÇEKME SİSTEMİ PSEUDOCODE

BAŞLA  
&nbsp;&nbsp;OKU PIN  
&nbsp;&nbsp;pin_hak = 3  

&nbsp;&nbsp;DÖNGÜ pin_hak > 0 İKEN  
&nbsp;&nbsp;&nbsp;&nbsp;EĞER PIN doğru İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "PIN doğrulandı."  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OKU bakiye  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;günlük_limit = 5000  

&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DÖNGÜ (işlem_tekrar = "E")  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OKU çekilecek_tutar  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EĞER çekilecek_tutar % 20 ≠ 0 İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Tutar 20 TL'nin katı olmalıdır."  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EĞER çekilecek_tutar > bakiye İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Yetersiz bakiye."  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EĞER çekilecek_tutar > günlük_limit İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Günlük limit aşıldı."  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;bakiye = bakiye - çekilecek_tutar  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;günlük_limit = günlük_limit - çekilecek_tutar  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "İşlem başarılı. Yeni bakiye:", bakiye  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Yeni işlem yapmak ister misiniz? (E/H)"  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;OKU işlem_tekrar  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BİTİR DÖNGÜ  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "İşlemler tamamlandı, iyi günler."  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ÇIK  
&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;pin_hak = pin_hak - 1  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;EĞER pin_hak > 0 İSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "Yanlış PIN. Kalan hakkınız:", pin_hak  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;DEĞİLSE  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;YAZ "3 kez hatalı giriş. Kart bloke edildi."  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;ÇIK  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;&nbsp;&nbsp;BİTİR EĞER  
&nbsp;&nbsp;BİTİR DÖNGÜ  

BİTİR
