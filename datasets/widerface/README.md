# WIDER FACE 

Yüz tespiti için bir veri seti pose, scale, occlusion, expression, appearance ve illumination açısından değişikliğe sahip olmalıdır. Wider Face bu kriterler doğrultusundayüksek derecede değişikliğe sahiptir.Aynı zamanda veri seti 32,203 görüntü ve 393,703 etiketli yüzden oluşur.

Yüz algılmada yaygın olarak AFW, FDDB, Pascal Face veri kümeleride kullanılır. AFW; Flickr görüntüleri kullanılarak 473 etiketli yüze sahip 205 görüntüye sahiptir. Her yüz için açıklamalar sınırlayıcı kutu, 6 yer işareti ve poz açılarını içerir. FDDB; 2.845 görüntüden oluşan 5,171 yüze sahip  ve bu yüzlere ait ek açıklamalar içeren bir veri setidir. Pascal-Face; 851 görüntü ve 1.341 açıklamalı yüzden oluşur.
### Neden Diğer Veri Setleri Tercih Edilmedi?

AFW ve Pascal Face veri setleri yanlızca birkaç yüz görüntü içerir ve arkaplan karmaşası ve yüz görünümlerinde sınırlı sayıda farklılık vardır.

## Wider Face Veri Kümesi 

Wider Face veri seti Wider veri setinin bir alt kümesidir. Wider'daki görseller 3 adımda toplanmıştır;
1. Olay kategorileri, video olay analziyle ilgili yaklaşık 1000 kavram sağlayan Multimedya için Büyük Ölçekli Ontoloji(LSCOM) izlenerek tenımlanmış ve seçilmiştir.
2. Görseller Goggle ve Bing gibi arama motorları kullanılarak alınır ve her kategori için 1000-3000 arası görsel toplanır.
3. Tüm görseller manuel olarak incelenir ve insaan yüzü olmayan görseller filtrelenerek veriler temizlenir.Daha sonra yüz görünümünde büyük çeşitlilik sağlamak için her etkinlik kategorisindeki benzer görseller kaldırılır.

* NOT= Veri setindeki tanınabilir tüm yüzler için sınırlayıcı kutular etiketlenir. Sınırlayıcı kutuların alnı, çeneyi ve yanağı sıkı bir şekilde kapsaması gerekir.Eğer bir yüz tıkanmışsa (occlusion) tıkanma ölçeğine ilişkin bir tahminle sınırlayıcı kutu ile etiketlenir.

Wider Face veri seti 
 olay sınıfına göre düzenlenmiştir. Her olay sınıfı için tarining/validation/testing setleri %40/%10/%50 olarak seçilir.
 Training/Testing ikilisi için 2 senaryo mevcuttur;
 1. Senaryo-Ext: Bir face detector herhangi bir harici veri seti ile eğitilir ve Wider Face test bölümünde test edilir.
 2. Senaryo-Int: Bir face detector Wider Face tarining/validation bölümlerinde eğitilir ve Wider Face test bölümünde test edilir.

 ## Wider Face'in Özellikleri 

 * Wider Face diğer veri setlerine göre daha zorlu bir yüz algılama kriterine sahiptir.(Overall)
 * Büyük ve orta ölçekli yüzlerin tespit edilme oarnı %90'dan fazla ve küçük ölçekli yüzlerin tespit edilme oranı %30'un altındadır.(Scale)
 * Occlusion seviyesi arttıkça tespit edilme oranı azılır. Kısmi veya ağır kapanma olan yüzlerin tespit edilme oranları %8 ile %50 arasındadır.
 * Dönme veya eğim açısı 30 dereceden büyükse yüz atipik olarak değerlendirilir veya sapma 90 dereceden büyükse. Alışılmadık pozlara sahip yüzlerin tespit edilmesi çok daha zorludur.

Wider Face belirttiğim gibi 60 olay kategorisi içerir. Olayların yüz algılamaya etkisini belirlemek için scale, occlusion ve pose ile olayları kategorize ediyoruz. Bu sıralamaya göre olaylar 3 bölüme ayrılır; Kolay(41-60), Orta(21-40) ve Zor(1-20).

* NOT= Olay odaklı yapısı nedeniyle Wider Face veri kümesi , farklı arka planlara sahip çok sayıda sahneye sahiptir ve bu durum veri kümesini hem olumlu hem de olumsuz örneklerle iyi bir eğitim kaynağı olarak mümkün kılar.

## Nasıl İndirebilirim
http://shuoyang1213.me/WIDERFACE/  adresinden download kısmında bulunan training, validation, testing ve face annotations kısımlarını indirmemiz yeterli.
