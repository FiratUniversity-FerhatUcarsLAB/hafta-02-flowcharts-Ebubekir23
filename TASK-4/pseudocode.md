Öğrenci Ad-Soyad: Ebubekir Yılmaz
Öğrenci No: 250541051
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
