Öğrenci Ad-Soyad: Ebubekir Yılmaz
Öğrenci No: 250541051
PROSEDUR AKILLI_EV_GÜVENLİK_SİSTEMİ_BAŞLAT

// Sistemin başlangıç durumu
DEĞİŞKEN SISTEM_AKTIF = YANLIŞ
DEĞİŞKEN ALARM_DURUMU = SIFIRLANDI

// Ana Döngü: Sistem 7/24 sürekli çalışır
DÖNGÜ (SÜREKLİ)

    // 1. Sistem Aktivasyon Kontrolü
    EĞER SISTEM_AKTIF == DOĞRU İSE

        // 2. Sensör Verilerini Oku
        TÜM_SENSORLERI_OKU
        DEĞİŞKEN TEHDIT_ALGILANDI = YANLIŞ

        // 3. Tehdit Algılama
        EĞER HAREKET_SENSORU_OKU == DOĞRU VEYA KAPI_PENCERE_SENSORU_OKU == DOĞRU İSE
            TEHDIT_ALGILANDI = DOĞRU
            KAMERA_KAYDINI_BAŞLAT
        SON_EĞER

        // 4. Tehdit Durumu İşle
        EĞER TEHDIT_ALGILANDI == DOĞRU İSE

            // 4a. Yanlış Alarm Kontrolü
            EĞER EV_SAHIBI_EVDEMI == DOĞRU İSE
                ALARM_SEVIYESI = 1 // Düşük Seviye (Ev İçi Hareket)
            DEĞİLSE // Ev Sahibi Dışarıda - Gerçek Tehdit Riski
                
                // 4b. Alarm Seviyesi Belirleme (Orta veya Yüksek)
                EĞER HAREKET_VAR == DOĞRU VE ERISIM_ACIK == DOĞRU İSE
                    ALARM_SEVIYESI = 3 // Yüksek Seviye (Kombine Tehdit)
                DEĞİLSE
                    ALARM_SEVIYESI = 2 // Orta Seviye (Tek Tehdit)
                SON_EĞER
            SON_EĞER

            // 5. Alarm ve Bildirim Eylemi
            EĞER ALARM_SEVIYESI > 0 İSE
                ALARM_CALDIR(ALARM_SEVIYESI)
                BILDIRIM_GONDER(SMS, UYGULAMA, EPOSTA, ALARM_SEVIYESI)
                ALARM_DURUMU = DEVAM_EDİYOR

                // 6. Alarm Sıfırlama Döngüsü
                DÖNGÜ (ALARM_DURUMU == DEVAM_EDİYOR)
                    BEKLE(10 SANIYE)
                    EĞER KULLANICI_ALARM_SIFIRLAMA_KOMUTU_GELDİ İSE
                        ALARM_DURUMU = SIFIRLANDI
                        KAMERA_KAYDINI_DURDUR
                    SON_EĞER
                SON_DÖNGÜ

                ALARM_SIFIRLA
            SON_EĞER

        SON_EĞER

    DEĞİLSE // Sistem Pasif Durumda
        BEKLE(5 SANIYE) // Enerji Tasarrufu
    SON_EĞER

SON_DÖNGÜ

SON_PROSEDUR
