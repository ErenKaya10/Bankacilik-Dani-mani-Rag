# 🏦 Akıllı Bankacılık Danışmanı — RAG

> **BERT Fine-Tuning ve RAG tabanlı, 16 bankacılık kategorisinde hizmet veren akıllı chatbot**

---

## 📖 Proje Hakkında

**Akıllı Bankacılık Danışmanı - RAG**, bankacılık sektöründe müşteri taleplerini anlayan, sınıflandıran ve doğru kaynağa yönlendiren yapay zeka tabanlı bir asistandır.

- 🗂️ 16 farklı bankacılık kategorisi
- 🎯 BERT modeli fine-tune → **%96 doğruluk oranı**
- 🔍 RAG (Retrieval-Augmented Generation) ile güncel bankacılık bilgileri
- 🖥️ Gradio ile kullanıcı dostu web arayüzü



---

## 🎯 Proje Özellikleri

| Özellik | Detay |
|---|---|
| Kategori Sayısı | 16 bankacılık işlemi |
| Veri Seti | 1.280+ Türkçe bankacılık cümlesi |
| Model Doğruluğu | %96 |
| Yanıt Süresi | 2–3 saniye |
| RAG Bilgi Chunk'ı | 50+ |
| Arayüz | Gradio |

---

## 🗂️ Kategoriler

| ID | Kategori | Açıklama |
|---|---|---|
| 0 | `kart_aktivasyon` | Kredi kartı aktivasyonu |
| 1 | `kart_iptal` | Kart iptali / kayıp / çalıntı |
| 2 | `ucret_ve_komisyonlar` | Banka ücretleri ve komisyonlar |
| 3 | `kart_basvuru` | Yeni kart başvurusu |
| 4 | `kart_faiz` | Kredi kartı faiz oranları |
| 5 | `havale_iban` | Havale / EFT işlemleri |
| 6 | `sifre_unuttum` | Şifre / PIN işlemleri |
| 7 | `sube_atm` | Şube / ATM bilgileri |
| 8 | `dolandiricilik` | Dolandırıcılık şüphesi |
| 9 | `musteri_hizmetleri` | Müşteri hizmetleri |
| 10 | `ihtiyac_kredisi_basvuru` | İhtiyaç kredisi başvurusu |
| 11 | `ihtiyac_kredisi_faiz` | İhtiyaç kredisi faiz oranları |
| 12 | `konut_kredisi_basvuru` | Konut kredisi başvurusu |
| 13 | `konut_kredisi_faiz` | Konut kredisi faiz oranları |
| 14 | `tasit_kredisi_basvuru` | Taşıt kredisi başvurusu |
| 15 | `tasit_kredisi_faiz` | Taşıt kredisi faiz oranları |

---

## 📁 Proje Dosyaları

| Dosya | Açıklama | Boyut |
|---|---|---|
| `son_model.ipynb` | Ana chatbot uygulaması (Jupyter Notebook) | 87 KB |
| `Model_Egitimi.ipynb` | BERT modeli fine-tune eğitim kodu | 328 KB |
| `banking_dataset_genisletilmis_80_tr_duzeltilmis.json` | Türkçe bankacılık veri seti (1.280+ cümle) | 137 KB |
| `banka_bilgi_bankasi_rag_detayli.json` | RAG bilgi bankası (50+ chunk) | 96 KB |
| `banka_bilgi_bankasi_rag_detayli.txt` | RAG bilgi bankası (okunabilir format) | 98 KB |
| `kategori_haritasi_final.json` | Kategori ID eşleştirmeleri | 952 B |
| `confusion_matrix.png` | Model performans görseli | 118 KB |

---

## 📚 Veri Seti

Projede İngilizce referans olarak **[PolyAI/banking77](https://huggingface.co/datasets/PolyAI/banking77)** veri seti kullanılmıştır (77 kategori, 13.083 soru). Ancak bu proje için **hibrit bir Türkçe veri seti** oluşturulmuştur:

- 16 farklı bankacılık kategorisi
- Her kategori için 80+ örnek cümle
- Toplamda **1.280+ Türkçe bankacılık cümlesi**

---

## 🚀 Kurulum ve Çalıştırma

### 1️⃣ Dosyaları İndir

Repoyu klonla veya ZIP olarak indir:


### 2️⃣ Google Drive'da Klasör Oluştur

Google Drive'ında `Bankacilik` adında bir klasör oluştur.

### 3️⃣ Dosyaları Drive'a Yükle

Aşağıdaki dosyaları `Bankacilik` klasörüne yükle:

- `banking_dataset_genisletilmis_80_tr_duzeltilmis.json`
- `banka_bilgi_bankasi_rag_detayli.json`
- `kategori_haritasi_final.json`

### 4️⃣ Modeli Eğit

1. `Model_Egitimi.ipynb` dosyasını **Google Colab** ile aç
   - `Dosya` → `Notebook yükle` → dosyayı seç
2. `Runtime` → `Change runtime type` → **T4 GPU** seç
3. `Runtime` → `Run all` ile çalıştır
4. Drive bağlantısı istendiğinde izin ver

Adım tamamlandığında Drive'ında şunlar oluşacak:

```
Bankacilik/
├── bert_intent_model_final/   ← eğitilmiş BERT modeli
└── confusion_matrix.png       ← performans grafiği
```

> ⏱️ **Tahmini süre:** 20–30 dakika (Colab ücretsiz GPU)

### 5️⃣ Chatbot'u Başlat

1. `son_model.ipynb` dosyasını **Google Colab** ile aç
2. `Runtime` → `Run all` yap
3. Drive bağlantısına izin ver
4. Oluşan Gradio linkine tıkla:

```
Running on public URL: https://xxxx.gradio.app
```

### 6️⃣ Test Et

| Soru | Beklenen Kategori |
|---|---|
| "Kredi kartımı nasıl aktif ederim?" | `kart_aktivasyon` |
| "Kartım kayboldu ne yapmalıyım?" | `kart_iptal` |
| "Konut kredisi faiz oranları nedir?" | `konut_kredisi_faiz` |
| "İhtiyaç kredisi için gerekli belgeler" | `ihtiyac_kredisi_basvuru` |
| "Havale ücreti ne kadar?" | `ucret_ve_komisyonlar` |

---

## 🏗️ Sistem Mimarisi

```
Kullanıcı Mesajı
       │
       ▼
┌──────────────────────────────────────────┐
│  1. BERT — Intent Detection              │
│     16 kategoriden birine sınıflandır    │
│     Güven skoru hesapla (0–100%)         │
└──────────────────────────────────────────┘
       │
       ▼
┌──────────────────────────────────────────┐
│  2. Güven Kontrolü                       │
│     ≥ %50 → RAG'e yönlendir             │
│     < %50 → "Anlayamadım" yanıtı        │
└──────────────────────────────────────────┘
       │
       ▼
┌──────────────────────────────────────────┐
│  3. RAG Sistemi (ChromaDB)               │
│     Metni embedding vektörüne çevir      │
│     En benzer chunk'u getir              │
└──────────────────────────────────────────┘
       │
       ▼
┌──────────────────────────────────────────┐
│  4. Yanıt Oluşturma                      │
│     Başlık + Bilgi + Süre + Güven skoru  │
└──────────────────────────────────────────┘
       │
       ▼
Kullanıcıya Yanıt  ⏱️ ~2–3 saniye
```

---

## 📊 Performans Metrikleri

```
              precision    recall  f1-score   support

kart_aktivasyon       1.00      1.00      1.00        16
kart_iptal            1.00      0.88      0.93        16
ucret_ve_komisyonlar  1.00      1.00      1.00        16
...
ihtiyac_kredisi_faiz  0.79      0.94      0.86        16
konut_kredisi_faiz    0.92      0.75      0.83        16

accuracy                            0.96       256
macro avg             0.96      0.96      0.96       256
```

Confusion matrix görseli: [`confusion_matrix.png`](confusion_matrix.png)

---

## 🛠️ Kullanılan Teknolojiler

| Teknoloji | Kullanım Amacı |
|---|---|
| Python 3.10 | Ana programlama dili |
| PyTorch | Derin öğrenme kütüphanesi |
| Transformers (Hugging Face) | BERT ve LLM modellerini yükleme |
| `dbmdz/bert-base-turkish-128k-cased`| https://huggingface.co/dbmdz/bert-base-turkish-128k-cased | Türkçe intent detection |
| Sentence-Transformers | Metin embedding |
| ChromaDB | Vektör veritabanı (RAG) |
| Gradio | Web arayüzü |
| Scikit-learn | Performans metrikleri |

## Önemli 
## 🔧 Notebook Görüntüleme Sorunu

Eğer GitHub'da `Invalid Notebook` hatası alıyorsanız, lütfen aşağıdaki linkleri kullanın:

- [Model_Egitimi.ipynb (NBSanity ile görüntüle)](https:nbsanity.com/ErenKaya10/Bankacilik-Dani-mani-Rag/blob/main/Model_Egitimi.ipynb)
- [son_model.ipynb (NBSanity ile görüntüle)](https://nbsanity.com/ErenKaya10/Bankacilik-Dani-mani-Rag/blob/main/son_model.ipynb)

Bu bağlantılar notebook'ları sorunsuz şekilde gösterecektir.


---

## 📄 Lisans

Bu proje [MIT](LICENSE) lisansı altında sunulmaktadır.
