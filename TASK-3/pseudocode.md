Öğrenci Ad-Soyad: Ebubekir Yılmaz
Öğrenci No: 250541051

### **HASTANE RANDEVU SİSTEMİ PSEUDOCODE**

```
BAŞLA
  OKU KullaniciID, Sifre
  pin_hak = 3
  
  DÖNGÜ pin_hak > 0 İKEN
    EĞER KULLANICI_KIMLIK_DOGRULA(KullaniciID, Sifre) DOĞRU İSE
      YAZ "Kimlik doğrulandı. Sisteme hoş geldiniz."
      YAZ "1- Randevu Al"
      YAZ "2- Tahlil Sonuçları"
      OKU secim

      EĞER secim == 1 İSE
        OKU SecilenPoliklinik
        OKU SecilenDoktor
        OKU SecilenSaat

        EĞER RANDEVU_ONAYLANABILIR İSE
          RANDEVU_VERITABANINA_KAYDET()
          SMS_GONDER()
          YAZ "Randevunuz başarıyla oluşturuldu."
        DEĞİLSE
          YAZ "Randevu oluşturulamadı. Lütfen tekrar deneyin."
        BİTİR EĞER
      DEĞİLSE EĞER secim == 2 İSE
        EĞER TAHLIL_BULUNUYOR İSE
          EĞER TAHLIL_SONUCU_HAZIR İSE
            YAZ "Tahlil sonuçlarınız görüntülendi."
            YAZ "PDF indirmek ister misiniz? (E/H)"
            OKU pdf_secim
            EĞER pdf_secim == "E" İSE
              PDF_OLUSTUR_VE_INDIR()
              YAZ "PDF indiriliyor..."
            BİTİR EĞER
          DEĞİLSE
            YAZ "Tahlil sonuçlarınız henüz hazır değil."
          BİTİR EĞER
        DEĞİLSE
          YAZ "Adınıza kayıtlı tahlil bulunamadı."
        BİTİR EĞER
      BİTİR EĞER
      
      YAZ "İşlemler tamamlandı, iyi günler."
      ÇIK
    DEĞİLSE
      pin_hak = pin_hak - 1
      EĞER pin_hak > 0 İSE
        YAZ "Yanlış kullanıcı adı veya şifre. Kalan hakkınız:", pin_hak
      DEĞİLSE
        YAZ "3 kez hatalı giriş. Hesabınız bloke edildi."
        ÇIK
      BİTİR EĞER
    BİTİR EĞER
  BİTİR DÖNGÜ

BİTİR
