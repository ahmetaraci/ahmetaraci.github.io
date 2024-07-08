---
title: Markdown Rehberi
date: 06/07/2024 11:00:00 +0300
categories: [Türkçe, Rehber]
tags: [Markdown, Rehber, Jekyll]
---

Markdown, John Gruber tarafından 2004 yılında geliştirilmiş, düz metin biçimlendirme (formatlama) dilidir. HTML gibi daha karmaşık biçimlendirme dillerine bir alternatif olarak ortaya çıkmıştır. Markdown, yazı yazmayı ve düzenlemeyi basit ve hızlı hale getirir. Özellikle yazılım geliştiriciler, blog yazarları, teknik yazarlar ve diğer içerik oluşturucular tarafından sıkça kullanılır. Blogumda paylaştığım Ruby ve Jekyll ile blog yazmayı paylaştığım yazımda da markdown ile yazılarımızı yazmayı görmüştük.

### Markdown'un Avantajları

1. **Kolay Öğrenim ve Kullanım:** Markdown'un sözdizimi (syntax) oldukça basit ve anlaşılırdır. Öğrenmesi ve kullanması kolaydır.
2. **Okunabilirlik:** Markdown ile yazılmış bir metin, biçimlendirilmemiş düz metin olarak okunabilir. Bu da içerik oluştururken veya düzenlerken göz yormaz.
3. **Platform Bağımsız:** Markdown dosyaları (.md uzantılı) hemen hemen her platformda açılabilir ve düzenlenebilir.
4. **Geniş Destek:** Çeşitli metin editörleri, web platformları, blog sistemleri (örneğin GitHub, Jekyll) ve içerik yönetim sistemleri Markdown'u destekler.

### Başlıklar

Başlıklar `#` işareti ile oluşturulur. Bir `#` işareti en büyük başlığı, altı `#` işareti ise en küçük başlığı temsil eder. HTML’deki <h> etiketi gibi çalışır.

```markdown
# Başlık 1

## Başlık 2

### Başlık 3

#### Başlık 4

##### Başlık 5

###### Başlık 6
```

### Paragraflar

Normal metin paragraflar halinde yazılır ve her paragraf arasında bir boş satır bırakılır.

```markdown
Bu bir paragraftır.

Bu da başka bir paragraftır.
```

Bu bir paragraftır.

Bu da başka bir paragraftır.

---

### Kalın ve İtalik Yazı

Metni kalın yapmak için çift yıldız `**` veya çift alt çizgi `__`, italik yapmak için tek yıldız `*` veya tek alt çizgi `_` kullanılır.

```markdown
**Bu metin kalındır.**
**Bu da kalın metindir.**

_Bu metin italiktir._
_Bu da italik metindir._
```

**Bu metin kalındır.Bu da kalın metindir.**

_Bu metin italiktir.Bu da italik metindir._

---

### Listeler

- **Sırasız Listeler:** `-`, `+` veya `*` ile başlatılır.

```markdown
- Öğe 1
- Öğe 2
  - Alt öğe 1
  - Alt öğe 2
```

- Öğe 1
- Öğe 2
  - Alt öğe 1
  - Alt öğe 2

---

- **Sıralı Listeler:** Sayılar ve noktalar ile başlatılır.

```markdown
1. İlk madde
2. İkinci madde
3. Üçüncü madde
```

1. İlk madde
2. İkinci madde
3. Üçüncü madde

---

### Bağlantılar

Bağlantılar köşeli parantez `[ ]` içinde bağlantı metni ve ardından normal parantez `( )` içinde URL ile oluşturulur.

```markdown
[Blogumu Ziyaret Edebilirsiniz](https://ahmetaraci.github.io)
```

[Blogumu Ziyaret Edebilirsiniz](https://ahmetaraci.github.io/)

---

### Görseller

Görseller bağlantılara benzer şekilde eklenir, ancak başına ünlem işareti `!` eklenir.

```markdown
![Açıklama](https://www.osgeo.org/wp-content/uploads/postgis-logo-1.png)
```

![https://www.osgeo.org/wp-content/uploads/postgis-logo-1.png](https://www.osgeo.org/wp-content/uploads/postgis-logo-1.png)

---

### Kod Blokları ve Satır İçi Kod

- **Satır İçi Kod:** Tek bir ters tırnak işareti ``` ile belirtilir.

```markdown
`print("Merhaba Dünya")`
```

---

- **Kod Blokları:** Üç ters tırnak işareti ````` ile başlar ve biter. İsteğe bağlı olarak dil belirtilebilir.

````markdown
```python
def merhaba():
    print("Merhaba Dünya")
```
````

````

---

### Alıntılar

Alıntılar `>` işareti ile başlar.

```markdown
> Bu bir alıntıdır.
>> Bu da iç içe alıntıdır.
````

> Bu bir alıntıdır.
>
> > Bu da iç içe alıntıdır.

---

### Vurgulamalar

Metin içerisinde bir kısmı vurgulamak için ` ` tırnakları içersine metin yazılır.

```markdown
Muhammet Ahmet ARACI `GIS Developer`
```

Muhammet Ahmet ARACI `GIS Developer`

---

### Çizgiler

Üç veya daha fazla tire `---`, yıldız `***` veya alt çizgi `___` kullanılarak yatay çizgi oluşturulabilir.

```markdown
---
***
___

---
```

---

---

---

### Tablo Oluşturmak

```markdown
|             | JAVASCRIPT          | PHP           |
| ----------- | ------------------- | ------------- |
| Tek Tırnak  | `'Yaşama Sevincim'` | 'Ömür Törpüm' |
| Çift Tırnak | `"Yaşama Sevincim"` | "Ömür Törpüm" |
```

|             | JAVASCRIPT        | PHP           |
| ----------- | ----------------- | ------------- |
| Tek Tırnak  | 'Yaşama Sevincim' | 'Ömür Törpüm' |
| Çift Tırnak | "Yaşama Sevincim" | "Ömür Törpüm" |

### Metinde Renk Değiştirmek

Markdown doğrudan renk değiştirme özelliklerini desteklemez, ancak HTML ile birlikte kullanarak metin rengini değiştirebilirsiniz.

```markdown
# Renk Örnekleri

Bu normal bir paragraf.

<span style="color: blue;">Bu metin mavi renkte.</span>

<span style="color: green;">Bu metin yeşil renkte.</span>

<span style="color: #ff6347;">Bu metin turuncu renkte.</span>

Bu tekrar normal bir paragraf.
```

# Renk Örnekleri

Bu normal bir paragraf.

<span style="color: blue;">Bu metin mavi renkte.</span>

<span style="color: green;">Bu metin yeşil renkte.</span>

<span style="color: #ff6347;">Bu metin turuncu renkte.</span>

Bu tekrar normal bir paragraf.

---

### İç İçe Listeler

Markdown'da iç içe listeler şu şekilde oluşturulabilir:

```markdown
Markdown'da iç içe listeler şu şekilde oluşturulabilir:

1. Ana madde 1
   1. Alt madde 1.1
   2. Alt madde 1.2
      1. Alt alt madde 1.2.1
      2. Alt alt madde 1.2.2
2. Ana madde 2
   1. Alt madde 2.1
   2. Alt madde 2.2
```

1. Ana madde 1
   1. Alt madde 1.1
   2. Alt madde 1.2
      1. Alt alt madde 1.2.1
      2. Alt alt madde 1.2.2
2. Ana madde 2
   1. Alt madde 2.1
   2. Alt madde 2.2

---

### Görev Listesi

Markdown'da görev listeleri şu şekilde oluşturulabilir:

```markdown
Markdown'da görev listeleri şu şekilde oluşturulabilir:

- [x] Görev 1 (Tamamlandı)
- [ ] Görev 2 (Tamamlanmadı)
- [ ] Görev 3 (Tamamlanmadı)
  - [x] Alt görev 3.1 (Tamamlandı)
  - [ ] Alt görev 3.2 (Tamamlanmadı)
```

- [x] Görev 1 (Tamamlandı)
- [ ] Görev 2 (Tamamlanmadı)
- [ ] Görev 3 (Tamamlanmadı)
  - [x] Alt görev 3.1 (Tamamlandı)
  - [ ] Alt görev 3.2 (Tamamlanmadı)

---

### Emojiler

Markdown içinde emojiler kullanmak çok basittir. Emoji kısa kodlarını kullanabilirsiniz. Örneğin:

```markdown
Burada bir gülümseme emojisi: 😄

Bir el sallama emojisi: 👋

Kalp emojisi: ❤️
```

Burada bir gülümseme emojisi: 😄

Bir el sallama emojisi: 👋

Kalp emojisi: ❤️

---

### İçerik Gizlemek

Markdown dosyamız içerisinde bulunmasını istediğimiz ancak dosya renderlandıktan sonra görünmesini istemediğimiz şeyleri gizler.

```markdown
<!-- Bu bölüm görünmeyecek -->
```

---
