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


## Dendrogram ( Öbek Ağacı )


![alt text](https://miro.medium.com/max/628/1*PvGL2AqONrf1NMYsvx7O1w.png))


Dendrogram, benzer veri kümeleri arasındaki ilişkileri veya hiyerarşik kümelenmeyi gösteren bir ağaç diyagramıdır. Kaç tane küme oluşturacağımız bilgisini verir. En uzun bacaktan çizilen yatay çizgi küme sayısını verir. Dendrogram şemasını yorumlarsak kümelenme şekli aşağıdaki gibidir.

E — F kümelenmiş (EF)
A — B kümelenmiş (AB)
D — EF kümelenmiş (DEF)
C — DEF kümelenmiş (CDEF)
AB —CDFE kümelenmiş (ABCDEF)


# csv dosyalarını okumak için
import pandas as pd

# 2 boyutlu grafik oluşturmak için
import matplotlib.pyplot as plt

# csv dosyamızı okuduk.
data = pd.read_csv('Iris.csv')

# Veriler
v = data.iloc[:,1:-1].values

# AgglomerativeClustering sınıfını import ettik
from sklearn.cluster import AgglomerativeClustering

# AgglomerativeClustering sınıfından bir nesne ürettik
# n_clusters = Ayıracağımız küme sayısı
# linkage ve affinity = mesafe ölçüm yöntemleri
# linkage ve affinity parametrelerinin değiştirilmesi başarı oranını etkiler.
ac = AgglomerativeClustering(n_clusters=3, affinity='euclidean',linkage='ward')

# Kümeleme ve tahmin işlemi yap
predict = ac.fit_predict(v)

# Dendogram grafiği gösterimi
import scipy.cluster.hierarchy as sch

# v = verilerimiz
# method = AgglomerativeClustering'in linkage parametresi ile aynı parametreyi veriyoruz. ( 'ward' )
dendrogram = sch.dendrogram(sch.linkage(v,method='ward'))
plt.show()

# Grafik şeklinde ekrana basmak için
plt.scatter(v[predict==0,0],v[predict==0,1],s=50,color='red')
plt.scatter(v[predict==1,0],v[predict==1,1],s=50,color='blue')
plt.scatter(v[predict==2,0],v[predict==2,1],s=50,color='green')
plt.title('Hierarchical Clustering Iris Dataset')

