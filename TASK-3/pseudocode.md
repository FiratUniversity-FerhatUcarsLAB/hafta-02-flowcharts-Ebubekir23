Öğrenci Ad-Soyad: Ebubekir Yılmaz
Öğrenci No: 250541051
FONKSİYON RandevuAl()
  BAŞLANGIÇ
  1. KULLANICI_KIMLIK_DOGRULA(KullaniciID, Sifre)
      EĞER KimlikDoğrulama_BAŞARILI İSE
      2. KULLANICI_GIRIS_YAP()
      3. POLIKLINIK_SECIMI_EKRANI_GOSTER()
      4. KULLANICI_POLIKLINIK_SEC(SecilenPoliklinik)
      5. DOKTOR_LISTESI_GETIR(SecilenPoliklinik)
      6. KULLANICI_DOKTOR_SEC(SecilenDoktor)
      7. UYGUN_SAATLERI_GETIR(SecilenDoktor, SecilenTarih)
      8. KULLANICI_SAAT_SEC(SecilenSaat)
      9. RANDEVU_ONAY_EKRANI_GOSTER(RandevuDetaylari)
      10. KULLANICI_ONAY_VER()
          EĞER Onay_VERILDI İSE
          11. RANDEVU_VERITABANINA_KAYDET(RandevuDetaylari)
          12. SMS_GONDER(KullaniciTelefon, RandevuDetaylari)
          13. EKRANA_MESAJ_GOSTER("Randevunuz başarıyla oluşturuldu.")
          DEĞİLSE
          14. EKRANA_MESAJ_GOSTER("Randevu işlemi iptal edildi.")
      DEĞERLENDİRME_BİTİŞİ
      DEĞİLSE
      15. EKRANA_MESAJ_GOSTER("Kimlik doğrulama başarısız. Lütfen tekrar deneyin.")
      DEĞERLENDİRME_BİTİŞİ
  BİTİŞ
