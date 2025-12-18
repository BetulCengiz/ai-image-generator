# AI Image Generator

Bu proje, Hugging Face API'sini kullanarak metin girdilerinden görseller oluşturan modern bir web uygulamasıdır. Kullanıcılar çeşitli modeller arasından seçim yapabilir, oluşturulacak görsel sayısını belirleyebilir ve farklı en boy oranları seçebilirler.

###  Uygulama Arayüzü
![](public/Macbook.png) 

## 🚀 Başlangıç

Projeyi çalıştırmak oldukça basittir. Ancak uygulamanın görselleri üretebilmesi için geçerli bir API anahtarına ihtiyacı vardır.

### 1. API Anahtarı Kurulumu
Bu uygulamayı kullanabilmek için kendi Hugging Face API anahtarınızı kullanmalısınız.

1.  `script.js` dosyasını açın.
2.  10. satırdaki `API_KEY` değişkenini bulun:
    ```javascript
    const API_KEY = "YOUR_API_KEY"
    ```
3.  `"YOUR_API_KEY"` ibaresini kendi Hugging Face API anahtarınızla değiştirin (örn: `"hf_..."`).

> **Not:** API anahtarınızın seçtiğiniz modelleri kullanma iznine sahip olduğundan emin olun.

## ⚙️ Özelleştirme ve Model Değişikliği

Proje, kullanıcıların ihtiyaçlarına göre özelleştirilebilir bir yapıdadır. İstediğiniz herhangi bir Hugging Face modelini projeye entegre edebilirsiniz.

### Model Nasıl Değiştirilir?

1.  **HTML Değişikliği:**
    `index.html` dosyasında `id="model-select"` olan `<select>` elementini bulun. Buraya yeni bir `<option>` ekleyerek istediğiniz modeli listeye dahil edebilirsiniz. `value` özelliği, modelin Hugging Face üzerindeki tam yolunu (ID) içermelidir.

    ```html
    <!-- Örnek: -->
    <option value="stabilityai/stable-diffusion-3-medium">Stable Diffusion 3</option>
    ```

2.  **JavaScript Düzenlemesi (generateImages):**
    ⚠️ **DİKKAT:** Farklı modeller, farklı parametreler veya veri yapıları gerektirebilir.
    
    Eğer eklediğiniz model standart yapıdan farklı çalışıyorsa veya modelin kullanımı zamanla değiştiyse, `script.js` dosyasındaki `generateImages` fonksiyonunu güncellemeniz gerekebilir.
    
    Özellikle şu kısmı modelin gereksinimlerine göre kontrol edin:
    ```javascript
    // script.js içinde generateImages fonksiyonu
    body: JSON.stringify({
        inputs: promptText,
        parameters: { width, height }, // Bazı modeller farklı parametreler isteyebilir
    }),
    ```
    Yeni modelin dokümantasyonunu kontrol ederek `inputs` ve `parameters` alanlarını doğru yapılandırdığınızdan emin olun.

## ✨ Özellikler

*   **Çoklu Model Desteği:** FLUX, Stable Diffusion XL, OpenJourney gibi popüler modeller hazır gelir.
*   **Esnek Ayarlar:**
    *   Görsel Sayısı (1-4 arası seçim)
    *   En Boy Oranı (1:1, 16:9, 9:16)
*   **Karanlık/Aydınlık Mod:** Sistem temasını algılar ve manuel geçiş imkanı sunar.
*   **Rastgele İstem Üretici:** İlham almak için "Zar" ikonuna tıklayarak rastgele bir istem oluşturabilirsiniz.
*   **Kolay İndirme:** Oluşturulan görselleri tek tıkla indirebilirsiniz.

## 🛠️ Teknolojiler

*   HTML5
*   CSS3 (Modern ve duyarlı tasarım)
*   JavaScript (ES6+)
*   Hugging Face Inference API
