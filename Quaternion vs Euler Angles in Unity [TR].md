Unity'de 3D çalışırken kafa kurcalayan konulardan biri 
Quaternion'ların ne işe yaradığı,
Neden her yerde Euler Angles kullanılmadığı ve Quaternion kullanıldığı.

3 Boyutlu rotasyon belirtmek için kullanılan Euler Açısı, 
bir 3x3 rotasyon matrisi ile ifade edilebiliyor. Örnek:

![Euler Açısı](/euler%20angle.svg)

İdeal bir sistemde her bir rotasyon matrisinin, yalnızca tek açıya isabet etmesini isteriz.
Sorun şu ki bu matrisler, her zaman için tek açıya tekabül etmeyebiliyor.
Aynı matris birden fazla açıya denk gelebiliyor. 

"Gimbal Lock" sorunu oluşabiliyor. İki eksenin çakışıp bağımsızlığını yitirmesi.
(Buna "Loss of degree of freedom" deniyor.) Örnek:

**Gimbal Lock'a uğrayan uçak: **
![Gimbal Lock'a uğrayan uçak](/Gimbal_lock_airplanebyLookang.gif) 

<sub>(By Lookang many thanks to Fu-Kwun Hwang and author of Easy Java Simulation = Francisco Esquembre - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=15837410) </sub>


**Gimbal Lock teorik gösterim:**
![Gimbal Lock sorunu teorik gösterim](/gimballockbyLookang.gif) 

<sub> (By Lookang many thanks to Fu-Kwun Hwang and author of Easy Java Simulation = Francisco Esquembre - Own work, CC BY-SA 3.0, https://commons.wikimedia.org/w/index.php?curid=15837410) </sub>

Bu sorunun yaşanmaması için Quaternion'lar kullanılıyor. 
Quaternion'larda Euler açılarına ek olarak 4. bir değer var. 
Bu değer skaler bir değer. Ve bunun olması, çakışmaları önlüyor.

Bir Quaternion, "a + bi + cj + dk" şeklinde gösterilebilir.

3 vektörel değerin yanındaki skaler değer sayesinde 
her bir rotasyon matrisi, görüntü kümesinde tek bir açıya işaret ediyor.
Ve çakışma sorunu çözülmüş oluyor.

Unity'de oyun yapılırken genellikle Quaternion'ların iç 
yapılarıyla fazla haşır neşir olunmuyor. İnternette yaptığım 
araştırmalara ve nabız yoklamalara göre bunlar daha çok 
gelişmiş matematik ve Makine ve Uçak mühendisliğinin konuları. 
Yazılım camiasında daha pragmatik yaklaşılıyor 
ve ihtiyaç olduğu ölçüde kullanılıyor.

Mesela Quaternion.Identity(); rotasyon yok demek
ya da 
Quaternion.lookrotation(yeniRotasyon); dediğimizde 
vereceğimiz yeni rotasyona dönüş sağlıyoruz.

