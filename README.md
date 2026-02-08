
# � Beyaz Kale: Bilingual Social Network Analysis of Literary Characters
# 📖 Beyaz Kale: Edebi Karakterlerin Çift Dilli Sosyal Ağ Analizi

[![Python](https://img.shields.io/badge/Python-3.8%2B-blue)](https://www.python.org/)
[![Internship Project](https://img.shields.io/badge/Project-Software%20Engineering%20Internship-orange)]()
[![Natural Language Processing](https://img.shields.io/badge/Field-NLP%20%26%20Network%20Science-purple)]()

<!-- Language Navigation -->
<div align="center">
  <h3>
    <a href="#-türkçe">🇹🇷 Türkçe</a> | <a href="#-english">🇬🇧 English</a>
  </h3>
</div>

---

<a name="türkçe"></a>
## 🇹🇷 Türkçe

### 📌 Proje Özeti
Bu çalışma, **Bilgisayar Mühendisliği Staj Programı** kapsamında geliştirilmiş akademik nitelikli bir **Doğal Dil İşleme (NLP)** ve **Sosyal Ağ Analizi (SNA)** projesidir. Proje, Orhan Pamuk'un *"Beyaz Kale"* adlı romanını vaka çalışması olarak kullanarak, metin içerisindeki karakterleri tespit eder, bu karakterler arasındaki gizli ilişkileri açığa çıkarır ve sosyal ağ teorisi metriklerini kullanarak karakterlerin eserdeki matematiksel önemini hesaplar.

Uygulama, **Türkçe** ve **İngilizce** metinleri paralel olarak işleyebilen çift dilli bir mimariye sahiptir.

### 🔬 Metodoloji ve Teknik Detaylar

Proje, yapılandırılmamış metin verisini yapılandırılmış ağ verisine dönüştürmek için aşağıdaki boru hattını (pipeline) izler:

#### 1. Veri Ön İşleme (Data Preprocessing)
*   Excel formatındaki ham metin verisi satır satır okunur.
*   **Tokenizasyon:** Cümleler kelimelere ayrıştırılır.
*   **Stopwords Temizliği:** "ve", "ile", "bir" gibi anlamsız bağlaçlar NLTK kütüphanesi kullanılarak filtrelenir.
*   **Noktalama İşareti Temizliği:** `string` kütüphanesi ile metin temizlenir.

#### 2. Varlık İsmi Tanıma (Named Entity Recognition - NER)
Karakterlerin tespiti için dile özgü algoritmalar geliştirilmiştir:
*   **Türkçe Modülü:** `Zemberek` (Zemberek-Python) kütüphanesi kullanılarak kelimelerin morfolojik analizi yapılır. Kelime kökleri incelenerek ve önceden tanımlanmış bir isim sözlüğü (`turkish_names.txt`) ile çapraz kontrol edilerek özel isimler tespit edilir.
*   **İngilizce Modülü:** `spaCy` kütüphanesinin (`en_core_web_sm`) önceden eğitilmiş modelleri kullanılarak metindeki 'PERSON' etiketli varlıklar yüksek doğrulukla çıkarılır.

#### 3. Ağ İnşası (Network Construction)
*   **Birlikte Görülme (Co-occurrence) Analizi:** İki karakterin ismi aynı cümle içerisinde veya belirli bir kelime penceresi (window size) içinde geçiyorsa, bu karakterler arasında bir ilişki (edge/kenar) olduğu varsayılır.
*   **Ağırlıklı Kenarlar:** Karakterler ne kadar sık birlikte anılırsa, aralarındaki bağ o kadar güçlenir (Weight artışı).

#### 4. Ağ Analizi Metrikleri
Oluşturulan graf üzerinde **Graph Theory (Çizge Teorisi)** metrikleri hesaplanır:
*   **Derece Merkeziliği (Degree Centrality):** Bir karakterin kaç farklı kişiyle doğrudan ilişkisi olduğunu gösterir. Popülariteyi temsil eder.
*   **Arasılık Merkeziliği (Betweenness Centrality):** Bir karakterin, diğer karakterler arasındaki en kısa yollar üzerinde ne sıklıkla bulunduğunu ölçer. Bilgi akışını kontrol etme gücünü (köprü olma durumu) ifade eder.
*   **Yakınlık Merkeziliği (Closeness Centrality):** Karakterin ağdaki diğer herkese ne kadar yakın olduğu. Bilgiye erişim hızını gösterir.
*   **Özvektör Merkeziliği (Eigenvector Centrality):** Karakterin, diğer önemli (bağlantısı çok olan) karakterlerle olan ilişkisini ölçer. Prestij göstergesidir.

### 🛠️ Kullanılan Teknolojiler

| Teknoloji | Amaç |
|-----------|------|
| **Python** | Ana geliştirme dili. |
| **Zemberek** | Türkçe morfolojik analiz ve kök bulma. |
| **spaCy** | İngilizce Varlık İsmi Tanıma (NER). |
| **NetworkX** | Karmaşık ağların oluşturulması ve metrik hesaplamaları. |
| **Matplotlib** | Ağların görselleştirilmesi (Graph Visualization). |
| **OpenPyXL** | Veri seti manipülasyonu. |

### 📂 Proje Yapısı

```
Beyaz_Kale_Project/
├── Main.py                 # Ana uygulama motoru
├── beyaz_kale.xlsx         # Örnek veri seti (TR-EN)
├── turkish_names.txt       # Türkçe isim veritabanı
├── requirements.txt        # Bağımlılık listesi
├── README.md               # Proje dokümantasyonu
└── Results_.../            # Her analiz işlemi için oluşturulan çıktı klasörü
    ├── centrality_measures.txt  # Hesaplanan metrikler
    ├── graph_output.png         # Oluşturulan ağ haritası
    └── relations.txt            # İlişki matrisleri
```

### 🚀 Kurulum ve Kullanım

1.  **Kurulum:**
    ```bash
    git clone https://github.com/KULLANICI_ADI/REPO.git
    cd REPO
    pip install -r requirements.txt
    python -m spacy download en_core_web_sm
    ```

2.  **Çalıştırma:**
    ```bash
    python Main.py
    ```

3.  **Kullanım:**
    *   Program açıldığında analiz etmek istediğiniz `.xlsx` dosyasını seçin.
    *   İlk çalıştırmada dosyaları oluşturmak için **"2"** seçeneğini kullanın.
    *   Sonuçlar otomatik olarak oluşturulan klasörde sunulacaktır.

---

<a name="english"></a>
## 🇬🇧 English

### 📌 Project Abstract
This project is an advanced **Natural Language Processing (NLP)** and **Social Network Analysis (SNA)** application developed as part of a **Computer Engineering Internship**. Using Orhan Pamuk's novel *"The White Castle"* as a primary case study, the system detects characters within literary texts, uncovers hidden relationships between them, and calculates the mathematical importance of each character using social network theory metrics.

The architecture is fully bilingual, capable of processing both **Turkish** and **English** corpora in parallel.

### 🔬 Methodology & Technical Details

The project utilizes a strict data pipeline to transform unstructured text into structured network data:

#### 1. Data Preprocessing
*   Raw text is ingested from Excel files.
*   **Tokenization:** Segmentation of text into sentences and words.
*   **Stopword Removal:** Filtering of high-frequency but low-meaning words (conjunctions, prepositions) using NLTK.
*   **Normalization:** Cleaning of punctuation via the `string` library.

#### 2. Named Entity Recognition (NER)
Custom approaches were implemented for each language:
*   **Turkish Module:** Utilizes the `Zemberek` NLP library for morphological analysis. The system analyzes word roots and cross-references them with a comprehensive dictionary (`turkish_names.txt`) to accurately identify proper nouns in agglutinative Turkish structure.
*   **English Module:** Leverages `spaCy`'s pre-trained transformer models (`en_core_web_sm`) to extract 'PERSON' entities with high precision.

#### 3. Network Construction
*   **Co-occurrence Analysis:** A relationship (edge) is established if two characters appear within the same sentence or a defined proximity window.
*   **Weighted Edges:** The frequency of co-occurrence determines the *weight* of the relationship, indicating the strength of the bond.

#### 4. Graph Theory Metrics
We compute key centrality measures on the generated graph:
*   **Degree Centrality:** Measures the number of direct connections. Indicates immediate popularity.
*   **Betweenness Centrality:** Measures how often a node acts as a bridge along the shortest path between two other nodes. Indicates control over information flow.
*   **Closeness Centrality:** Measures the average length of the shortest path to all other nodes. Indicates independence and efficiency.
*   **Eigenvector Centrality:** Measures a node’s influence based on the influence of its neighbors.

### 🛠️ Tech Stack

| Technology | Purpose |
|------------|---------|
| **Python** | Core programming language. |
| **Zemberek** | Turkish NLP and morphological disambiguation. |
| **spaCy** | English Named Entity Recognition. |
| **NetworkX** | Complex network creation and algorithmic analysis. |
| **Matplotlib** | Data and graph visualization. |
| **OpenPyXL** | Dataset handling. |

### 📂 Directory Structure

```
Beyaz_Kale_Project/
├── Main.py                 # Core application engine
├── beyaz_kale.xlsx         # Sample dataset (TR-EN)
├── turkish_names.txt       # Turkish name database
├── requirements.txt        # PIP dependencies
├── README.md               # Documentation
└── Results_.../            # Output directory for each run
    ├── centrality_measures.txt  # Computed academic metrics
    ├── graph_output.png         # Network visualization
    └── relations.txt            # Adjacency/Relation lists
```

### 🚀 Installation & Usage

1.  **Setup:**
    ```bash
    git clone https://github.com/USERNAME/REPO.git
    cd REPO
    pip install -r requirements.txt
    python -m spacy download en_core_web_sm
    ```

2.  **Execution:**
    ```bash
    python Main.py
    ```

3.  **Operation:**
    *   Select your target `.xlsx` file when prompted.
    *   Choose option **"2"** for the initial run to generate datasets.
    *   View results in the auto-generated results folder.


