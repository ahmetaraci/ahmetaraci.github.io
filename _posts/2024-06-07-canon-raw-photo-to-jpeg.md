---
title: CR2 uzantılı RAW fotoğrafların JPEG'e dönüşümünde Python kullanmak
date: 07/06/2024 17:00:00 +0300
categories: [Türkçe]
tags: [Python, Script]
---

## RAW Fotoğraflarınızı Python ile JPEG'e Dönüştürmek

Merhaba, eğer siz de benim gibi Canon marka fotoğraf makinenizden çıkan RAW formatındaki (CR2) fotoğrafları JPEG formatına dönüştürmekte zorlandıysanız blog ilginizi çekecektir. Bu yazıda, Python kullanarak bu dönüşümü nasıl yapabileceğinizi anlatacağım. Üstelik sadece birkaç satır kod yazarak!

### Neden Python?

Fotoğraf düzenleme programları bazen çok karmaşık ve kafa karıştırıcı olabiliyor. Ancak bir yazılımcı olarak, kod yazmak benim için çok daha rahat ve konforlu. Python, sunduğu basit ve güçlü kütüphanelerle bu işi kolayca halletmemizi sağlıyor. Gelin, adım adım bu süreci nasıl gerçekleştireceğimize bakalım.

### Gerekli Kütüphaneler

Öncelikle, bu işlemi gerçekleştirmek için PIL (Pillow) kütüphanesine ihtiyacımız var. Bu kütüphaneyi yüklemek oldukça basit:

```bash
pip install pillow
```

## Python Scriptimiz

İşte RAW formatındaki (CR2) fotoğraflarınızı JPEG formatına dönüştüren Python scripti:

```python

import os
from PIL import Image

# CR2 dosyalarının bulunduğu klasör
input_folder = r"C:\path\to\your\raw_folder"

# JPEG dosyalarının kaydedileceği klasör
output_folder = r"C:\path\to\your\jpeg_folder"

# CR2 dosyalarını dönüştürme ve JPEG olarak kaydetme
for filename in os.listdir(input_folder):
    if filename.lower().endswith('.cr2'):
        input_path = os.path.join(input_folder, filename)
        output_path = os.path.join(output_folder, os.path.splitext(filename)[0] + '.jpg')

        # CR2 dosyasını açma ve JPEG olarak kaydetme
        image = Image.open(input_path)
        image.save(output_path, 'JPEG', quality=100)  # JPEG kalite ayarı (0-100 arası)
        image.close()

print("Dönüştürme işlemi tamamlandı.")

```

## Scripti Nasıl Kullanırız?

1. **Girdi ve Çıktı Klasörlerini Belirleyin:**
   Yukarıdaki scriptte, `input_folder` ve `output_folder` değişkenlerinin değerlerini kendi bilgisayarınızdaki klasör yollarıyla değiştirin. `input_folder`, RAW dosyalarınızın bulunduğu klasör; `output_folder` ise dönüştürülen JPEG dosyalarının kaydedileceği klasör olacak.

2. **Scripti Çalıştırın:**
   Python scriptini çalıştırarak dönüşüm işlemini başlatın. Script, belirttiğiniz klasördeki tüm CR2 dosyalarını bulacak ve bunları JPEG formatına dönüştürerek belirttiğiniz çıktı klasörüne kaydedecektir.

3. **Dönüştürme Kalitesi:**
   Scriptteki `quality` parametresi ile JPEG kalitesini ayarlayabilirsiniz. Bu değer 0 ile 100 arasında bir değerdir. 100 en yüksek kaliteyi, 0 ise en düşük kaliteyi temsil eder.

## Sonuç

Gördüğünüz gibi, Python ile RAW fotoğraflarınızı JPEG formatına dönüştürmek oldukça basit. Bu yöntemi kullanarak, profesyonel görüntü işleme uygulamalarıyla uğraşmadan fotoğraflarınızı dilediğiniz formata çevirebilirsiniz. Umarım bu yazı sizin için faydalı olmuştur. Herhangi bir sorunuz olursa, benimle iletişime geçmekten çekinmeyin!
