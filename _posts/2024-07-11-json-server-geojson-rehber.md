---
title: JSON Server ve GeoJSON ile Kullanımı
date: 11/07/2024 11:00:00 +0300
categories: [Türkçe, Rehber]
tags: [JSON, GeoJSON, Backend, API]
---

## JSON Server Nedir?

JSON Server, küçük projeler veya hızlı prototip geliştirme süreçleri için kullanabileceğiniz, basit ve hafif bir RESTful API sunucusudur. Bir JSON dosyasını, minimum konfigürasyon ile bir veritabanı gibi kullanmanızı sağlar ve bu veriyi RESTful API aracılığıyla erişilebilir hale getirir.

Yazının içeriğini barındıran [github reposuna](https://github.com/ahmetaraci/json-server-geojson-rehber) bağlantıdan erişebilirsiniz.

## Neden JSON Server Kullanmalıyız?

1. **Hızlı Kurulum ve Kullanım:** JSON Server, dakikalar içinde kurulabilir ve çalıştırılabilir. Özellikle küçük projelerde ve prototiplerde hızlıca API oluşturmanızı sağlar.
2. **Geliştirme ve Test:** Geliştirme sürecinde backend hazır değilse, frontend geliştirme için geçici bir API sunucusu olarak kullanılabilir.
3. **Minimal Yapılandırma:** Karmaşık konfigürasyonlara gerek yoktur. JSON dosyanızdaki verileri kolayca API endpointlerine dönüştürür.
4. **JSON Dosyasını Veri Tabanı Olarak Kullanma:** JSON formatında sakladığınız verileri, bir veritabanı gibi kullanmanıza olanak tanır.

## JSON Server Kurulumu ve Kullanımı

### Gereksinimler

- Node.js ve npm (Node Package Manager)

### Adım 1: Node.js ve npm Kurulumu

JSON Server'ı kullanabilmek için öncelikle Node.js ve npm kurulu olmalıdır. Node.js'i resmi web sitesinden ([https://nodejs.org/](https://nodejs.org/)) indirebilir ve kurulum talimatlarını takip edebilirsiniz.

Kurulumun ardından, terminal veya komut istemcisine aşağıdaki komutları yazarak Node.js ve npm'in doğru şekilde kurulduğunu doğrulayabilirsiniz:

```bash
node -v
npm -v
```

### Adım 2: JSON Server'ın Kurulumu

JSON Server'ı global olarak kurmak için aşağıdaki komutu terminale yazın:

```bash
npm install -g json-server
```

### Adım 3: JSON Server'ı Başlatma

JSON Server'ı başlatmak için bir JSON dosyasına ihtiyacımız olacak. Örnek bir JSON dosyası oluşturalım:

```json
{
  "posts": [
    { "id": 1, "title": "Merhaba Dünya", "author": "Ahmet" },
    { "id": 2, "title": "JSON Server", "author": "Mehmet" }
  ],
  "comments": [
    { "id": 1, "body": "Harika bir yazı!", "postId": 1 },
    { "id": 2, "body": "Teşekkürler!", "postId": 1 }
  ],
  "profile": { "name": "Ahmet" },
  "locations": [
    {
      "id": 1,
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [28.97953, 41.015137]
      },
      "properties": {
        "name": "İstanbul"
      }
    },
    {
      "id": 2,
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [32.859741, 39.933365]
      },
      "properties": {
        "name": "Ankara"
      }
    }
  ]
}
```

Bu JSON dosyasını `db.json` adıyla kaydedin. Ardından JSON Server'ı başlatmak için terminale aşağıdaki komutu yazın:

```bash
json-server --watch db.json
```

Bu komut, `db.json` dosyasını izlemeye alacak ve localhost üzerinde 3000 portunda bir API sunucusu başlatacaktır. Tarayıcınızda `http://localhost:3000` adresine giderek API'yi test edebilirsiniz.

### Adım 4: JSON Server'ı Kullanma

Başlatılan sunucuda aşağıdaki API endpointlerine erişebilirsiniz:

- `GET /posts`
- `GET /posts/1`
- `POST /posts`
- `PUT /posts/1`
- `PATCH /posts/1`
- `DELETE /posts/1`
- `GET /locations` (GeoJSON verisi)

### HTTP Metotları ve Örnekler

### GET Metodu

GET metodu, sunucudan veri almak için kullanılır. Örneğin, tüm post verilerini almak için:

```bash
curl http://localhost:3000/posts
```

Sonuç:

```bash
[
  { "id": 1, "title": "Merhaba Dünya", "author": "Ahmet" },
  { "id": 2, "title": "JSON Server", "author": "Mehmet" }
]
```

Belirli bir postu almak için:

```bash
curl http://localhost:3000/posts/1
```

Sonuç:

```json
{ "id": 1, "title": "Merhaba Dünya", "author": "Ahmet" }
```

### POST Metodu

POST metodu, sunucuya yeni veri eklemek için kullanılır. Örneğin, yeni bir post eklemek için:

```bash
curl -X POST -H "Content-Type: application/json" -d '{"title": "Yeni Post", "author": "Ali"}' http://localhost:3000/posts
```

Sonuç:

```json
{
  "title": "Yeni Post",
  "author": "Ali",
  "id": 3
}
```

### PUT Metodu

PUT metodu, mevcut bir veriyi tamamen güncellemek için kullanılır. Örneğin, mevcut bir postu güncellemek için:

```bash
curl -X PUT -H "Content-Type: application/json" -d '{"title": "Güncellenmiş Post", "author": "Ahmet"}' http://localhost:3000/posts/1
```

Sonuç:

```json
{
  "id": 1,
  "title": "Güncellenmiş Post",
  "author": "Ahmet"
}
```

### PATCH Metodu

PATCH metodu, mevcut bir veriyi kısmen güncellemek için kullanılır. Örneğin, bir postun sadece başlığını güncellemek için:

```bash
curl -X PATCH -H "Content-Type: application/json" -d '{"title": "Kısmen Güncellenmiş Post"}' http://localhost:3000/posts/1
```

Sonuç:

```json
{
  "id": 1,
  "title": "Kısmen Güncellenmiş Post",
  "author": "Ahmet"
}
```

### DELETE Metodu

DELETE metodu, mevcut bir veriyi silmek için kullanılır. Örneğin, bir postu silmek için:

```bash
curl -X DELETE http://localhost:3000/posts/1
```

Sonuç: Post silinir ve artık erişilemez.

---

### GeoJSON Verilerini JSON Server da Kullanmak

Yazımızda son olarak kısaca Web CBS geliştirmek isteyen kişiler için Türkiye içerisinde nokta, çizgi ve alan verilerini içeren bir GeoJSON örneği oluşturdum ve bu veriyi Leaflet ve OpenLayers ile nasıl görselleştireceğimizi anlatıyorum.

### GeoJSON Verisi

Öncelikle, `db.json` dosyamızdaki `locations` bölümünü aşağıdaki gibi güncelleyelim:

```json
{
  "locations": [
    {
      "id": 1,
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [28.97953, 41.015137]
      },
      "properties": {
        "name": "İstanbul"
      }
    },
    {
      "id": 2,
      "type": "Feature",
      "geometry": {
        "type": "Point",
        "coordinates": [32.859741, 39.933365]
      },
      "properties": {
        "name": "Ankara"
      }
    },
    {
      "id": 3,
      "type": "Feature",
      "geometry": {
        "type": "LineString",
        "coordinates": [
          [28.97953, 41.015137],
          [32.859741, 39.933365]
        ]
      },
      "properties": {
        "name": "İstanbul-Ankara Yolu"
      }
    },
    {
      "id": 4,
      "type": "Feature",
      "geometry": {
        "type": "Polygon",
        "coordinates": [
          [
            [30.632813, 36.102376],
            [32.695313, 36.102376],
            [32.695313, 37.188268],
            [30.632813, 37.188268],
            [30.632813, 36.102376]
          ]
        ]
      },
      "properties": {
        "name": "Antalya Bölgesi"
      }
    }
  ]
}
```

### Leaflet ile Harita Ekleme

### Adım 1: Leaflet Kütüphanesini Dahil Etme

HTML dosyanıza Leaflet CSS ve JS dosyalarını ekleyin:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>Leaflet Harita</title>
    <link
      rel="stylesheet"
      href="https://unpkg.com/leaflet@1.7.1/dist/leaflet.css"
    />
    <style>
      #map {
        height: 500px;
      }
    </style>
  </head>
  <body>
    <div id="map"></div>
    <script src="https://unpkg.com/leaflet@1.7.1/dist/leaflet.js"></script>
    <script src="app.js"></script>
  </body>
</html>
```

### Adım 2: Harita ve GeoJSON Verisi

`app.js` dosyasına aşağıdaki kodları ekleyerek haritayı oluşturun ve GeoJSON verisini ekleyin:

```javascript
document.addEventListener("DOMContentLoaded", function () {
  var map = L.map("map").setView([39.9334, 32.8597], 6);

  L.tileLayer("https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png", {
    maxZoom: 18,
  }).addTo(map);

  fetch("http://localhost:3000/locations")
    .then((response) => response.json())
    .then((data) => {
      L.geoJSON(data, {
        onEachFeature: function (feature, layer) {
          if (feature.properties && feature.properties.name) {
            layer.bindPopup(feature.properties.name);
          }
        },
      }).addTo(map);
    });
});

![Sertifika](/assets/gim / leaflet_json_server.png);
```

### OpenLayers ile Harita Ekleme

### Adım 1: OpenLayers Kütüphanesini Dahil Etme

HTML dosyanıza OpenLayers CSS ve JS dosyalarını ekleyin:

```html
<!DOCTYPE html>
<html>
  <head>
    <title>OpenLayers Harita</title>
    <link rel="stylesheet" href="https://openlayers.org/en/v6.5.0/css/ol.css" />
    <style>
      #map {
        height: 500px;
        width: 100%;
      }
    </style>
  </head>
  <body>
    <div id="map" class="map"></div>
    <script src="https://openlayers.org/en/v6.5.0/build/ol.js"></script>
    <script src="app.js"></script>
  </body>
</html>
```

### Adım 2: Harita ve GeoJSON Verisi

`app.js` dosyasına aşağıdaki kodları ekleyerek haritayı oluşturun ve GeoJSON verisini ekleyin:

```javascript
document.addEventListener("DOMContentLoaded", function () {
  var map = new ol.Map({
    target: "map",
    layers: [
      new ol.layer.Tile({
        source: new ol.source.OSM(),
      }),
    ],
    view: new ol.View({
      center: ol.proj.fromLonLat([32.8597, 39.9334]),
      zoom: 6,
    }),
  });

  fetch("http://localhost:3000/locations")
    .then((response) => response.json())
    .then((data) => {
      if (Array.isArray(data)) {
        var geojsonFormat = new ol.format.GeoJSON();
        var features = geojsonFormat.readFeatures(
          {
            type: "FeatureCollection",
            features: data,
          },
          {
            featureProjection: "EPSG:3857",
          }
        );

        var vectorSource = new ol.source.Vector({
          features: features,
        });

        var vectorLayer = new ol.layer.Vector({
          source: vectorSource,
        });

        map.addLayer(vectorLayer);
      } else {
        console.error("GeoJSON verisi geçersiz format.");
      }
    })
    .catch((error) => {
      console.error("GeoJSON verisi alınamadı veya uygun değil", error);
    });
});

![Sertifika](/assets/gim / openlayers_json_server.png);
```

Bu adımlarla, JSON Server üzerinden sağlanan noktalar, çizgiler ve alanlar (poligonlar) içeren GeoJSON verisini Leaflet veya OpenLayers kullanarak haritaya ekleyebilirsiniz. Blogunuzda bu rehberi paylaşarak, okuyucularınıza JSON Server ve GeoJSON verilerini haritaya ekleme konusunda kapsamlı bilgi sunabilirsiniz. JSON Server ile ilgili daha fazla bilgiye [resmi dökümantasyon](https://github.com/typicode/json-server) sayfasından, Leaflet ve OpenLayers hakkında ise [Leaflet dökümantasyonu](https://leafletjs.com/) ve [OpenLayers dökümantasyonu](https://openlayers.org/) sayfalarından ulaşabilirsiniz.
