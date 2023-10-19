# Tina Face:  

Tina  Face  temel  object  detection  uygulamalarında  kullanılan  yöntemlerin  face  detection 
uygulamalarında  da  kullanılabileceği  ve  bu  uygulamalarda  güçlü  fakat  basit  çözümler  olacağını 
savunarak oluşturulan bir face detection yöntemidir. 

## FPN Nedir?

  Birden fazla ölçekteki görüntülerin doğru ve hızlı bir şekilde işlenmesi için doğruluk ve hıx göz önünde bulundurularak hazırlanmış bir özellik çıkarıcıdır. 
  Object  detection için  normal  özellik piramidinden  daha kaliteli bilgilerle birden  fazla  özellik haritası katmanı oluşturur. (çok ölçekli özellik haritaları) 
  FPN aşağıdan yukarıya bir yol ve yukarıdan aşağı bir yoldan oluşur. 

    NOT:  Düşük seviyeli yapılardan oluşan görüntü katmanına daha yakın olan özellik haritaları, doğru nesne tespiti için etkili olmaz. 

    NOT: FPN, giriş olarak rastgele boyuttaki tek ölçekli görüntüyü alan ve tam evrişimli bir şekilde birden fazla düzeyde orantılı boyutlu özellik haritaları çıkaran bir özellik çıkarıcıdır. Omurga mimarisinden farklıdır. Boyun mimarisi olarak geçer genelde. 

## IoU Nedir?

  Intersection over Union : Nesne algılamayla ilgili uygulamalarda kullanılır. Amaç; Doğru çerçeve ve tahmin sonucu oluşan çerçeve tamamen örtüşene kadar; Yani IoU=1 olana kadar tahmini geliştirmeye devam etmektir.0 ve 1 arasında bir değere sahiptir

                IoU=Kesişme Alanı/Birleşme Alanı

## DCN Nedir?

  Temel  amacı  geleneksel  CNN'lerdeki  evrişim  işlemindeki  sert  ve  sabit  örüntü  eşleşmelerini geliştirmektir. 
  Geleneksel evrişim katmanları, görüntü üzerindeki özellikleri tek bir pencereden(kernel)  işler ve bu pencerenin  boyutu  her  katmanda  aynıdır.  Nesne  tespiti  işlemlerinde  nesneler  farklı  boyutlarda  ve şekillerde  olabileceği  ve  özellikle  kenarlarda  yer  aldığında  sınırlarda  bulunan  özellikleri  doğru  bir şekilde tespit etmek önemlidir. DCN bu tür zorluklara çözüm olmak için tasarlanmıştır. 
  DCN, geleneksel evrişim katmanlarına göre şu temel avantajlara sahiptir: 

   Deformable Convolution: DCN, evrişim işlemi sırasında kernelin her bir noktasını esnek hale getirir. Bu, nesnelerin kenarlarını veya dönüşlerini daha iyi algılamak için özellik haritasını daha dinamik bir şekilde incelemesine olanak tanır.

   Adaptive  Sampling:  DCN, pikselleri farklı ölçeklerde ve yüksekliklerde örneklemek için adaptif bir örnekleme mekanizması kullanır. Bu, nesnelerin daha iyi tespit edilmesini sağlar. 

   Uzaysal Duyarlılık: DCN, evrişim katmanlarının uzaysal duyarlılığını artırır ve böylece nesnelerin daha hassas konumlarını tespit etmeyi sağlar. 

## SGD Optimizasyonu Nedir?

  Amacı bir modelin kayıp fonksiyonunu (loss function)  minimize  etmek  için  model  parametrelerini güncellemektir. 
  Ana  avantajı;  Büyük  veri  seti  ve  büyük  model  parametrelerini  eğitirken  hesaplama  maliyetini düşürmesidir.

  ###  Çalışma Mantığı: 
    1.Başlangıçta,  modelin  parametrelerini  (ağırlıklarını)  rastgele  veya  belirli  bir  başlangıç  değeri  ile başlatın. 
    2.Eğitim  veri  kümesini  rastgele  karıştırın  veya  rasgele  örnekler  alın.  Bu,  modelin  her  bir  eğitim döneminde farklı örneklerle güncellenmesini sağlar. 
    3.Her bir eğitim örneği için aşağıdaki adımları izleyin: 
        a. Örnek üzerindeki tahmini sonuçları hesaplayın (ileri besleme - forward propagation). 
        b. Gerçek sonuçlarla tahminler arasındaki kaybı (loss) hesaplayın. 
        c. Kaybı minimize etmek için ağırlıkları güncellemek için gradyanı hesaplayın. 
        d. Gradyanı kullanarak ağırlıkları güncelleyin: 
            Yeni Ağırlık = Eski Ağırlık - (Öğrenme Hızı * Gradyan) 
    4.Belirli bir epoch (eğitim dönemi) boyunca bu işlemi veri kümesindeki tüm örnekler için tekrarlayın. Genellikle bir veri kümesinin tüm örnekleri bir defa geçtiğinde bir epoch tamamlanır. 
    5.Belirli bir sayıda epoch veya başka bir durum belirli bir kriteri karşılayana kadar bu işlemi tekrarlayın. Bu, modelin eğitim sürecini tamamlar. 

    NOT: Genellikle büyük veri kümeleri ve karmaşık modellerle çalışırken tercih edilir.

    NOT:  SGD'nin  ana  hiperparametreleri  arasında;  learning  late,  mini-batch  boyutu,  momentum  ve düzenleme terimleri gibi faktörler yer alır. 
  
  
 
 
 

  