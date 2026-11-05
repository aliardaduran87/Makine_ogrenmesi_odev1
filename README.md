# Türkiye 81 İl Sosyo-Ekonomik Makine Öğrenmesi Projesi

Bu proje, Türkiye'nin 81 iline ait sosyo-ekonomik göstergeleri kullanarak **Keşifçi Veri Analizi (EDA)**, **Denetimsiz Öğrenme (K-Means Kümeleme & PCA)**, **Çok Sınıflı Sınıflandırma (Random Forest ile Coğrafi Bölge Tahmini)** ve **Regresyon (Kişi Başı Gelir Tahmini)** analizlerini gerçekleştiren uçtan uca bir makine öğrenmesi çalışmasıdır.

---

## 📁 Proje Klasör Mimarisi

```text
ml-odev1/
│
├── data/                      # Projede kullanılan ham ve işlenmiş veri setlerini barındıran klasör.
│   └── turkiye_81_il.csv      # 81 ile ait sosyo-ekonomik ve demografik verileri içeren CSV veri seti.
│
├── notebooks/                 # Aşama aşama deneysel analizlerin yürütüldüğü Jupyter defterleri.
│   └── proje.ipynb            # EDA, Kümeleme, Sınıflandırma ve Regresyon adımlarının uygulandığı ana defter.
│
├── .gitignore                 # Sanal ortam, geçici dosyalar ve gereksiz sistem dosyalarının Git'e eklenmesini önleyen dosya.
├── requirements.txt           # Projenin çalışması için gereken Python kütüphanelerini listeleyen bağımlılık dosyası.
└── README.md                  # Projenin amacını, kurulum adımlarını ve dosya yapısını özetleyen dokümantasyon dosyası.
```

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

## 🎯 Proje Adımları

1. **Adım 1:** Proje İskeleti ve Dosya Düzeni
2. **Adım 2:** Veri Yükleme ve Keşifçi Veri Analizi (EDA)
3. **Adım 3:** K-Means ile İllerin Sosyo-Ekonomik Kümelenmesi ve PCA Görselleştirmesi
4. **Adım 4:** Random Forest ile 7 Coğrafi Bölge Sınıflandırması
5. **Adım 5:** Doğrusal Regresyon ve Random Forest ile Kişi Başına Düşen Gelir Tahmini

