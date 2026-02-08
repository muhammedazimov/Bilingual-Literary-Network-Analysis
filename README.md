
# Beyaz Kale - Metin Analizi ve Karakter Ağı

Bu proje, Orhan Pamuk'un "Beyaz Kale" romanı üzerinde karakter ilişkilerini ve metin analizini gerçekleştiren bir Python uygulamasıdır. Proje, hem Türkçe hem de İngilizce metinleri analiz ederek karakter ağlarını görselleştirir ve merkezilik ölçümlerini hesaplar.

> **Not:** Bu proje, staj kapsamında geliştirilmiş bir çalışmadır.

## Özellikler

-   **Çift Dilli Analiz:** Türkçe ve İngilizce metinleri destekler.
-   **Karakter Ağı Çıkarımı:** Metin içerisindeki karakterleri tespit eder ve birlikte geçme sıklıklarına göre ilişki ağları oluşturur.
-   **Merkezilik Ölçümleri:** Oluşturulan ağlar üzerinde Derece (Degree), Arasılık (Betweenness), Yakınlık (Closeness) ve Özvektör (Eigenvector) merkeziliklerini hesaplar.
-   **Görselleştirme:** Karakter ağlarını görsel olarak sunar.
-   **Zemberek Entegrasyonu:** Türkçe morfolojik analiz için Zemberek kütüphanesini kullanır.

## Gereksinimler

Projenin çalışması için aşağıdaki Python kütüphanelerine ve Java Runtime Environment (JRE)'a ihtiyaç vardır:

-   Python 3.8+
-   Java 8+ (Zemberek için gereklidir)

Gerekli Python paketlerini yüklemek için:

```bash
pip install -r requirements.txt
```

Ayrıca spaCy İngilizce dil modelini indirmeniz gerekmektedir:

```bash
python -m spacy download en_core_web_sm
```

## Kurulum ve Çalıştırma

1.  Projeyi bilgisayarınıza indirin.
2.  Gerekli kütüphaneleri yükleyin (yukarıdaki adımları izleyin).
3.  `beyaz_kale.xlsx` dosyasının proje dizininde olduğundan emin olun (veya kendi veri setinizi kullanın).
4.  Uygulamayı çalıştırın:

```bash
python Main.py
```

5.  Program başladığında sizden analiz edilecek kitabı içeren Excel dosyasını seçmeniz istenecektir (1. Sütun Türkçe, 2. Sütun İngilizce metin olmalıdır).
6.  Ardından, karakter listelerini içeren dosyalarınızın olup olmadığını soracaktır. İlk çalıştırmada "2" seçeneğini kullanarak dosyaların oluşturulmasını sağlayabilirsiniz.

## Dosya Yapısı

-   `Main.py`: Ana uygulama kodu.
-   `beyaz_kale.xlsx`: Örnek veri dosyası.
-   `turkish_names.txt`: Türkçe isimlerin listesi (karakter tespiti için kullanılır).
-   `requirements.txt`: Gerekli Python kütüphaneleri.

## Çıktılar

Program çalıştırıldığında seçilen Excel dosyasının adıyla bir klasör oluşturulur (örneğin `Results_beyaz_kale`) ve tüm analiz sonuçları bu klasöre kaydedilir:
-   `characterRelationsTR.txt`, `characterRelationsEN.txt`: Karakter ilişki ağırlıkları.
-   `centrality_measures.txt`: Merkezilik ölçümleri.
-   Grafiksel görseller.
