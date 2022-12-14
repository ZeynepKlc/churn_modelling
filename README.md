# CHURN MODELLING

Veri setini [kaggle](https://www.kaggle.com/datasets/shubh0799/churn-modelling) sitesinden yükleyebilirsiniz.



[![N|Solid](https://cldup.com/dTxpPi9lDf.thumb.png)](https://nodesource.com/products/nsolid)

[![Build Status](https://travis-ci.org/joemccann/dillinger.svg?branch=master)](https://travis-ci.org/joemccann/dillinger)

## _Veri Seti Hikayesi_

Veri setinde banka müşterilerinin bazı banka hesap bilgileri ve demografik özellikleri (yaş,cinsiyet,tahmini maaş vb.) ayrıntılı bilgileri mevcuttur.Müşteri kayıp analizi yaparak,  müşterilerin bankayı terk edip etmeme ihtimallerini önceden tahmin etmek istiyoruz.


## Veri Setindeki Değişkenler

- **CustomerId:** Bankada bulunan müşterilerin kimlik numarasıdır.
- **Surname:** Müşterilerin soyisimlerini içeren değişkendir
- **CreditScore:** Müşterilerin kredi notlarını içeren değişkendir.
- **Geography:** Müşterilerin ülkelerini belirten değişkendir.
- **Gender:** Müşterilerin cinsiyetlerini belirten değişkendir.
- **Age:** Müşterilerin yaşlarını belirten değişkendir.
- **Tenure:** Müşterilerin bankada bulunduğu yıl sayısıdır.
- **Balance:** Müşterilerin bankadaki parasıdır.
- **NumOfProducts:** Müşterilerin sahip olduğu banka ürün sayılarıdır.
- **HasCrCard:** Müşterilerin kredi kartının olup olmadığını 1 ve 0'larla gösteren değişkendir.
- **IsActiveMember:** Müşterilerin aktif üye olup olmadıklarını gösteren değişkendir.
- **EstimatedSalary:** Müşterilerin tahmini maaşlarıdır.
- **Exited:** Müşterilerin bankayı terk edip etmediklerini ifade eden değişkendir.


> Tüm kütüphaneleri import ediyoruz. 
> Veri setini yüklüyoruz.



```sh
import pandas as pd 
df=pd.read_csv("Churn_Modelling.csv").copy()
```


##  Keşifçi Veri Analizi

- Veri setimizi test ve train seti olarak ikiye ayırıp train setiyle modele koyup en başarılı makine öğrenmesi modeliyle test setimizdeki başarı performansını değerlendireceğiz.

- Müşterinin churn olma durumuna etkisi olmayan, gereksiz verileri veri setinden siliyoruz.





## Veri Görselleştirme

Veri görselleştirme, verileri daha iyi anlayabilmek, aralarındaki ilişkileri, dağılımları gözlemlemek için kullandığımız bir bölümdür.



# Sonuç

- Bankada 3-4 ürüne sahip müşterilerin bankayı terk etmeleri 1-2 ürüne sahip müşterilere göre daha fazla.
- Almanya'daki müşterilerin Fransa ve İspanya'ya göre bankayı terk etme oranları daha yüksek.
- Banka müşterilerinin ortalama yaş aralığı 38-42 arası değişiyor.
- 70 yaş üzeri müşterilerin büyük çoğunluğu bankada kalmayı tercih ediyor.


# Rapor

Müşterilerin bankayı terk edip etmemelerini tahmin etmek için oluşturulan ve grafiklerle veriyi anlamaya çalışıp bir takım nesnel yorumlar getirdikten sonra veri önişleme ile veriler düzenlenip modele uygun hale getirildi. Random-Forest,Gradient Boosting ve Lightgbm modelleri kullanıldı ve model için son aşamada LightGBM modeli seçilmiştir.

- **LightGBM modelinde;**
  
  
  *Accuracy skoru % 82.9*
  
  *Cross val. skoru % 86.15 olarak ölçülmüştür.*

- **Doğru tahmin edilenler**   --> %82.9 (2000 tahminden 1658 tanesi doğru)
 
  *True Negative --> %68.95 --> Churn olmayacağı tahmin edilenler ve churn olmayanlar.*
  
  *True Positive --> %13.95  --> Churn olacağı tahmin edilen ve churn olanlar.*
  

- **Yanlış tahmin edilenler**   --> %17.1 (2000 tahminden 342 tanesi yanlış)

   *False Positive --> %6.70  --> Churn olacağı tahmin edilen ama churn olmayanlar.*
   
   *False Negative --> %10.40 --> Churn olmayacağı tahmin edilen ama churn olanlar.*
  


- **Churn olmayanlar**
  
  *Gerçek test veri setinde (0)            --> 1587*
  
  *Test veri seti içinde tahmin edilen (0) --> 1513*


- **Churn olanlar**
  
  *Gerçek test veri setinde (1)            --> 413*
  
  *Test veri seti içinde tahmin edilen (1) --> 487*
  


