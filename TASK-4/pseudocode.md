Öğrenci Ad-Soyad: Ebubekir Yılmaz
Öğrenci No: 250541051
Elbette, istediğiniz formatta **Hastane Randevu Sistemi** ve **Üniversite Ders Kayıt Sistemi** için sözde kodları (pseudocode) yeniden düzenledim. Bu format, girintilerle kodun akışını ve mantığını daha net gösterir.

-----

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
```

-----

### **ÜNİVERSİTE DERS KAYIT SİSTEMİ PSEUDOCODE**

```
BAŞLA
  OKU OgrenciID, Sifre
  giris_hak = 3

  DÖNGÜ giris_hak > 0 İKEN
    EĞER KULLANICI_KIMLIK_DOGRULA(OgrenciID, Sifre) DOĞRU İSE
      YAZ "Giriş başarılı. Ders kaydı ekranına yönlendiriliyorsunuz."
      YAZ "Ders seçimi yapmak ister misiniz? (E/H)"
      OKU ders_secim_istege_bagli

      EĞER ders_secim_istege_bagli == "E" İSE
        OKU SECILEN_DERSLER
        
        KONTROLLERDEN_GECTI = DOĞRU
        
        HER_BIR_DERS İÇİN SECILEN_DERSLER DÖNGÜSÜ
          EĞER DERS_KONTENJANI_DOLU_MU() İSE
            YAZ "Hata: Ders kontenjanı dolu. Ders:", Ders.Adi
            KONTROLLERDEN_GECTI = YANLIŞ
            DÖNGÜDEN_ÇIK
          DEĞİLSE EĞER DERS_ONKOSULLARI_SAGLANDI_MI() DEĞİLSE
            YAZ "Hata: Ön koşullar sağlanamadı. Ders:", Ders.Adi
            KONTROLLERDEN_GECTI = YANLIŞ
            DÖNGÜDEN_ÇIK
          DEĞİLSE EĞER ZAMAN_CAKISMASI_VAR_MI() İSE
            YAZ "Hata: Zaman çakışması. Ders:", Ders.Adi
            KONTROLLERDEN_GECTI = YANLIŞ
            DÖNGÜDEN_ÇIK
          DEĞİLSE EĞER KREDI_LIMITI_ASILDI_MI() İSE
            YAZ "Hata: Kredi limiti aşıldı."
            KONTROLLERDEN_GECTI = YANLIŞ
            DÖNGÜDEN_ÇIK
          BİTİR EĞER
        BİTİR DÖNGÜ

        EĞER KONTROLLERDEN_GECTI DOĞRU İSE
          YAZ "Dersleriniz danışman onayına gönderildi."
          EĞER DANISMAN_ONAYI_ALINDI İSE
            DERS_KAYDINI_TAMAMLA()
            YAZ "Ders kaydınız başarıyla tamamlandı."
          DEĞİLSE
            YAZ "Danışman onayı bekleniyor veya red edildi."
          BİTİR EĞER
        BİTİR EĞER
      BİTİR EĞER

      YAZ "İyi günler dileriz."
      ÇIK
    DEĞİLSE
      giris_hak = giris_hak - 1
      EĞER giris_hak > 0 İSE
        YAZ "Yanlış öğrenci ID veya şifre. Kalan hakkınız:", giris_hak
      DEĞİLSE
        YAZ "3 kez hatalı giriş. Hesabınız bloke edildi."
        ÇIK
      BİTİR EĞER
    BİTİR EĞER
  BİTİR DÖNGÜ

BİTİR
```
