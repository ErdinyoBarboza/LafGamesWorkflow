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
> All letters are lowercase, e.g. `deserteagle`, 
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
#### AHerzaman [PascalCase](#terms-cases) kullanın
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
### 2.7 Very Large Asset Sets Get Their Own Folder Layout

This can be seen as a pseudo-exception to [2.6](#2.6).

There are certain asset types that have a huge volume of related files where each asset has a unique purpose. The two most common are Animation and Audio assets. If you find yourself having 15+ of these assets that belong together, they should be together.

For example, animations that are shared across multiple characters should lay in `Characters/Common/Animations` and may have sub-folders such as `Locomotion` or `Cinematic`.

> This does not apply to assets like textures and materials. It is common for a `Rocks` folder to have a large amount of textures if there are a large amount of rocks, however these textures are generally only related to a few specific rocks and should be named appropriately. Even if these textures are part of a [Material Library](#2.8).

<a name="2.8"></a>
<a name="structure-material-library"></a>
### 2.8 `MaterialLibrary`

If your project makes use of master materials, layered materials, or any form of reusable materials or textures that do not belong to any subset of assets, these assets should be located in `Assets/ProjectName/MaterialLibrary`.

This way all 'global' materials have a place to live and are easily located.

> This also makes it incredibly easy to enforce a 'use material instances only' policy within a project. If all artists and assets should be using material instances, then the only regular material assets that should exist are within this folder. You can easily verify this by searching for base materials in any folder that isn't the `MaterialLibrary`.

The `MaterialLibrary` doesn't have to consist of purely materials. Shared utility textures, material functions, and other things of this nature should be stored here as well within folders that designate their intended purpose. For example, generic noise textures should be located in `MaterialLibrary/Utility`.

Any testing or debug materials should be within `MaterialLibrary/Debug`. This allows debug materials to be easily stripped from a project before shipping and makes it incredibly apparent if production assets are using them if reference errors are shown.

<a name="2.9"></a>
<a name="scene-structure"></a>
## 2.9 Scene Structure
Next to the project’s hierarchy, there’s also scene hierarchy. As before, we’ll present you a template. You can adjust it to your needs. Use named empty game objects as scene folders.

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

 - All empty objects should be located at 0,0,0 with default rotation and scale.
 - For empty objects that are only containers for scripts, use “@” as prefix – e.g. @Cheats
 - When you’re instantiating an object in runtime, make sure to put it in _Dynamic – do not pollute the root of your hierarchy or you will find it difficult to navigate through it.

**[⬆ Back to Top](#table-of-contents)**

<a name="scripts"></a>

## 3. Scripts

This section will focus on C# classes and their internals. When possible, style rules conform to Microsoft's C# standard.

### Sections
> 3.1 [Class Organization](#classorganization)

> 3.2 [Compiling](#compiling)

> 3.3 [Variables](#variables)

> 3.4 [Functions](#functions)

<a name="classorganization"></a>
### 3.1 Class Organization
Source files should contain only one public type, although multiple internal classes are allowed.

Source files should be given the name of the public class in the file.

Organize namespaces with a clearly defined structure,

Class members should be alphabetized, and grouped into sections:
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

Within each of these groups order by access:
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
To save some time you can overwrite Unity's default script template with your own  to automatically setup the namespace and regions etc. See this Unity [support](https://support.unity3d.com/hc/en-us/articles/210223733-How-to-customize-Unity-script-templates) article to learn how.

<a name="namespace"></a>
#### Namespace
Use a namespace to ensure your scoping of classes/enum/interface/etc won't conflict with existing ones from other namespaces or the global namespace. The project should at minimum use the projects name for the Namespace to prevent conflicts with any imported Third Party assets.

#### All Public Functions Should Have A Summary

Simply, any function that has an access modifier of Public should have its summary filled out. 

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
If a class has only a small number of variables, Foldout Groups are not required.

If a class has a moderate amount of variables (5-10), all [Serializable](#serializable) variables should have a non-default Foldout Group assigned. A common category is `Config`.

To create Foldout Groups there are 2 options in Unity. 

* The first is to define a `[Serializable] public Class` inside the main class however this can have a performance impact. This allows the use of the same variable name to be shared.
* The second option is to use the Foldout Group Attribute available with [Odin Inspector](https://odininspector.com/).

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

**Bad**

* `PlayerScore`
* `PlayerKills`
* `MyTargetPlayer`
* `MyCharacterName`
* `CharacterSkills`
* `ChosenCharacterSkin`

All of these variables are named redundantly. It is implied that the variable is representative of the `PlayerCharacter` it belongs to because it is `PlayerCharacter` that is defining these variables.

**Good**

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
All booleans should be named in PascalCase but prefixed with a verb.

Example: Use `isDead` and `hasItem`, **not** `Dead` and `Item`.

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
Interfaces are led with a capital `I` then followed with PascalCase.

Example: ```public interface ICanEat { }```

<a name="functions"></a>
### 3.4 Functions, Events, and Event Dispatchers
This section describes how you should author functions, events, and event dispatchers. Everything that applies to functions also applies to events, unless otherwise noted.

#### Function Naming
The naming of functions, events, and event dispatchers is critically important. Based on the name alone, certain assumptions can be made about functions. For example:

* Is it a pure function?
* Is it fetching state information?
* Is it a handler?
* What is its purpose?

These questions and more can all be answered when functions are named appropriately.

<a name="function-verbrule"></a>
#### All Functions Should Be Verbs
All functions and events perform some form of action, whether its getting info, calculating data, or causing something to explode. Therefore, all functions should start with verbs. They should be worded in the present tense whenever possible. They should also have some context as to what they are doing.

Good examples:

* `Fire` - Good example if in a Character / Weapon class, as it has context. Bad if in a Barrel / Grass / any ambiguous class.
* `Jump` - Good example if in a Character class, otherwise, needs context.
* `Explode`
* `ReceiveMessage`
* `SortPlayerArray`
* `GetArmOffset`
* `GetCoordinates`
* `UpdateTransforms`
* `EnableBigHeadMode`
* `IsEnemy` - ["Is" is a verb.](http://writingexplained.org/is-is-a-verb)

Bad examples:

* `Dead` - Is Dead? Will deaden?
* `Rock`
* `ProcessData` - Ambiguous, these words mean nothing.
* `PlayerState` - Nouns are ambiguous.
* `Color` - Verb with no context, or ambiguous noun.

#### Functions Returning Bool Should Ask Questions
When writing a function that does not change the state of or modify any object and is purely for getting information, state, or computing a yes/no value, it should ask a question. This should also follow [the verb rule](#function-verbrule).

This is extremely important as if a question is not asked, it may be assumed that the function performs an action and is returning whether that action succeeded.

Good examples:

* `IsDead`
* `IsOnFire`
* `IsAlive`
* `IsSpeaking`
* `IsHavingAnExistentialCrisis`
* `IsVisible`
* `HasWeapon` - ["Has" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)
* `WasCharging` - ["Was" is past-tense of "be".](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html) Use "was" when referring to 'previous frame' or 'previous state'.
* `CanReload` - ["Can" is a verb.](http://grammar.yourdictionary.com/parts-of-speech/verbs/Helping-Verbs.html)

Bad examples:

* `Fire` - Is on fire? Will fire? Do fire?
* `OnFire` - Can be confused with event dispatcher for firing.
* `Dead` - Is dead? Will deaden?
* `Visibility` - Is visible? Set visibility? A description of flying conditions?

#### Event Handlers and Dispatchers Should Start With `On`
Any function that handles an event or dispatches an event should start with `On` and continue to follow [the verb rule](#function-verbrule).

Good examples:

* `OnDeath` - Common collocation in games
* `OnPickup`
* `OnReceiveMessage`
* `OnMessageRecieved`
* `OnTargetChanged`
* `OnClick`
* `OnLeave`

Bad examples:

* `OnData`
* `OnTarget`

**[⬆ Back to Top](#table-of-contents)**
<a name="anc"></a>
<a name="4"></a>

## 4. Asset Naming Conventions
Naming conventions should be treated as law. A project that conforms to a naming convention is able to have its assets managed, searched, parsed, and maintained with incredible ease.

Most things are prefixed with the prefix generally being an acronym of the asset type followed by an underscore.

**Assets use [PascalCase](#cases)**

<a name="base-asset-name"></a>
<a name="4.1"></a>
### 4.1 Base Asset Name - `Prefix_BaseAssetName_Variant_Suffix`
All assets should have a _Base Asset Name_. A Base Asset Name represents a logical grouping of related assets. Any asset that is part of this logical group 
should follow the the standard of  `Prefix_BaseAssetName_Variant_Suffix`.

Keeping the pattern `Prefix_BaseAssetName_Variant_Suffix` in mind and using common sense is generally enough to warrant good asset names. Here are some detailed rules regarding each element.

`Prefix` and `Suffix` are to be determined by the asset type through the following [Asset Name Modifier](#asset-name-modifiers) tables.

`BaseAssetName` should be determined by short and easily recognizable name related to the context of this group of assets. For example, if you had a character named Bob, all of Bob's assets would have the `BaseAssetName` of `Bob`.

For unique and specific variations of assets, `Variant` is either a short and easily recognizable name that represents logical grouping of assets that are a subset of an asset's base name. For example, if Bob had multiple skins these skins should still use `Bob` as the `BaseAssetName` but include a recognizable `Variant`. An 'Evil' skin would be referred to as `Bob_Evil` and a 'Retro' skin would be referred to as `Bob_Retro`.

For unique but generic variations of assets, `Variant` is a two digit number starting at `01`. For example, if you have an environment artist generating nondescript rocks, they would be named `Rock_01`, `Rock_02`, `Rock_03`, etc. Except for rare exceptions, you should never require a three digit variant number. If you have more than 100 assets, you should consider organizing them with different base names or using multiple variant names.

Depending on how your asset variants are made, you can chain together variant names. For example, if you are creating flooring assets for an Arch Viz project you should use the base name `Flooring` with chained variants such as `Flooring_Marble_01`, `Flooring_Maple_01`, `Flooring_Tile_Squares_01`.

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
| Texture                 | T_         | _?         | See [Textures](#anc-textures)    |
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
| Mesh          |        | _mesh_lod0* | Only use LOD suffix if model uses LOD's |
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
| Texture (Packed)        | T_         | _*         | See notes below about [packing](#anc-textures-packing). |
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
* It is better to resize the texture in Photoshop then to use Unity’s compression options when the in game texture resolution is already known. This reduces the file size and import time of the texture into Unity.
* When working with a high-resolution source PSD outside your Unity project use the same name for both the high-resolution and the imported Unity file. This allows quick iteration when swapping between the 2 textures.

More information for importing textures can be found here: [https://docs.unity3d.com/Manual/ImportingTextures.html](https://docs.unity3d.com/Manual/ImportingTextures.html)

Textures requiring the use of a Alpha channel should follow this guide: [https://docs.unity3d.com/Manual/HOWTO-alphamaps.html](https://docs.unity3d.com/Manual/HOWTO-alphamaps.html)

##### Texture File Format

Bütün textürler .PSD formatında olmalıdır. Dosyanın layerları olmamalı ve sadece bir adet Alpha channel olmalıdır.

**[⬆ Back to Top](#table-of-contents)**

<a name="audio"></a>
### 5.4 Audio

Only import uncompressed audio files in to Unity using WAV or AIFF formats.

Great guide on [Unity Audio Import Optimization](https://www.gamasutra.com/blogs/ZanderHulme/20190107/333794/Unity_Audio_Import_Optimisation__getting_more_BAM_for_your_RAM.php)

**[⬆ Back to Top](#table-of-contents)**



#### Article References:
https://unity3d.com/learn/tutorials/topics/tips/large-project-organisation
https://github.com/Allar/ue4-style-guide
http://www.arreverie.com/blogs/unity3d-best-practices-folder-structure-source-control/
