# aygaz_bootcamp_MLProject

--https://www.kaggle.com/code/seynoma/supervised-fraud-detection

--https://www.kaggle.com/code/seynoma/unsupervised-fraud-detection

1. Veri Yükleme ve Keşifsel Veri Analizi (Exploratory Data Analysis - EDA):
Her iki notebook'ta da çevrimiçi ödeme sahtekarlık verileriyle çalıştım. İlk olarak, veri setindeki sütunları inceledim ve bunlar üzerinden bazı tanımlayıcı istatistikler çıkardım:

Veri setindeki sütunlar:
step: Zamanı temsil eden adımlar.
amount: İşlemin tutarı.
oldbalanceOrg / newbalanceOrig: Gönderen hesabın işlem öncesi ve sonrası bakiyeleri.
oldbalanceDest / newbalanceDest: Alıcı hesabın işlem öncesi ve sonrası bakiyeleri.
isFraud: İşlemin sahte olup olmadığını belirten hedef değişken.
isFlaggedFraud: Şüpheli olarak işaretlenen işlemler.
Veri setinin genel yapısını ve dağılımını anlamak için tanımlayıcı istatistikler kullanarak (df.describe()) sütunların ortalamalarını, minimum ve maksimum değerlerini inceledim. Ayrıca verilerin dengesizliğini fark ettim; isFraud etiketinin büyük kısmı sahte olmayan işlemlerden oluşuyor.

2. Veri Dengesizliği ile Başa Çıkma:
Veri setindeki sınıflar arasında dengesizlik vardı. Bu dengesizlik, dolandırıcılık olmayan işlem sayısının çok fazla olması nedeniyle modelin dolandırıcılık işlemlerini tanımakta zorlanmasına neden olabilirdi. Bu durumu çözmek için denetimsiz öğrenme notebook'unda RandomUnderSampler kullanarak dolandırıcılık olmayan işlemlerin sayısını azalttım. Bu sayede veri setini dengeleyerek daha adil bir öğrenme sağladım.

3. Denetimli Öğrenme Yöntemleri:
Denetimli öğrenme notebook'unda, etiketlenmiş verilerle çalıştım ve hedef değişken olan isFraud ile dolandırıcılığı tespit etmeye yönelik çeşitli algoritmalar denedim. Kullanılan algoritmalar:

Lojistik Regresyon: İlk denediğim yöntem lojistik regresyondu. Bu yöntem, dolandırıcılık tespitinde temel bir sınıflandırıcı olarak etkili olabilir.

Karar Ağaçları ve Rastgele Orman (Random Forest): Karar ağaçları ve rastgele orman yöntemlerini denedim. Bu algoritmalar, verinin yapısını iyi öğrenen güçlü modellerdir ve sınıflandırma performansında önemli iyileşmeler sağlayabilir.

XGBoost: Daha sonra XGBoost algoritmasını denedim. Yüksek doğruluk ve hız avantajı sunan bu algoritma ile model performansını artırmayı amaçladım.

Veri bölünmesi: Veriyi eğitim ve test seti olarak böldüm. Genelde %80 eğitim ve %20 test olarak ayırarak modellerin genel başarımını değerlendirdim.

Performans değerlendirme:

Doğruluk (Accuracy), Hassasiyet (Precision), Duyarlılık (Recall) ve F1 skoru gibi metriklerle modellerin performansını değerlendirdim. Bu metrikler, özellikle dengesiz veri setlerinde modelin ne kadar doğru sonuçlar verdiğini anlamak için önemlidir.
4. Denetimsiz Öğrenme Yöntemleri:
Denetimsiz öğrenme notebook'unda etiketlenmemiş verilerle çalıştım ve anomali tespiti yaparak sahtecilik tespit etmeye çalıştım. Kullandığım algoritmalar:

K-Means: Bu algoritma ile veriyi kümeler haline getirdim. K-Means, verileri gruplar halinde kümeler ve olağandışı işlemler kümelerin dışında kaldığı için bu işlemleri anomali (yani sahtecilik) olarak işaretledim.

DBSCAN: DBSCAN algoritmasını da denedim. Bu yöntem, verideki yoğun bölgeleri kümeler olarak tanımlar ve düşük yoğunluklu bölgeleri anomali olarak işaretler. Bu sayede olağandışı işlemleri tespit etmeye çalıştım.

İzole Orman (Isolation Forest): İzole Orman algoritmasını kullanarak, verilerdeki normal işlemleri izole edip anomali olarak nitelendirilen işlemleri tespit etmeye çalıştım.

5. Sonuçlar:
Her iki yaklaşımda da algoritmaların performansını değerlendirdim. Denetimli öğrenme yöntemlerinde elde ettiğim doğruluk ve F1 skoru, özellikle XGBoost algoritması ile iyi sonuçlar verdi. Denetimsiz öğrenme yöntemleri ise anomali tespitine dayandığı için, sahtecilik işlemlerini doğrudan yakalama kapasitesi sınırlıydı, ancak bazı yöntemler (örneğin, İzole Orman) daha başarılı sonuçlar verdi.
