# Türkiye 81 İl Makine Öğrenmesi Projesi (Coğrafi ve Sosyo-Ekonomik Analiz)

Bu proje, Türkiye'nin 81 iline ait **enlem-boylam koordinatları** ve **sosyo-ekonomik göstergeleri** kullanarak **Keşifçi Veri Analizi (EDA)**, **Denetimsiz Öğrenme (Enlem/Boylam ile K-Means 7 Kümeleme & Türkiye Haritası)**, **Çok Sınıflı Sınıflandırma (Random Forest ile 7 Coğrafi Bölge Tahmini)** ve **Regresyon (Kişi Başı Gelir Tahmini)** analizlerini gerçekleştiren uçtan uca bir veri bilimi çalışmasıdır.

---

## 📁 Proje Klasör Mimarisi

```text
Makine_ogrenmesi_odev1/
│
├── data/                      # Projede kullanılan veri setlerini barındıran klasör.
│   └── turkiye_81_il.csv      # 81 ile ait enlem, boylam, nüfus, gelir ve sanayi verilerini içeren CSV veri seti.
│
├── notebooks/                 # Tüm makine öğrenmesi aşamalarının yürütüldüğü Jupyter defterleri.
│   └── proje.ipynb            # EDA, 7 Küme Haritası, Sınıflandırma ve Regresyon analizlerinin ana defteri.
│
├── .gitignore                 # Sanal ortam, önbellek ve gereksiz sistem dosyalarının Git'e eklenmesini önleyen dosya.
├── requirements.txt           # Projenin çalışması için gereken Python kütüphanelerini listeleyen bağımlılık dosyası.
├── README.md                  # Projenin amacını, veri kaynaklarını ve kurulum adımlarını özetleyen kılavuz doküman.
└── proje.ipynb                # Kök dizinde de doğrudan çalıştırılabilir ve çıktıları saklanmış notebook kopyası.
```

---

## 🌐 Veri Seti ve Resmi Kaynaklar (Data Sources)

Projede kullanılan [turkiye_81_il.csv](data/turkiye_81_il.csv) veri seti, Türkiye Cumhuriyeti resmi kamu kurumlarının açık veri ve istatistik portallarından derlenmiştir:

| Gösterge | Değişken Adı | Resmi Kaynak Kurum | Doğrudan Erişim Linki |
| :--- | :--- | :--- | :--- |
| **Coğrafi Koordinatlar** | `enlem`, `boylam` | **Harita Genel Müdürlüğü (HGM)** & **AFAD** | [harita.gov.tr](https://www.harita.gov.tr) / [veri.afad.gov.tr](https://veri.afad.gov.tr) |
| **Nüfus** | `nufus` | **TÜİK** (Adrese Dayalı Nüfus Kayıt Sistemi) | [TÜİK Nüfus ve Demografi Portalı](https://data.tuik.gov.tr/Kategori/GetKategori?p=Nufus-ve-Demografi-109) |
| **Kişi Başı Gelir** | `kisi_basi_gelir` | **TÜİK** (İl Düzeyinde Kişi Başına GSYH Bülteni) | [TÜİK İl Bazında GSYH İstatistikleri](https://data.tuik.gov.tr/Kategori/GetKategori?p=Ekonomi-ve-Ticaret-107) |
| **İşsizlik Oranı** | `issizlik_orani` | **TÜİK & İŞKUR** (Bölgesel İşgücü Göstergeleri) | [TÜİK İstihdam ve İşsizlik Portalı](https://data.tuik.gov.tr/Kategori/GetKategori?p=Istihdam-Issizlik-ve-Ucret-108) |
| **Eğitim Göstergeleri** | `okullasma_orani`, `okur_yazar_orani` | **Milli Eğitim Bakanlığı (MEB)** & **TÜİK** | [MEB Resmi İstatistik Portalı](https://sgb.meb.gov.tr/www/resmi-istatistikler/kategori/88) |
| **Sanayi ve Tarım Payı** | `sanayi_payi`, `tarim_payi` | **Sanayi ve Teknoloji Bakanlığı (SEGE Araştırması)** | [Sanayi ve Teknoloji Bakanlığı SEGE Raporları](https://www.sanayi.gov.tr/merkez-birimi/b94224510b7b/sege) |
| **İl İhracat Hacmi** | `ihracat_milyon_dolar` | **Türkiye İhracatçılar Meclisi (TİM)** | [TİM İl Bazında İhracat Rakamları](https://tim.org.tr/tr/ihracat-rakamlari) |

---

## ⚙️ Kurulum ve Sanal Ortam (Virtual Environment)

### 1. Sanal Ortamı Oluşturma
Terminal veya PowerShell'de proje kök dizininde şu komutu çalıştırın:
```bash
python -m venv venv
```

### 2. Sanal Ortamı Aktifleştirme
- **Windows (PowerShell):**
  ```powershell
  .\venv\Scripts\Activate.ps1
  ```
  *(Eğer yetki hatası alırsanız PowerShell'de: `Set-ExecutionPolicy -Scope Process -ExecutionPolicy Bypass` komutunu çalıştırabilirsiniz.)*
- **Windows (Komut İstemi / CMD):**
  ```cmd
  venv\Scripts\activate.bat
  ```

### 3. Gerekli Kütüphaneleri Yükleme
```bash
pip install -r requirements.txt
```

### 4. Jupyter Notebook'u Başlatma
```bash
jupyter notebook
```
veya doğrudan VS Code / Cursor editöründe `notebooks/proje.ipynb` dosyasını açıp sağ üstten oluşturulan `venv` kernel'ini seçebilirsiniz.

---

## 🎯 Proje Aşamaları

1. **Adım 1: Proje İskeleti ve Dosya Düzeni**
   - Modüler dizin mimarisi, `requirements.txt` bağımlılıkları ve sanal ortam yapılandırması.
2. **Adım 2: Veri Yükleme ve Keşifçi Veri Analizi (EDA)**
   - Eksik veri kontrolü, temel betimsel istatistikler ve Seaborn korelasyon ısı haritası.
3. **Adım 3: Enlem ve Boylam Koordinatlarına Göre 7 Kümeleme (K-Means & Türkiye Haritası)**
   - İllerin enlem ve boylam koordinatları kullanılarak K-Means ($k=7$) ile kümelenmesi.
   - 7 küme merkezinin (Centroids) kırmızı yıldızlarla gösterildiği Türkiye Haritası saçılım grafiği.
   - Bulunan 7 küme ile Türkiye'nin gerçek 7 coğrafi bölgesinin çapraz tablo (`crosstab`) ile karşılaştırılması.
4. **Adım 4: Random Forest ile 7 Coğrafi Bölge Sınıflandırması**
   - İllerin koordinat ve sosyo-ekonomik özelliklerinden bölgesini tahmin eden çok sınıflı sınıflandırma modeli.
   - Sınıflandırma Başarı Raporu (Precision, Recall, F1-Score) ve Karmaşıklık Matrisi (Confusion Matrix) ısı haritası.
5. **Adım 5: Kişi Başına Düşen Gelir Regresyonu**
   - Doğrusal Regresyon (Linear Regression) ile Random Forest Regressor kıyaslaması.
   - MAE, RMSE ve $R^2$ (Belirlilik Katsayısı) metriklerinin analizi ve grafiksel gösterimi.
