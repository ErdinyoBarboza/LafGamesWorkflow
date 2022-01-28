# Unity Style Guide

Bu makale, Unity'de bir proje yapısı ve komut dosyaları ve assetler için bir adlandırma kuralı kurmaya yönelik fikirler içerir. 

<a name="toc"></a>
## Table of Contents

> 1. [Giriş](#introduction)
> 1. [Proje Yapısı](#structure)
> 1. [Scriptler](#scripts)
> 1. [Asset Adlandırma Kuralları](#anc)
> 1. [Asset Workflows](#asset-workflows)

<a name="introduction"></a>
## 1. Introduction

### Sections

> 1.1 [Style](#style)

> 1.2 [Önemli Terminoloji](#importantterminology)

<a name="style"></a>
### 1.1 Style

#### Projenizin zaten bir stil kılavuzu varsa, onu takip etmelisiniz.
Bir proje üzerinde veya önceden var olan bir stil kılavuzuna sahip bir ekiple çalışıyorsanız, buna saygı gösterilmelidir. Mevcut bir stil kılavuzu ile bu kılavuz arasındaki herhangi bir tutarsızlık, mevcut stile uygun olmalıdır.

Bununla birlikte, stil kılavuzları yaşayan belgeler olmalıdır ve değişikliğin tüm kullanımlara fayda sağladığını düşünüyorsanız, bu kılavuzda olduğu gibi mevcut bir stil kılavuzunda stil kılavuzu değişiklikleri önermelisiniz.

> ##### *Stil üzerine tartışmalar anlamsızdır. Bir stil rehberi olmalı ve onu takip etmelisiniz.* 
> [_Rebecca Murphey_](https://rmurphey.com)

#### Herhangi bir projedeki tüm yapı, assetler ve kod, kaç kişi katkıda bulunursa bulunsun, tek bir kişinin oluşturduğu gibi görünmelidir.
Bir projeden diğerine geçmek, stil ve yapının yeniden öğrenilmesine neden olmamalıdır. Bir stil kılavuzuna uymak, gereksiz varsayımları ve belirsizlikleri ortadan kaldırır.

Ayrıca, stil hakkında düşünmeniz gerekmediğinden, talimatları takip etmeniz yeterli olduğundan, daha verimli oluşturma ve bakıma olanak tanır. Bu stil kılavuzu, en iyi uygulamalar göz önünde bulundurularak yazılmıştır; bu, bu stil kılavuzunu izleyerek, izlenmesi zor sorunları da en aza indireceğiniz anlamına gelir.

#### Arkadaşlar, arkadaşlarının kötü bir tarza sahip olmasına izin vermez.
Bir stil rehberine karşı çalışan veya stil rehberi olmayan birini görürseniz, onları düzeltmeye çalışın.

Bir ekip içinde çalışırken veya bir topluluk içinde tartışırken, insanlar tutarlı olduğunda yardım etmek ve yardım istemek çok daha kolaydır. Kimse birinin spagetti kodunu çözmeye yardım etmekten veya anlayamadığı adlara sahip assetlerle uğraşmaktan hoşlanmaz.

İşi farklı ama tutarlı ve aklı başında bir stil kılavuzuna uygun olan birine yardım ediyorsanız, ona uyum sağlamanız gerekir. Herhangi bir stil kılavuzuna uymuyorsa lütfen buraya yönlendirin. 

<a name="importantterminology"></a>
### 1.2 Önemli Terminoloji

<a name="terms-prefab"></a>
#### Prefabs
Unity, yeniden kullanılabilir bir Prefab olarak tüm bileşenleri, özellik değerleri ve alt GameObject'leri ile eksiksiz bir GameObject oluşturmanıza, yapılandırmanıza ve saklamanıza izin veren bir sistem için Prefab terimini kullanır. 

<a name="terms-level-map"></a>
#### Levels/Maps/Scene
Levellar, bazı kişilerin harita dediği veya Unity'nin Sahne dediği şeyi ifade eder. Bir Level, bir object koleksiyonu içerir. 

<a name="terms-serializable"></a>
#### Serializable
Serileştirilebilir olan değişkenler Unity'deki Inspector penceresinde gösterilir. Daha fazla bilgi için Unity'nin [Seri hale getirilebilir](https://docs.unity3d.com/Manual/script-Serialization.html) belgelerine bakın. 

<a name="terms-cases"></a>
#### Cases
Bir şeyleri adlandırmanın birkaç farklı yolu vardır. İşte bazı yaygın kasa türleri: 

> ##### PascalCase
> Baş harfler büyük ve boşluksuz, e.g. `DesertEagle`, `StyleGuide`, `ASeriesOfWords`.
> 
> ##### camelCase
> İlk harf küçük ancak sonraki bütün kelimeler büyük harfli ve boşluksuz, e.g. `desertEagle`, `styleGuide`, `aSeriesOfWords`.

>  ##### lowercase
> Bütün harfler küçük harf, e.g. `deserteagle`, 
>
> ##### Snake_case
> Büyük yada küçük harfi önemsemeden ancak boşlukları _ ile değiştir, e.g. `desert_Eagle`, `Style_Guide`, `a_Series_of_Words`.

**[⬆ Back to Top](#table-of-contents)**

<a name="structure"></a>
## 2. Proje Dizin Yapısı
Bir projenin dizin yapısı stili yasa olarak kabul edilmelidir. Asset adlandırma kuralları ve içerik dizini yapısı el ele gider ve herhangi birinin ihlali gereksiz kaosa neden olur.

Bu tarzda, asset türlerini klasörlerle gruplayan başka bir ortak yapı yerine, assetlerle çalışanlar için belirli bir türdeki assetlerı bulmak için Proje Penceresinin filtreleme ve arama yeteneklerine daha fazla dayanan bir yapı kullanacağız.

> Bir prefix [adlandırma kuralı](#asset-name-modifiers) kullanmak, klasörleri `Meshes`, `Textures`, ve `Materials` gibi benzer türdeki assetlerı içerecek şekilde kullanmak, varlık türlerinin her ikisi de zaten sıralanmış olduğundan gereksiz bir uygulamadır ve prefix kullanarak içerik tarayıcısında filtrelenebilir. 
<pre>
Assets
    <a name="#structure-developers">_Developers</a>(Use a `_`to keep this folder at the top)
        DeveloperName
            (Üzerinde çalışılan assetler)
    <a name="structure-top-level">ProjectName</a>
            Characters
            	Anakin
                CountDooku
            FX
                Vehicles
                    Abilities
                        IonCannon
                            (Particle Systems, Textures)
                Weapons
            Gameplay
                Characters
                Equipment
                Input
                Vehicles
                    Abilities
                    Air
                        TieFighter
                            (Models, Textures, Materials, Prefabs)
            <a name="#structure-levels">_Levels</a>
                Frontend
                Act1
                    Level1
            Lighting
                HDRI
                Lut
                Textures
            MaterialLibrary
            	Debug
            	Shaders
            Objects
                Architecture (Single use big objects)
                    DeathStar
                Props (Repeating objects to fill a level)
                    ObjectSets
                        DeathStar
            Scripts
                AI
                Gameplay
                    Input
                Tools
            Sound
                Characters
                Vehicles
                    TieFighter
                        Abilities
                            Afterburners
                Weapons
            UI
                Art
                    Buttons
                Resources
                    Fonts
    ExpansionPack (DLC)
    Plugins
    ThirdPartySDK  
</pre>




Bu yapılandırmayı kullanmamızın sebepleri aşağıdakilerdir.

### Sections

> 2.1 [Dosya İsimleri](#structure-folder-names)

> 2.2 [Üst Düzey Dosyalar](#structure-top-level)

> 2.3 [Developer Dosyaları](#structure-developers)

> 2.4 [Levellar](#levels)

> 2.5 [Define Ownership](#structure-ownership)

> 2.6 [`Assets` ve `AssetTypes`](#structure-assettypes)

> 2.7 [Büyük Setler](#structure-large-sets)

> 2.8 [Materyal Kütüphanesi](#structure-material-library)

> 2.9 [Scene Structure](#scene-structure)


<a name="2.1"></a>
<a name="structure-folder-names"><a>
### 2.1 Dosya İsimleri
Bunlar, içerik yapısındaki(content structure) herhangi bir klasörü adlandırmak için ortak kurallardır. 

<a name="2.1.1"></a>
#### Herzaman [PascalCase](#terms-cases) kullanın
PascalCase, bir isme büyük harfle başlamayı ifade eder ve ardından boşluk kullanmak yerine, takip eden her kelime büyük harfle başlar. Örneğin, "DesertEagle", "RocketPistol" ve "ASeriesOfWords". 

<a name="2.1.2"></a>
#### Asla boşluk kullanmayın
Bir önceki kuralın tekrarı olarak [2.1.1](#2.1.1), asla boşluk kullanmayın. Boşluklar, çeşitli mühendislik araçlarının ve toplu işlemlerin başarısız olmasına neden olabilir. İdeal olarak projenizin kökü de boşluk içermez ve 'C:\Kullanıcılar\Adım\Belgelerim\Unity Projeleri' yerine 'D:\Proje' gibi bir yerde bulunur. 

<a name="2.1.3"></a>
#### Unicode Karakter ve benzeri semboller kullanmayın
Oyun karakterlerinizden birinin adı 'Öykü' ise, klasör adı 'Oyku' olmalıdır. Unicode karakterler mühendislik araçları için [Boşluklar](#2.1.2)'dan daha kötü olabilir ve bazı parça uygulamaları da yollarda Unicode karakterleri desteklemez. 

Bununla ilgili olarak, projeniz ve bilgisayarınızın kullanıcı adı bir Unicode karaktere sahipse (yani adınız 'Öykü' ise), 'Belgelerim' klasörünüzde bulunan herhangi bir proje bu sorundan muzdarip olacaktır. Genellikle projenizi "D:\Project" gibi bir şeye taşımak bu gizemli sorunları çözecektir. 

"az", "AZ" ve "0-9" dışında "@", "-", "_", ",", "*" ve "#" gibi diğer karakterlerin kullanılması da beklenmeyen hatalara ve kaynak kontrolü programlarının kafasının karışmasına sebep olabilir ve bu yüzden önerilmez.
<a name="structure-no-empty-folders"></a>
#### Boş Dosya Bulunmaz
Kısacası, boş klasör bulunmamalıdır. İçerik tarayıcısının kullanımını zorlaştırırlar

İçerik tarayıcısında silemeyeceğiniz boş bir klasör olduğunu fark ederseniz, aşağıdakileri gerçekleştirmelisiniz:
1. Kaynak kontrolünü kullandığınızdan emin olun.
1. Diskteki klasöre gidin ve içindeki assetlerı silin.
1. Düzenleyiciyi kapatın.
1. Kaynak kontrol durumunuzun senkronize olduğundan emin olun (yani, Perforce kullanıyorsanız, içerik dizininizde bir Çevrimdışı Çalışmayı Uzlaştırın)
1. Düzenleyiciyi açın. Her şeyin hala beklendiği gibi çalıştığını onaylayın. Olmazsa, geri dönün, neyin yanlış gittiğini bulun ve tekrar deneyin.
1. Klasörün şimdi gitmiş olduğundan emin olun.
1. Değişiklikleri kaynak kontrolüne gönderin. 

<a name="2.2"></a>
<a name="structure-top-level"><a>
### 2.2 Projeye özel Assetler için Üst Düzey Klasör kullanın
Bir projenin tüm assetleri, projenin adını taşıyan bir klasörde bulunmalıdır. Örneğin, projenizin adı 'Generic Shooter' ise, içeriğinin _tümü_ 'Assets/GenericShooter'da bulunmalıdır. 

> `Developer` klasörü, projenizin dayandığı assetler için değildir ve bu nedenle projeye özel değildir. Bununla ilgili ayrıntılar için [Developer Klasörleri](#2.3) bölümüne bakın. 

Bu yaklaşımın birden çok nedeni vardır. 

<a name="2.2.1"></a>
#### Global Assetlere Hayır
Genellikle kod stili kılavuzlarında, global ad alanını kirletmemeniz gerektiği yazılır ve bu da aynı prensibi izler. Assetlerin bir proje klasörünün dışında var olmasına izin verildiğinde, bir klasörde olmayan assetler, assetleri organize etmeme gibi kötü davranışı teşvik ettiği için katı bir yapı düzenini uygulamak genellikle çok daha zor hale gelir.

Her varlığın bir amacı olmalıdır, aksi takdirde bir projeye ait değildir. Bir varlık deneysel bir testse ve proje tarafından kullanılmayacaksa, bir [`Developer`](#2.3) klasörüne konmalıdır. 

<a name="2.2.2"></a>
#### Migration Çakışmalarını Azaltın
Birden fazla proje üzerinde çalışırken, her ikisi için de faydalı bir şey yapılmışsa, bir ekibin assetleri bir projeden diğerine kopyalaması yaygındır.

Projeye özel tüm assetlerı üst düzey bir klasöre yerleştirerek, bu assetlerı yeni bir projeye aktarırken geçiş çakışması olasılığını azaltırsınız.

<a name="2.2.2e1"></a>
##### Master Material Örneği
Örneğin, bir projede başka bir projede kullanmak istediğiniz bir ana malzeme oluşturduğunuzu ve bu varlığı başka bir projeye taşıdığınızı varsayalım. Bu varlık bir üst düzey klasörde değilse, 'Assets/MaterialLibrary/M_Master' gibi bir ada sahip olabilir. Hedef projede zaten bir ana malzeme yoksa, bu sorunsuz çalışmalıdır.

Projelerden biri veya her ikisi üzerinde çalışma ilerledikçe, normal gelişim süreci nedeniyle ilgili ana materyalleri kendi özel projelerine uygun hale getirilmek üzere değişebilir.

Sorun, örneğin bir proje için bir sanatçı, güzel bir genel modüler static mesh kümesi oluşturduğunda ve birisi bu static mesh kümesini ikinci projeye dahil etmek istediğinde ortaya çıkıyor. assetlerı oluşturan sanatçı, talimat verildiği şekilde 'Assets/MaterialLibrary/M_Master'a dayalı malzeme örnekleri kullandıysa, bir taşıma gerçekleştirildiğinde, daha önce taşınan 'Assets/MaterialLibrary/M_Master' varlığı için büyük bir çakışma olasılığı vardır. .

Bu sorunu tahmin etmek zor ve hesaba katmak zor olabilir. static meshları taşıyan kişi, her iki projenin ana malzemesinin geliştirilmesine aşina olan aynı kişi olmayabilir ve söz konusu static meshların, daha sonra ana malzemeye dayanan maddi örneklere dayandığının farkında bile olmayabilirler. Ancak Migrate aracı, tüm bağımlılık zincirinin çalışmasını gerektirir ve bu nedenle, bu assetlerı diğer projeye kopyalarken 'Assets/MaterialLibrary/M_Master'ı almaya zorlanacak ve mevcut varlığın üzerine yazacaktır.

Bu noktada, her iki proje için ana malzemeler _herhangi bir şekilde_ uyumsuzsa, bir proje için tüm malzeme kitaplığının yanı sıra halihazırda taşınmış olabilecek diğer bağımlılıkları bozma riskiyle karşı karşıya kalırsınız, çünkü assetler içinde depolanmamıştır. üst düzey bir klasör. static meshların basit geçişi artık çok çirkin bir görev hale gelir.

<a name="2.2.3"></a>
#### Samplelar, Templatelar ve 3rd taraf Contentler Risksiz Hale Gelir
[2.2.2](#2.2.2)'ye bir uzantı olarak, projenizin en üst düzey klasörü benzersiz bir şekilde adlandırılmamış ise ve bir ekip üyesi sample, template veya bir üçüncü taraftan satın aldığı assetleri eklemeye karar verirse, bu yeni varlıkların projeye müdahale etmeyeceği garanti edilir

[Üst düzey klasör kuralına](#2.2) tam olarak uyması için 3. taraf içeriğine güvenemezsiniz. İçeriğinin çoğunluğu üst düzey bir klasörde bulunan, ancak muhtemelen Unity örnek içeriğinin yanı sıra genel "Assets" klasörünü kirleten düzey dosyalarına sahip birçok varlık vardır.

[2.2](#2.2)'ye uyarken, yaşayabileceğiniz en kötü 3. taraf çatışması, iki 3. taraf varlığının her ikisinin de aynı örnek içeriğe sahip olmasıdır. Tüm varlıklarınız, klasörünüze taşımış olabileceğiniz örnek içerik de dahil olmak üzere projeye özel bir klasördeyse, projeniz asla bozulmaz.

#### DLC, alt projeler ve yamalar kolayca güncellenir 
Projeniz DLC'yi yayınlamayı planlıyorsa veya bununla ilişkili birden fazla alt projeye sahipse, taşınabilecek veya bir yapı içinde pişirilmeyecekse, bu projelerle ilgili varlıkların kendi ayrı üst düzey içerik klasörleri olmalıdır. Bu, DLC'yi ana proje içeriğinden ayrı olarak çok daha kolay hale getirir. Alt projeler de minimum çabayla içeri ve dışarı taşınabilir. Bir varlığın malzemesini değiştirmeniz veya bir yamada bazı çok özel varlık geçersiz kılma davranışı eklemeniz gerekiyorsa, bu değişiklikleri kolayca bir yama klasörüne koyabilir ve çekirdek projeyi bozma şansı olmadan güvenle çalışabilirsiniz. 

<a name="2.3"></a>
<a name="structure-developers"></a>
### 2.3 Lokal testler için Developer Dosyasını kullanın
Bir projenin geliştirilmesi sırasında, ekip üyelerinin çekirdek projeyi riske atmadan özgürce deney yapabilecekleri bir tür "sandbox"a sahip olmaları çok yaygındır. Bu çalışma devam ediyor olabileceğinden, bu ekip üyeleri varlıklarını bir projenin kaynak kontrol sunucusuna koymak isteyebilirler. Tüm ekipler Geliştirici klasörlerinin kullanılmasını gerektirmez, ancak bunları kullananlar genellikle kaynak denetimine gönderilen varlıklarla ilgili ortak bir sorunla karşılaşır. 

Bir ekip üyesinin, kullanıma hazır olmayan varlıkları yanlışlıkla kullanması çok kolaydır ve bu varlıklar kaldırıldığında sorunlara neden olur. Örneğin, bir sanatçı modüler bir statik ağ kümesi üzerinde yineleniyor olabilir ve hala boyutlandırmalarını ve ızgara yakalamalarını doğru hale getirmek için çalışıyor olabilir. Bir dünya oluşturucu bu varlıkları ana proje klasöründe görürse, inanılmaz bir değişime ve/veya kaldırılmaya tabi olabileceklerini bilmeden bunları bir düzeyde kullanabilir. Bu, ekipteki herkesin çözmek için büyük miktarlarda yeniden çalışmasına neden olur.

Bu modüler varlıklar bir Geliştirici klasörüne yerleştirildiyse, dünya oluşturucunun bunları kullanmak için hiçbir nedeni olmamalıydı ve tüm sorun asla olmayacaktı.

Varlıklar kullanıma hazır olduğunda, bir sanatçının varlıkları projeye özel klasöre taşıması yeterlidir. Bu aslında varlıkları deneyselden üretime hazır hale taşımaktır.


<a name="levels"></a>
### 2.4 Bütün [Scene](#terms-level-map) Dosyaları, Levels denen bir dosyanın içinde olmalıdır
Seviye dosyaları inanılmaz derecede özeldir ve özellikle alt seviyeler veya akış seviyeleri ile çalışıyorlarsa, her projenin kendi harita adlandırma sistemine sahip olması yaygındır. Belirli bir proje için hangi harita organizasyonu sistemi mevcut olursa olsun, tüm seviyeler 'Assets/ProjectNameName/Levels'a ait olmalıdır.

Birine, nerede olduğunu açıklamak zorunda kalmadan belirli bir haritayı açmasını söyleyebilmek, büyük bir zaman tasarrufu ve genel 'yaşam kalitesi' iyileştirmesidir. Seviyelerin 'Levels/Campaign1/' veya 'Levels/Arenas' gibi 'Levels' alt klasörlerinde olması yaygındır, ancak buradaki en önemli şey hepsinin 'Assets/ProjectName/Levels' içinde bulunmasıdır. .

Bu aynı zamanda mühendisler için pişirme işini de kolaylaştırır. Onlar için rastgele klasörleri kazmak zorundalarsa, bir derleme işlemi için seviye atlamaları son derece sinir bozucu olabilir. Bir takımın seviyeleri tek bir yerdeyse, bir yapıda yanlışlıkla bir harita pişirmemek çok daha zordur. Ayrıca, aydınlatma oluşturma komut dosyalarının yanı sıra QA süreçlerini de basitleştirir.

<a name="2.5"></a>
<a name="structure-ownership"></a>
### 2.5 Zone/Asset/Feature'ları Sahiplenin
Birden fazla kişiden oluşan ekiplerde, zone/assets/featureların sahipliğini tanımlayın. Sahneler veya hazır yapılar gibi bazı varlıklar, birden fazla kişi tarafından yapılan eşzamanlı değişiklikleri çok iyi işlemez ve çatışma yaratır. Belirli bir varlığı değiştirebilecek (veya değiştirme hakkı verebilecek) tek bir kişiye sahip olmak, bu sorunun önlenmesine yardımcı olur. 

<a name="2.6"></a>
<a name="structure-assettypes"></a>
### 2.6 `Assets` veya `AssetTypes` diye dosyalar açmayın

<a name="2.6.1"></a>
#### 'Assets' adlı bir klasör oluşturmak gereksizdir. 
Bütün assetler zaten assettir.

<a name="2.6.2"></a>
#### `Meshes`, `Textures`, veya `Materials` diye dosyalar açmak gereksizdir.
Tüm varlık adları, varlık türleri göz önünde bulundurularak adlandırılır. Bu klasörler yalnızca fazla bilgi sunar ve bu klasörlerin kullanımı, Content Browser'ın sağladığı sağlam ve kullanımı kolay filtreleme sistemi ile kolayca değiştirilebilir.

`Environment/Rocks/` içinde yalnızca static mesh görüntülemek ister misiniz? Sadece  Static Mesh filtresini açın. Tüm varlıklar doğru şekilde adlandırılırsa, öneklerden bağımsız olarak alfabetik sırayla da sıralanırlar. Hem  Static Mesh hem de Skeletal Meshleri görüntülemek ister misiniz? Her iki filtreyi de açmanız yeterlidir. bu, İçerik Tarayıcının ağaç görünümünde potansiyel olarak 'Control-Click' ile iki klasör seçme ihtiyacını ortadan kaldırır.

> Bu aynı zamanda bir varlığın tam yol adını çok az fayda sağlayacak şekilde genişletir. Statik bir mesh için "SM_" öneki yalnızca üç karakterdir, "Meshes/" ise yedi karakterdir.

Bunu yapmamak aynı zamanda birisinin 'Materials' klasörüne statik bir mesh veya textüre koymasının kaçınılmazlığını da önler.

<a name="2.7"></a>
<a name="structure-large-sets"></a>
### 2.7 Aşırı Büyük Asset Setleri kendilerine ait Dosya Layoutuna sahip olur

Bu kural [2.6](#2.6)nın uygulanmadığı yerlerden biridir.

Her bir assetin benzersiz bir amacı olduğu, çok sayıda ilgili dosya içeren belirli asset türleri vardır. En yaygın ikisi Animasyon ve Ses assetleridir. Eğer bu varlıkların 15'ten fazlasına sahipseniz, birlikte olmaları gerekir.

Örneğin, birden çok karakter arasında paylaşılan animasyonlar "Karakterler/Ortak/Animasyonlar" içinde yer almalıdır ve "Lokomosyon" veya "Sinematik" gibi alt klasörleri olabilir.

> Bu, textürler ve malzemeler gibi varlıklar için geçerli değildir. Çok miktarda kaya varsa, bir 'Kayalar' klasörünün büyük miktarda dokuya sahip olması yaygındır, ancak bu dokular genellikle yalnızca birkaç belirli kaya ile ilgilidir ve uygun şekilde adlandırılmalıdır. Bu dokular bir [Malzeme Kitaplığının](#2.8) parçası olsa bile.

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `MaterialLibrary`

Projeniz ana materialler, sub materialler veya assetlerin herhangi bir alt grubuna ait olmayan herhangi bir yeniden kullanılabilir malzeme veya textürden yararlanıyorsa, bu assetler `Assets/ProjectName/MaterialLibrary`de bulunmalıdır.

Bu şekilde tüm 'global' materyallerin yaşayacak bir yeri olur ve kolayca bulunur.

> Bu aynı zamanda bir proje içinde 'yalnızca materyal instanceları kullanın' politikasının uygulanmasını inanılmaz derecede kolaylaştırır. Tüm sanatçılar ve assetler malzeme instanceları kullanıyorsa, sadece standard materyal assetleri bu klasördedir. `MaterialLibrary` olmayan herhangi bir klasörde temel malzemeleri arayarak bunu kolayca doğrulayabilirsiniz.

`MaterialLibrary` tamamen malzemelerden oluşmak zorunda değildir. Paylaşılan yardımcı dokular, malzeme işlevleri ve bu nitelikteki diğer şeyler burada da amaçlarını belirleyen klasörler içinde saklanmalıdır. Örneğin, genel noise dokuları `MaterialLibrary/Utility` içinde bulunmalıdır.

Herhangi bir test veya hata ayıklama materyali "MaterialLibrary/Debug" içinde olmalıdır. Bu, hata ayıklama malzemelerinin sevkıyattan önce bir projeden kolayca çıkarılmasını sağlar ve referans hataları gösteriliyorsa üretim varlıklarının bunları kullanıp kullanmadığını inanılmaz derecede belirgin hale getirir.

<a name="2.9"></a>
<a name="scene-structure"></a>
## 2.9 Scene Structure
Proje hiyerarşisinin yanında sahne hiyerarşisi de var. Daha önce olduğu gibi, size bir şablon sunacağız. İhtiyaçlarınıza göre ayarlayabilirsiniz. 
Sahne klasörleri olarak adlandırılmış boş oyun nesnelerini kullanın.

<pre>
Debug
Management
UI
Cameras
Lights
World
    Terrain
    Props
Gameplay
	Actors
	Items
_Dynamic
</pre>

- Tüm boş nesneler, varsayılan döndürme ve ölçekleme ile 0,0,0'da bulunmalıdır.
- Yalnızca scriptleri sahneye getirme amaçlı olan boş nesneler için prefix olarak “@” kullanın – ör. @Cheats
- Runtime'da bir nesneyi başlatırken, onu _Dynamic içine koyduğunuzdan emin olun - hiyerarşinizin kökünü kirletmeyin, aksi takdirde gezinmeyi zor bulursunuz.
**[⬆ Back to Top](#table-of-contents)**

<a name="scripts"></a>

## 3. Scripts

Bu bölüm, C# sınıflarına ve içlerine odaklanacaktır. Mümkün olduğunda, Microsoft'un C# stil kuralları standardına uyunuz. 
### Sections
> 3.1 [Class Organization](#classorganization)

> 3.2 [Compiling](#compiling)

> 3.3 [Variables](#variables)

> 3.4 [Functions](#functions)

<a name="classorganization"></a>
### 3.1 Class Organizasyonu
Birden çok internal classa izin verilmesine rağmen, kaynak dosyalarda yalnızca bir public type olmalıdır.

Kaynak dosyalara, dosyadaki public classın adı verilmelidir.

Açıkça tanımlanmış bir yapı ile Namespace/Ad alanlarını düzenleyin, 

Class memberları should be alfabetik olmalı, ve bölümlere gruplandırılmalıdır:
* Constant Fields
* Static Fields
* Fields
* Constructors
* Properties
* Events / Delegates
* LifeCycle Methods (Awake, OnEnable, OnDisable, OnDestroy)
* Public Methods
* Private Methods
* Nested types

Bu grupların içi ise accesse göre sıralandırılmalıdır:
* public
* internal
* protected
* private
```
namespace ProjectName
{
	/// <summary>  
	/// Brief summary of what the class does
	/// </summary>
    public class Account
    {
      #region Fields
      
      [Tooltip("Public variables set in the Inspector, should have a Tooltip")]
      public static string BankName;
      
	  /// <summary>  
	  /// They should also have a summary
	  /// </summary>
      public static decimal Reserves;
 
	  public string BankName;
	  public const string ShippingType = "DropShip";
	  
	  private float _timeToDie;
	  
	  #endregion
	  
	  #region Properties
	  
      public string Number {get; set;}
      public DateTime DateOpened {get; set;}
      public DateTime DateClosed {get; set;}
      public decimal Balance {get; set;}
            
	  #endregion
	 
	  #region LifeCycle
	  
      public Awake()
      {
        // ...
      }
      
      #endregion
	  #region Public Methods
	  
      public AddObjectToBank()
      {
        // ...
      }
      
      #endregion
    }
}
```

#### Script Templates
Biraz zaman kazanmak için, ad alanını ve bölgeleri vb. otomatik olarak ayarlamak için Unity'nin default script template'ının üzerine kendinizinkini yazabilirsiniz. Bunu şu articledan öğrenebilirsiniz: [support](https://support.unity3d.com/hc/en-us/articles/210223733-How-to-customize-Unity-script-templates)

<a name="namespace"></a>
#### Namespace
Sınıflar/enum/arayüz/vb kapsamınızın diğer ad alanlarından veya genel ad alanından mevcut olanlarla çakışmayacağından emin olmak için bir ad alanı kullanın. Proje, içe aktarılan Üçüncü Taraf varlıklarıyla çakışmaları önlemek için en azından Ad Alanı için proje adını kullanmalıdır.

#### Tüm Public İşlevlerinin Bir Özeti Olmalıdır
 
Kısacası, Public'e access modifier'ı olan herhangibir functionun summary/özeti olmalıdır.

```
/// <summary>
/// Fire a gun
/// </summary>
public void Fire()
{
// Fire the gun.
}
```

#### Foldout Groups
Bir sınıfın yalnızca az sayıda değişkeni varsa, Katlamalı Gruplar/Foldout Gruplar gerekli değildir.

If a class has a moderate amount of variables (5-10), all [Serializable](#serializable) variables should have a non-default Foldout Group assigned. A common category is `Config`.

Unity'de folder grupları yapmanın 2 yolu vardır.

* Bunun ilk yolu Main classın içinde `[Serializable] public Class`  define etmektir ancak bu performansa etki eder. Bu aynı variable isminin paylaşılmasına izin verir.
* İkinci yol ise [Odin Inspector](https://odininspector.com/) tarzı üçüncül parti program kullanmaktır.

```
[[Serializable](https://docs.unity3d.com/ScriptReference/Serializable.html)]
public struct PlayerStats
	{
        public int MovementSpeed;
    }
    
[FoldoutGroup("Interactable")]
public int MovementSpeed = 1;
```

#### Commenting
Comments should be used to describe intention, algorithmic overview, and/or logical flow.
It would be ideal if from reading the comments alone someone other than the author could understand a function’s intended behavior and general operation.

While there are no minimum comment requirements and certainly some very small routines need no commenting at all, it is hoped that most routines will have comments reflecting the programmer’s intent and approach.

##### Comment Style
Place the comment on a separate line, not at the end of a line of code.

Begin comment text with an uppercase letter.

End comment text with a period.

Insert one space between the comment delimiter (//) and the comment text, as shown in the following example.

The // (two slashes) style of comment tags should be used in most situations. Where ever possible, place comments above the code instead of beside it. Here are some examples:
```
        // Sample comment above a variable.
        private int _myInt = 5;
```

#### Regions
The `#region` directive enables you to collapse and hide sections of code in C# files. The ability to hide code selectively makes your files more manageable and easier to read. 
```
#region "This is the code to be collapsed"
    Private components As System.ComponentModel.Container
#endregion
```

#### Spacing
Do use a single space after a comma between function arguments.

Example: `Console.In.Read(myChar, 0, 1);`
* Do not use a space after the parenthesis and function arguments.
* Do not use spaces between a function name and parenthesis.
* Do not use spaces inside brackets.
<a name="3.1"></a>
<a name="compiling"></a>
### 3.2 Compiling
All scripts should compile with zero warnings and zero errors. You should fix script warnings and errors immediately as they can quickly cascade into very scary unexpected behavior.

Do *not* submit broken scripts to source control. If you must store them on source control, shelve them instead.

### 3.3 Variables
The words `variable` and `property` may be used interchangeably.

#### Variable Naming

##### Nouns
All non-boolean variable names must be clear, unambiguous, and descriptive nouns. 

##### Case
All variables use PascalCase unless marked as [private](#privatevariables) which use camelCase. 

Use PascalCase for abbreviations of 4 characters or more (3 chars are both uppercase).

##### Considered Context
All variable names must not be redundant with their context as all variable references in the class will always have context.

###### Considered Context Examples:
Consider a Class called `PlayerCharacter`.

**Kötü**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

All of these variables are named redundantly. It is implied that the variable is representative of the `PlayerCharacter` it belongs to because it is `PlayerCharacter` that is defining these variables.

**İyi**

* `Score`
* `Kills`
* `TargetPlayer`
* `Name`
* `Skills`
* `Skin`

#### Variable Access Level
In C#, variables have a concept of access level. Public means any code outside the class can access the variable. Protected means only the class and any child classes can access this variable internally. Private means only this class and no child classes can access this variable.
Variables should only be made public if necessary.

Prefer to use the attribute `[SerializeField]` instead of making a variable public.

##### Local Variables
Local variables should use camelCase.

###### Implicitly Typed Local Variables
Use implicit typing for local variables when the type of the variable is obvious from the right side of the assignment, or when the precise type is not important.
```
var var1 = "This is clearly a string.";
var var2 = 27;
var var3 = Convert.ToInt32(Console.ReadLine());
// Also used in for loops
for (var i = 0; i < bountyHunterFleets.Length; ++i) {};
```

Do not use var when the type is not apparent from the right side of the assignment.
Example
```
int var4 = ExampleClass.ResultSoFar();
```

<a name="privatevariables"></a>
##### Private Variables
Private variables should have a prefix with a underscore `_myVariable` and use camelCase.

Unless it is known that a variable should only be accessed within the class it is defined and never a child class, do not mark variables as private. Until variables are able to be marked `protected`, reserve private for when you absolutely know you want to restrict child class usage.

##### Do _Not_ use Hungarian notation
Do _not_ use Hungarian notation or any other type identification in identifiers
```
// Correct
int counter;
string name;
 
// Avoid
int iCounter;
string strName;
```

#### Variables accessible in the Editor

##### Tooltips 
All [Serializable](#serializable) variables should have a description in their `[Tooltip]` fields that explains how changing this value affects the behavior of the script.

##### Variable Slider And Value Ranges
All [Serializable](#serializable) variables should make use of slider and value ranges if there is ever a value that a variable should _not_ be set to.

Example: A script that generates fence posts might have an editable variable named `PostsCount` and a value of -1 would not make any sense. Use the range fields `[Range(min, max)]` to mark 0 as a minimum.

If an editable variable is used in a Construction Script, it should have a reasonable Slider Range defined so that someone can not accidentally assign it a large value that could crash the editor.

A Value Range only needs to be defined if the bounds of a value are known. While a Slider Range prevents accidental large number inputs, an undefined Value Range allows a user to specify a value outside the Slider Range that may be considered 'dangerous' but still valid.

#### Variable Types

##### Booleans

###### Boolean Prefix
Bütün Booleanlar PascalCase'te yazılmalı ve bir prefix kullanmalıdır.
Örnek: `isDead` ve `hasItem` kullanın, `Dead` ve `Item` **kullanmayın**.

###### Boolean Names
All booleans should be named as descriptive adjectives when possible if representing general information.

Try to not use verbs such as `isRunning`. Verbs tend to lead to complex states.

###### Boolean Complex States
Do not use booleans to represent complex and/or dependent states. This makes state adding and removing complex and no longer easily readable. Use an enumeration instead.

Example: When defining a weapon, do **not** use `isReloading` and `isEquipping` if a weapon can't be both reloading and equipping. Define an enumeration named `WeaponState` and use a variable with this type named `WeaponState` instead. This makes it far easier to add new states to weapons.

##### Enums
Enums use PascalCase and use singular names for enums and their values. Exception: bit field enums should be plural. Enums can be placed outside the class space to provide global access.

Example: 
```
public enum WeaponType
{
    Knife,
    Gun
}

// Enum can have multiple values
[Flags]
public enum Dockings
{
	None = 0,
	Top = 1,
}

public WeaponType Weapon
```

##### Arrays
Arrays follow the same naming rules as above, but should be named as a plural noun.

Example: Use `Targets`, `Hats`, and `EnemyPlayers`, not `TargetList`, `HatArray`, `EnemyPlayerArray`.

##### Interfaces
Interfaceler büyük harf `I` ile başlayıp sonrasında PascalCase ile devam eder.

Example: ```public interface ICanEat { }```

<a name="functions"></a>
### 3.4 Functions, Events, and Event Dispatchers
This section describes how you should author functions, events, and event dispatchers. Everything that applies to functions also applies to events, unless otherwise noted.

#### Function Naming
The naming of functions, events, and event dispatchers is critically important. Based on the name alone, certain assumptions can be made about functions. For example:

* Saf bir fonksiyon mu?
* State Information alıyor mu?
* Handler mı?
* Amacı nedir?

These questions and more can all be answered when functions are named appropriately.

<a name="function-verbrule"></a>
#### Bütün Functionlar Fiil Olmalıdır
All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should start with verbs. They should be worded in the present tense whenever possible. They should also have some context as to what they are doing.

İyi örnekler:

* `Fire` - Character / Weapon classı ise iyi bir örnek çünkü, konuyla alakalı. Barrel / Grass / ve benzeri belirsiz classlar için kötü bir örnek.
* `Jump` - Characater classı ise iyi bir örnek, ancak değil ise belirsiz.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" bir fiildir.](http://writingexplained.org/is-is-a-verb)

Kötü örnekler:

* `Dead` - Dead mi? Yoksa Öldürme mi?
* `Rock`
* `ProcessData` - Belirsiz, bu kelimeler hiçbir şey ifade etmiyor.
* `PlayerState` - İsimler belirsizdir.
* `Color` - Bağlamsız bir fiil, veya belirsiz bir isim .

#### Bool Fonksiyonları Soru Sormalı
State değiştirmeyen, object modifiye etmeyen, sadece informasyon, state yada yes/no value'su hesaplayan fuunctionlar soru sormalıdır.
Yine [fiil kuralı](#function-verbrule)nı kullanmalıdır.

Soru sormazsanız functionunuz başka tipler ile karıştırılır.

İyi örnekler:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" bir fiildir.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was", "be"nin geçmiş zamanlı çekimidir.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) 'önceki frame' yada 'önceki state' ile ilgili durumlarda "was" kullanın.
* `CanReload` - ["Can" bir fiildir.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Kötü örnekler:

* `Fire` - Ateş mi yapsın? Yanıyor mu? Yanacak mı?
* `OnFire` - Event Dispatcher ile karıştırılabilir.
* `Dead` - Öldü mü? Ölüleşecek mi?
* `Visibility` - Visible mı? Visibility ayarı mı?

#### Event Handlers ve Dispatchers `On` İle Başlamalı
Event handlelayıcı veya event dispatchleyen herhangibir function `On` ile başlamalı ve [fiil kurallarını](#function-verbrule) takip etmelidir.

İyi örnekler:

* `OnDeath` - Yaygın bir örnek
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Kötü örnekler:

* `OnData`
* `OnTarget`

**[⬆ Back to Top](#table-of-contents)**
<a name="anc"></a>
<a name="4"></a>

## 4. Asset İsimlendirme Kuralları
Adlandırma kuralları kanun olarak kabul edilmelidir. Bir adlandırma kuralına uyan bir proje, assetlerinin inanılmaz bir kolaylıkla yönetilmesini, aranmasını, ayrıştırılmasını ve sürdürülmesini sağlayabilir.

Çoğu şeyin önüne, genellikle varlık türünün bir kısaltması olan önek eklenir ve ardından bir alt çizgi gelir.

**Assetler [PascalCase](#cases) Kullanır**

<a name="base-asset-name"></a>
<a name="4.1"></a>
### 4.1 Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`
Bütün assetlerin bir _Base Asset Name_'e sahip olması lazım. Temel Varlık Adı, ilgili varlıkların mantıksal bir gruplamasını temsil eder. Bu mantıksal grubun parçası olan herhangi bir varlık `Prefix_BaseAssetName_Variant_Suffix` standardını takip etmelidir. 

`Prefix_BaseAssetName_Variant_Suffix` kalıbını akılda tutmak ve sağduyuyu kullanmak, iyi varlık adlarını garanti etmek için genellikle yeterlidir. İşte her bir elementle ilgili bazı ayrıntılı kurallar.

`Prefix` ve `Suffix`, aşağıdaki [Asset Adı Modifiyeleri](#asset-name-modifiers) tabloları aracılığıyla varlık türüne göre belirlenecektir.

`BaseAssetName`, bu asset grubunun bağlamıyla ilgili kısa ve kolayca tanınabilir bir adla belirlenmelidir. Örneğin, Bob adında bir karakteriniz olsaydı, Bob'un tüm assetlerinin `BaseAssetName`i `Bob` olurdu

Varlıkların benzersiz ve belirli varyasyonları için, "Varyant", bir varlığın temel adının bir alt kümesi olan varlıkların mantıksal gruplandırmasını temsil eden kısa ve kolayca tanınabilir bir addır. Örneğin, Bob'un birden fazla dış görünümü varsa, bu dış görünümler yine de "TemelAssetName" olarak "Bob"u kullanmalı, ancak tanınabilir bir "Varyant" içermelidir. Bir 'Evil' dış görünümü, 'Bob_Evil' olarak anılacaktır ve bir 'Retro' dış görünümü, 'Bob_Retro' olarak anılacaktır.

Varlıkların benzersiz ancak genel varyasyonları için "Varyant", "01" ile başlayan iki basamaklı bir sayıdır. Örneğin, sıradan olmayan kayalar üreten bir ortam sanatçınız varsa, bunlar 'Rock_01', 'Rock_02', 'Rock_03' vb. olarak adlandırılır. Nadir istisnalar dışında, asla üç basamaklı bir değişken numarasına ihtiyaç duymamalısınız. 100'den fazla varlığınız varsa, bunları farklı temel adlarla veya birden çok varyant adı kullanarak düzenlemeyi düşünmelisiniz.

Varlık varyantlarınızın nasıl yapıldığına bağlı olarak varyant adlarını birlikte zincirleyebilirsiniz. Örneğin, bir Arch Viz projesi için döşeme varlıkları oluşturuyorsanız, 'Flooring_Marble_01', 'Flooring_Maple_01', 'Flooring_Tile_Squares_01' gibi zincirleme varyantlarla 'Flooring' temel adını kullanmalısınız.

<a name="1.1-examples"></a>
#### Examples

##### Character

| Asset Type               | Asset Name   |
| ------------------------ | ------------ |
| Skeletal Mesh            | SK_Bob       |
| Material                 | M_Bob        |
| Texture (Diffuse/Albedo) | T_Bob_D      |
| Texture (Normal)         | T_Bob_N      |
| Texture (Evil Diffuse)   | T_Bob_Evil_D |

##### Prop

| Asset Type               | Asset Name   |
| ------------------------ | ------------ |
| Static Mesh (01)         | SM_Rock_01   |
| Static Mesh (02)         | SM_Rock_02   |
| Static Mesh (03)         | SM_Rock_03   |
| Material                 | M_Rock       |
| Material Instance (Snow) | MI_Rock_Snow |

<a name="asset-name-modifiers"></a>
### 4.2 Asset Adlandırma Kuralları

Bir varlığı adlandırırken, bir varlığın [Asset İsmi](#base-asset-name) ile kullanılacak ön(prefix) eki ve son(suffix) eki belirlemek için bu tabloları kullanın. 

#### Sections

> 4.2.1 [En Yaygın](#anc-common)

> 4.2.2 [Animations](#anc-animations)

> 4.2.3 [Artificial Intelligence](#anc-ai)

> 4.2.4 [Prefabs](#anc-prefab)

> 4.2.5 [Materials](#anc-materials)

> 4.2.6 [Textures](#anc-textures)

> 4.2.7 [Miscellaneous](#anc-misc)

> 4.2.8 [Physics](#anc-physics)

> 4.2.9 [Audio](#anc-audio)

> 4.2.10 [User Interface](#anc-ui)

> 4.2.11 [Effects](#anc-effects)

<a name="anc-common"></a>
#### En Yaygın

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Level / Scene           |  *          |            | [Levels diye bir dosyanın içinde olmalı.](#levels) e.g. `Levels/A4_C17_Parking_Garage.unity` |
| Level (Persistent)      |            | _P         |                                  |
| Level (Audio)           |            | _Audio     |                                  |
| Level (Lighting)        |            | _Lighting  |                                  |
| Level (Geometry)        |            | _Geo       |                                  |
| Level (Gameplay)        |            | _Gameplay  |                                  |
| Prefab                  |        |            |                                  |
| Material                | M_         |            |                                  |
| Static Mesh             | SM_       |            |                                  |
| Skeletal Mesh           | SK_       |            |                                  |
| Texture                 | T_         | _?         | Bkz [Textures](#anc-textures)    |
| Particle System         | PS_       |            |                                  |

<a name="anc-models"></a>

#### 4.2.1a 3D Models (FBX Files)

PascalCase

| Asset Type    | Prefix | Suffix | Notes |
| ------------- | ------ | ------ | ----- |
| Characters    | CH_    |        |       |
| Vehicles      | VH_    |        |       |
| Weapons       | WP_    |        |       |
| Static Mesh   | SM_    |        |       |
| Skeletal Mesh | SK_    |        |       |
| Skeleton      | SKEL_  |        |       |
| Rig           | RIG_   |        |       |

#### 4.2.1b 3d Models (3ds Max)

Bütün 3ds Max 3d mesh exportları FBXlerden ayırabilmek için küçük harfle yazılmalıdır.

| Asset Type    | Prefix | Suffix      | Notes                                   |
| ------------- | ------ | ----------- | --------------------------------------- |
| Mesh          |        | _mesh_lod0* | LOD suffixini sadece LOD kullanıyorsanız ekleyin |
| Mesh Collider |        | _collider   |                                         |

<a name="anc-animations"></a>

#### 4.2.2 Animations 
| Asset Type           | Prefix | Suffix | Notes |
| -------------------- | ------ | ------ | ----- |
| Animation Clip       | A_     |        |       |
| Animation Controller | AC_    |        |       |
| Avatar Mask          | AM_    |        |       |
| Morph Target         | MT_    |        |       |

<a name="anc-ai"></a>
#### 4.2.3 Artificial Intelligence

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| AI Controller           | AIC_     |            |                                  |
| Behavior Tree           | BT_      |            |                                  |
| Blackboard              | BB_       |            |                                  |
| Decorator               | BTDecorator_ |          |                                  |
| Service                 | BTService_ |            |                                  |
| Task                    | BTTask_  |            |                                  |
| Environment Query       | EQS_     |            |                                  |
| EnvQueryContext         | EQS_     | Context    |                                  |

<a name="anc-prefab"></a>
#### 4.2.4 Prefabs

| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Prefab         |        |            |                                  |
| Prefab Instance         | I       |            |                                  |
| Scriptable Object       |     |        |  Editörde "Blueprint" labelı koyulmalıdır. |

<a name="anc-materials"></a>

#### 4.2.5 Materials
| Asset Type        | Prefix | Suffix | Notes |
| ----------------- | ------ | ------ | ----- |
| Material          | M_     |        |       |
| Material Instance | MI_    |        |       |
| Physical Material | PM_    |        |       |

<a name="anc-textures"></a>

#### 4.2.6 Textures
| Asset Type              | Prefix     | Suffix     | Notes                            |
| ----------------------- | ---------- | ---------- | -------------------------------- |
| Texture                 | T_         |            |                                  |
| Texture (Diffuse/Albedo/Base Color)| T_ | _D      |                                  |
| Texture (Normal)        | T_         | _N         |                                  |
| Texture (Roughness)     | T_         | _R         |                                  |
| Texture (Alpha/Opacity) | T_         | _A         |                                  |
| Texture (Ambient Occlusion) | T_     | _AO      |                                  |
| Texture (Bump)          | T_         | _B         |                                  |
| Texture (Emissive)      | T_         | _E         |                                  |
| Texture (Mask)          | T_         | _M         |                                  |
| Texture (Specular)      | T_         | _S         |                                  |
| Texture (Packed)        | T_         | _*         | Aşağıdaki başlığa bakınız [packing](#anc-textures-packing). |
| Texture Cube            | TC_       |            |                                  |
| Media Texture           | MT_       |            |                                  |
| Render Target           | RT_       |            |                                  |
| Cube Render Target      | RTC_     |            |                                  |
| Texture Light Profile   | TLP_     |            |                                  |

<a name="anc-textures-packing"></a>

#### 4.2.6.1 Texture Paketleme
Birden çok doku verisi katmanını tek bir dokuda paketlemek yaygın bir uygulamadır. Bunun bir örneği, bir dokunun sırasıyla Kırmızı, Yeşil ve Mavi kanalları olarak Yayıcı, Pürüzlülük, Ortam Oklüzyonunu birlikte paketlemesidir. Son eki belirlemek için, verilen son ek harflerini yukarıdan bir araya getirmeniz yeterlidir, ör. '_ERO'.

> Diffuse/Albedo'nuzun alfa kanalına bir Alfa/Opaklık katmanı eklemek genellikle kabul edilebilir ve bu yaygın bir uygulama olduğundan, "_D" son ekine "A" eklemek isteğe bağlıdır.

Diffuse/Albedo'nun alfa kanalındaki bir Alfa/Opaklık maskesi dışında bir dokuya (RGBA) 4 kanal verinin paketlenmesi önerilmez, çünkü alfa kanallı bir doku, olmayandan daha fazla yüke neden olur. 
<a name="anc-misc"></a>

#### 4.2.7 Miscellaneous

| Asset Type                      | Prefix | Suffix | Notes |
| ------------------------------- | ------ | ------ | ----- |
| Universal Render Pipeline Asset | URP_   |        |       |
| Post Process Volume Profile     | PP_    |        |       |
| User Interface                  | UI_    |        |       |

<a name="anc-physics"></a>
#### 4.2.8 Physics

| Asset Type        | Prefix | Suffix | Notes |
| ----------------- | ------ | ------ | ----- |
| Physical Material | PM_    |        |       |

<a name="anc-audio"></a>

#### 4.2.9 Audio

| Asset Type     | Prefix | Suffix | Notes                                                        |
| -------------- | ------ | ------ | ------------------------------------------------------------ |
| Audio Clip     | A_     |        |                                                              |
| Audio Mixer    | MIX_   |        |                                                              |
| Dialogue Voice | DV_    |        |                                                              |
| Audio Class    |        |        | Prefix/suffix kullanımı yok. AudioClasses dosyasına konulması gerekmektedir. |

<a name="anc-ui"></a>
#### 4.2.10 User Interface
| Asset Type       | Prefix | Suffix | Notes |
| ---------------- | ------ | ------ | ----- |
| Font             | Font_  |        |       |
| Texture (Sprite) | T_     | _GUI   |       |

<a name="anc-effects"></a>
#### 4.2.11 Effects
| Asset Type      | Prefix | Suffix | Notes |
| --------------- | ------ | ------ | ----- |
| Particle System | PS_    |        |       |
**[⬆ Back to Top](#table-of-contents)**

<a name="asset-workflows"></a>

## 5. Asset Workflowu

Bu bölüm, Unity'de kullanılabilen assetlerı oluşturmaya ve içe aktarmaya yönelik en iyi uygulamaları açıklar. 

<a name="toc"></a>
### Sections

> 5.1 [Unity Asset Import Settings](#unityimport)
>
> 5.3 [Textures](#textures)
>
> 5.4 [Audio](#audio)

<a name="unityimport"></a>

### 5.1 Unity Asset Import Settings

Unitynin [AssetPostprocessor'ü](https://docs.unity3d.com/ScriptReference/AssetPostprocessor.html) assetleri içe aktarmadan önce veya sonra içe aktarma işlem hattına bağlanmanıza ve komut dosyalarını çalıştırmanıza olanak tanır. Bu, assetler projeye ilk kez içe aktarıldığında içe aktarma ayarlarını uygulamanıza olanak tanır. Örneğin import ederken sonu `_N` ile biten textürler otomatik olarak Normal Map olarak işaretlenebilir.

İçe Aktarma Ayarları için örnek kılavuz:

https://github.com/justinwasilenko/Unity-AssetPostProcessor

<a name="textures"></a>
### 5.3 Textürler

* Textürler yukarıdaki [isimlendirme kurallarını](#anc-textures) kullanır. 
* İkinin katı olmalılar (Örneğin, 512 x 512 or 256 x 1024).
* Mümkün olduğunca Textüre Atlası kullanın.
* 3D yazılımı, kaydettiğinizde veya dışa aktardığınızda tutarlılık için Unity proje textürelerine işaret etmelidir. 
* Oyun içi texture çözünürlüğü zaten biliniyorsa dokuyu Photoshop'ta yeniden boyutlandırmak, Unity'nin sıkıştırma seçeneklerini kullanmaktan daha iyidir. Bu, dosya boyutunu azaltır ve dokunun Unity'nin içine aktarılma süresini azaltır.
* Unity projenizin dışında yüksek çözünürlüklü bir kaynak PSD ile çalışırken, hem yüksek çözünürlüklü hem de içe aktarılan Unity dosyası için aynı adı kullanın. Bu, 2 doku arasında geçiş yaparken hızlı yinelemeye izin verir. 

Textürleri içe aktarmak ile ilgili daha fazla bilgiyi burada bulabilirsiniz: [https://docs.unity3d.com/Manual/ImportingTextures.html](https://docs.unity3d.com/Manual/ImportingTextures.html)

Alfa kanalının kullanılmasını gerektiren textürler bu kılavuzu takip etmelidir: [https://docs.unity3d.com/Manual/HOWTO-alphamaps.html](https://docs.unity3d.com/Manual/HOWTO-alphamaps.html)

##### Texture File Format

Bütün textürler .PSD formatında olmalıdır. Dosyanın layerları olmamalı ve sadece bir adet Alpha channel olmalıdır.

**[⬆ Back to Top](#table-of-contents)**

<a name="audio"></a>
### 5.4 Audio

Unity'e sadece kompresse edilmemiş WAV or AIFF formatlarında ses yükleyin.

Güzel bir guide: [Unity Audio Import Optimization](https://www.gamasutra.com/blogs/ZanderHulme/20190107/333794/Unity_Audio_Import_Optimisation__getting_more_BAM_for_your_RAM.php)

**[⬆ Back to Top](#table-of-contents)**



#### Article References:
https://unity3d.com/learn/tutorials/topics/tips/large-project-organisation
https://github.com/Allar/ue4-style-guide
http://www.arreverie.com/blogs/unity3d-best-practices-folder-structure-source-control/
