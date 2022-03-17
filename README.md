# GEE
Google Earth Engine Introduction

Google Earth Engine, Dünya yüzeyindeki değişiklikleri algılamak, eğilimleri haritalamak ve farklılıkları ölçmek için uydu görüntülerinin büyük ölçekli işlenmesini sağlayan bulut tabanlı bir platformdur. 

## Cloud Computing
Bulut bilişim yani cloud computing, internet aracılığıyla sağlanan donanım ve yazılımın kullanımını tanımlar. 

Bulut bilişim, uzaktan algılamanın neresinde?

Hava durumu haritalarının ve yüksek çözünürlüklü uydu tabanlı haritaların çevrimiçi mevcudiyeti göz önüne alındığında, bulut bilişimin uzaktan algılamada zaten düzenli olarak kullanıldığı iddia edilebilir. Bununla birlikte, şu anda bulutta bulunmayan, toplumsal ve ekonomik faydaları olan sayısız başka uzaktan algılama uygulaması vardır.

Bulut bilişimin uzaktan algılamadaki avantajları nelerdir?

* Çevrimiçi, isteğe bağlı, ölçeklenebilir görüntü işleme yetenekleri sağlar.
* Küresel bir kullanıcı topluluğuna görüntüden türetilen ürünler ve görselleştirme araçları sunar.
* İşleme araçlarının, büyük görüntü veritabanlarıyla verimli bir şekilde bir arada bulunmasına olanak tanır.
* Uzman olmayanların yazılım engellerini ve donanım gereksinimlerini ortadan kaldırır.
* Yeni algoritmaların ve işleme araçlarının hızlı entegrasyonunu ve dağıtımını kolaylaştırır.
* Gelişmiş uygulama paylaşımı yoluyla uzaktan algılamada teknoloji transferini hızlandırır.
* Uzaktan algılama bilim adamlarını amaçlanan son kullanıcılarla daha doğrudan birleştirir.

Populer Cloud Computing Platformları
* AWS
* Microsoft Azure
* IBM Cloud
* Google Cloud

## GEE'in Özellikleri
* Büyük veri işlemede kullanılabilecek paralel process'lere ve hızlı hesaplama platformlarına sahiptir.
* Kullanıcılar, GEE'deki verileri kendi çalışma ortamlarına indirmeye ve başka bir yazılım ile GEE'de bulunan bir işleme işlemini gerçekleştirmeye gerek kalmadan Google sunucularını kullanabilirler.
* GEE birçok kullanıma hazır algoritmaya sahiptir.

## GEE Datasets
* Landsat 4, 5, 7, 8
* MODIS
* Sentinel 1, 2 ,3
* Atmospheric Data
* Meteorological Data
* Vectorial Data

## Code Editor
Earth Engine Javascript API'si için bir Entegre Geliştirme Ortamıdır (IDE). Kod yazmak, hata ayıklamak, çalıştırmak ve yönetmek için kolay bir yol sunar . 

### Image Collection ile çalışma
Earth Engine'deki çoğu veri kümesi bir 'ImageCollection'dır.
Bir ImageCollection, genellikle aynı uydu veya veri sağlayıcıdan farklı zaman ve konumlarda alınan görüntülerden oluşan bir veri kümesidir. 
Koleksiyon, sensör tarafından şimdiye kadar toplanan tüm görüntüleri içerir. 
Tüm koleksiyonlar çok kullanışlı değil. Çoğu uygulama, görüntülerin bir alt kümesini gerektirir. 

Uygun görüntüleri seçmek için filtreler kullanıyoruz .
Birçok filtre işlevi türü vardır, bir filtre seçin ve ardından filter() işlevi filtre parametreleriyle çalıştırın.


3 ana filtreleme tekniği:
* Meta verilere göre filtrele (ee.Filter.eq()) : ee.Filter.lt() vb. gibi filtreleri kullanarak görüntü meta verilerine filtre uygulayabilirsiniz . PATH/ROW değerleri, Yörünge numarası, Bulut örtüsü vb. kriterlere göre filtreleme yapabilirsiniz.
* Tarihe göre filtrele : ee.Filter.date() gibi filtreleri kullanarak belirli bir tarih aralığındaki görüntüleri seçebilirsiniz.
* Konuma göre filtrele : ee.Filter.bounds() öğesini kullanarak bir sınırlayıcı çizim, konum veya geometri içeren görüntülerin alt kümesini seçebilirsiniz.


#### ImageCollection Üzerinde Hesaplama
Bir indeks hesaplama gibi bazı hesaplamaları birçok görüntüye uygulamak istiyorsanız, 'map()' kullanmalısınız.
Önce 1 görüntü alan ve o görüntü üzerinde hesaplamanın sonucunu döndüren bir fonksiyon tanımlarsınız. 
Ardından, 'map()' ile bu işlevi ImageCollection üzerinde yapabilirsiniz, bu da hesaplamanın sonuçlarıyla birlikte yeni bir ImageCollection ile sonuçlanır. 

Bu, aşina olduğunuz bir for döngüsüne benzer - ancak map() kullanmak , hesaplamanın paralel çalışmasına izin verir.


### FeatureCollection ile çalışma
FeatureCollection, ImageCollection benzer ancak görseller değil özellikler içerirler . 
Bir CBS'deki Vektör Katmanlarına eşdeğerdirler.
Filtreleme, sıralama ve oluşturma gibi tüm sette ek işlemleri etkinleştirmek için ilgili özellik grupları bu şeklinde birleştirilebilir.

#### Feature
Earth Engine'deki Feature, GeoJSON özelliği olarak tanımlanır. 
Spesifik olarak, bir Feature, bir nesneyi depolayan bir özelliğe ve diğer özelliklerin bir sözlüğünü depolayan bir 'geometry' özelliğe sahip bir nesnedir.

### Reducers
Earth Engine'de, kompozitler oluştururken, istatistik hesaplarken, regresyon analizi yaparken vb. sırasında 'reduce' işlemini çalıştırmanız gerekir. 

Earth Engine'de , görüntüler, ImageCollection, FeatureCollection, Liste, Sözlük vb. gibi birden çok değeri tutabilen tüm veri yapılarında çalışan 'reducer'ları destekler. 

### Time-Series Charts
Earth Engine API, Google Chart API'ye dayalı grafik işlevleri desteğiyle birlikte gelir. 
Burada bir zaman serisi grafiği oluşturmak için 'ui.Chart.image.series()' işlevini kullanıyoruz.


### Dışa Aktarma (Export)
Earth Engine, harici bir programda kullanılmak üzere hem vektör hem de tarama verilerinin dışa aktarılmasına olanak tanır. Vektör verileri a CSV veya a Shapefile olarak dışa aktarılabilirken, Raster'lar GeoTIFF olarak dışa aktarılabilir.
Dışa Aktarma işlemi tamamlandığında, belirtilen klasördeki Google Drive'ınıza her dışa aktarma görevi için bir GeoTiff dosyası eklenecektir.


#### Bir ImageCollection Dışa Aktarma (Export)
Earth Engine kullanıcıları tarafından en sık sorulan sorulardan biri şudur : Bir koleksiyondaki tüm görüntüleri nasıl indiririm ? 
Earth Engine API, tek bir görüntüyü dışa aktarmanıza izin verir, ancak görüntü koleksiyonunu dışa aktarmanıza izin vermez. ( Bunun gibi toplu dışa aktarma yapmanın önerilen yolu, Python API'sinin 'ee.batch.Export' işlevlerini kullanmak ve her görüntüyü yinelemek ve dışa aktarmak için bir Python for döngüsü kullanmaktır. )








## Kaynaklar
* https://earthengine.google.com/faq/
* https://developers.google.com/earth-engine/datasets/
* https://appliedsciences.nasa.gov/join-mission/training/english/arset-using-google-earth-engine-land-monitoring-applications
* https://courses.spatialthoughts.com/end-to-end-gee.html#exporting-data
