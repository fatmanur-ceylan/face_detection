# Retina-Face
  Ele alınan konu face recognition, 2D face alignment ve 3D face reconstruction yüz lokalizasyon görevlerini ortak eğitim yoluyla bir çerçevede birleştirip birbirinden faydalanmalarını sağlamaktır.Face recognition ve 2D face alignment ile paralel bir eğitim gerçekleştirilerek 3D face reconstruction için oldukça sağlam bir model oluşturulmuştur.
  
## İzlenen Yaklaşım
  ### **3D Face Reconstruction** 

  Sabit üçgen topolojisi ile önceden tanımlanmş sabitsayıda N köşe belirleniyor.Bu köşelerin birleştirilmesi ile hizalanmış 3D face elde ediliyor.Bu işlem için köşelerin sınırlandırılması gerekiyor.Bunu için köşe kaybını kullanıyoruz.(2D => 3D)

    NOT=Sabit üçgen topolojisi ile yüzdeki her piksel, barisantrik koordinatlar ve üçgen indeksi tarafından indekslenir. Bu sayede 3D face ile piksel bazında bir uyum yakalanmış olur. Daha fazla köşe, ağı daha bilgilendirici ve pürüzsüz hale getirir.

  Bir yüzü 3D'den 2D'ye yansıtırken meydana gelen bilgi kaybı nedeniyle z koordinatlarını ve görünmeyen köşelerin x ve y koordinaatlarını tahmin etmek zorlaşır bunun önüne geçmek için kenar kaybını hesaplıyoruz.
  kenar kaybını ve köşe kaybını birleştirerek ağ regrasyon kaybı hesaplanıyor.

### **Multi-level Face Localisation**

  Training anchor için multi-task loss en aza indirilmelidir.
  3D ağları oluşturmak için ortografik projeksiyon kullanılıyor.Bu sebeple tüm köşeleri burun ucunun z koordinatı 0 olacak şekilde ayarlanır.Sonrasında z koordinatları anchor ölçeği ile normalleştiriliyor.

    NOT=Ortografik projeksiyon bir nesnenin üç boyutlu yapısını iki boyutlu bir görüntüye dönüştürmek için kullanılan bir projeksiyon yöntemidir. Ortografik projeksiyon, nesnenin uzaklığına bağlı olarak boyutları değişmeyen bir görüntü elde etmek için kullanılır.
    
    NOT=Daha anlamsal noktalrın yerelleştirilmesi, daha doğru kutu tahminine katkıda bulunacağı ve yüz algılama veri kümesindeki daha zorlu eğitim senaryoları daha sağlam nokta tahmini ile sonuçlanacağı için her görev diğer görevleerden yararlanabiliyor durumdadır.
    
  ### **Single-shot Multi-level Face Localisation**

  Model 3 ana bileşenden oluşur; Feature pyramid network, the context head module ve the cascade multi-task loss.
  Feature pyramid network giriş görüntülerini alır ve farklı ölçeklerde beş özellik haritası çıkarır.

    NOT= Beş özellik haritası göz merkezleri, Burun ucu ve ağız köşelerini içeren özellik haritası.

  Retina-Face P2'den P6'ya kadar olan feature pyramid düzeylerini kullanır.P2'den P5'e kadar yukarıdan aşağıya ve yanal bağlantılar kullanılarak karşılık gelen ResNet artık aşamasının (C2'den C5'e) çıktısından hesaplanır. P6 ise C5'te adım=2 olacak şekilde 3x3 evrişim yoluyla hesaplanır.

    NOT=P2'den P6'ya kadar olan feature pyramid düzeylerinde ölçeğe özgü anchor kullanılır.

    NOT= P2 daha fazla hesaplama süresi pahasına ve daha fazla yanlış pozitif riskiyle küçük anchorlar yerleştirilerek küçük yüzleri yakalamak için tasarlanmıştır.

    NOT= C1 ila C5, ImageNet-11k veri kümesi üzerinde önceden eğitilmiş bir sınıfandırma ağıdır.
  
  Context head module belirli bir ölçeğin özellik haritasını alır ve multi-task loss'u hesaplar.Birinci context head module, normal bağlantıdan sınırlayıcı kutuyu tahmin eder. İkinci context head module brirnci context head module tarafından oluşturulan regrasyonlu bağlantıyı kullanarak daha doğru bir sınırlayıcı kutu tahmin eder.

  The cascade multi-task loss yüz lokalizasyonunun performansını geliştirmek için multi-task loss ile kademeli regrasyon kullanılır.

  NOT=İlk head module için, Birleşim Üzerindeki Kesişme (IoU) 0,7'den büyük olduğunda anchorlar bir temel doğruluk kutusuyla ve IoU 0,3'ten küçük olduğunda arka planla eşleştirilir. İkinci kafa modülü için, IoU 0,5'ten büyük olduğunda anchorlar bir temel doğruluk kutusuyla ve IoU 0,4'ten küçük olduğunda arka planla eşleştirilir. Eşleşmeyen anchorlar eğitim sırasında göz ardı edilir.

 