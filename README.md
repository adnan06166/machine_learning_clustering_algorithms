# machine_learning_clustering_algorithms


# Hiyerarşik Kümeleme Algoritması Nedir?

![alt text](https://miro.medium.com/max/770/1*0BDVA8JPsSHivx7e6SEGtw.png)

Hiyerarşik kümeleme adındanda anlaşılacağı üzere bir kümeleme algoritmasıdır. Agglomerative ( Parçadan bütüne ) ve Divisive ( Bütünden parçaya ) olarak iki farklı varyasyonu vardır.

Agglomerative varyasyonunu anlatmaya çalışırsak ilk önce tüm veriler bir küme haline getirilir yani N tane eleman varsa N tane küme oluşur. Daha sonra birbirine mesafe olarak yakın olan kümeler birleşerek yeni bir küme oluşturur. Bu durum sistem kararlı oluncaya kadar devam eder. Divisive ise Agglomerative’ in tam tersidir. İlk başta tüm veriler tek bir küme oluşturulur. Daha sonra bu küme parçalanarak kümeleme işlemi yapılır.

Agglomerative ( Yığınsal ) hiyerarşik kümelemede mesafe hesaplamak için bir çok yol vardır. Dendrogram oluşturmada da kullanılırlar.

**Single Linkage** : İki küme arasındaki en yakın mesafeyi hesaplar.

**Complete Linkage**: İki küme arasındaki en uzak mesafeyi hesaplar.

**Average Linkage**: İki küme arasındaki ortalama mesafeyi hesaplar.

Bunların dışında ward, weighted, centroid ve median yöntemleri vardır. Seçilen yöntem sonucu etkiler.


