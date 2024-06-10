---
title: Docker ile Ubuntu Server'da Geoserver Kurulumu
date: 13/05/2024 12:00:00 +0300
categories: [turkce]
tags: [docker, ubuntu, geoserver]
---

# Docker ile Ubuntu Server'da Geoserver Kurulumu

Bu blog yazısında, yeni kurulmuş bir Ubuntu sunucuda Docker kullanarak Geoserver'ı nasıl kuracağımızı adım adım göstereceğim.

## Adım 1: Sunucuya SSH Erişimi

Öncelikle, sunucuya SSH erişimi sağlayarak işe başlıyoruz. Terminal veya SSH istemcisini kullanarak sunucuya erişiyoruz.

```bash
ssh kullanici_adiniz@server_ipiniz
```

## Adım 2: Docker Kurulumu

Docker'ı sunucuya kurmak için aşağıdaki adımları izliyoruz.

```bash
sudo apt update
sudo apt install apt-transport-https ca-certificates curl software-properties-common
curl -fsSL https://download.docker.com/linux/ubuntu/gpg | sudo apt-key add -
sudo add-apt-repository "deb [arch=amd64] https://download.docker.com/linux/ubuntu $(lsb_release -cs) stable"
sudo apt update
sudo apt install docker-ce

```

## Adım 3: Geoserver YML Dosyası Oluşturma

Geoserver'ı Docker konteynerı olarak çalıştırmak için bir Docker Compose dosyası oluşturuyoruz. Örnek bir YML dosyası şu şekilde olabilir:

```yaml
version: "3"

services:
  geoserver:
    image: kartoza/geoserver:latest
    ports:
      - "8080:8080" # Geoserver'ı 8080 portunda çalıştırıyoruz.
    environment:
      - GEOSERVER_MEMORY_OPTS=-Xms8g -Xmx8g
```

## Adım 4: Docker Compose ile Konteynerı Çalıştırma

Yukarıdaki YML dosyasını kullanarak Docker Compose ile Geoserver konteynerını başlatıyoruz.

```bash
docker-compose up -d

```

## Adım 4: Erişim Kontrolü

Konteynerları başarıyla çalıştırdıktan sonra, tarayıcınızı kullanarak Geoserver'a erişebilirsiniz. Varsayılan olarak, Geoserver'ı http://server_ipniz:8080/geoserver adresinden görebilirsiniz.
