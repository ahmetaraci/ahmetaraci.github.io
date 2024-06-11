---
title: Oh My Posh ile Windows 11 Terminalinizi Renklendirin
date: 11/06/2024 10:00:00 +0300
categories: [turkce]
tags: [OhMyPosh, PowerShell, Kişiselleştirme]
---

Youtube'da birçok developerda gördüğüm renkli terminali denemek için kolları sıvıyorum, deneyimlerimi size aktarıyorum. Bu yazıda, Oh My Posh'un ne olduğunu, neden ihtiyacımız olduğunu ve nasıl yükleneceğini adım adım anlatacağım.

## Oh My Posh Nedir?

Oh My Posh, Windows Terminal, PowerShell ve WSL için geliştirilmiş bir prompt teması yöneticisidir. Terminalinizi daha estetik ve bilgi dolu hale getiren, özelleştirilebilir temalar sunar. Oh My Posh ile terminaliniz sadece bir komut satırı olmaktan çıkar, aynı zamanda çalışmanızı daha verimli hale getiren bir araç haline gelir.

## Neden Oh My Posh Kullanmalıyız?

### 1. Görsellik ve Estetik

Oh My Posh, terminalinizi görsel olarak çekici hale getirir. Renkli ve temalı promptlar, çalışmanızı daha keyifli hale getirir.

### 2. Bilgilendirici Promptlar

Çalıştığınız dizin, git durumu, saat ve tarih gibi bilgileri prompt üzerinde görüntüleyebilirsiniz. Bu, iş akışınızı hızlandırır ve gereksiz komut yazma ihtiyacını azaltır.

### 3. Kişiselleştirme

Oh My Posh, geniş bir tema yelpazesi sunar ve kendi temanızı oluşturmanıza imkan tanır. Terminalinizi kendi zevkinize göre özelleştirebilirsiniz.

## Nasıl Kurulur?

### 1. Windows Terminal Kurulumu

Eğer henüz Windows Terminal yüklü değilse, [Microsoft Store](https://aka.ms/terminal) üzerinden indirip kurabilirsiniz.

### 2. PowerShell Kurulumu

Oh My Posh, PowerShell 7 veya üstü ile çalışır. PowerShell'i yüklemek için [resmi PowerShell sayfasını](https://github.com/PowerShell/PowerShell) ziyaret edebilirsiniz.

### 3. Oh My Posh Kurulumu

#### 3.1 Oh My Posh'u İndirin

Öncelikle, PowerShell veya Windows Terminal'inizi açın ve aşağıdaki komutu çalıştırarak Oh My Posh'u indirin (Administrator olarak çalıştırınız):

```powershell
winget install JanDeDobbeleer.OhMyPosh -s winget
```

Ekranda bir değişiklik olmadığını gördünüz endişelenmeyiniz. Çünkü Oh My Posh daha başlatılmadı.

#### 3.2 Oh My Posh'u Çağırın

```powershell
oh-my-posh
```

Komutu ile çağırdığınızda komutun tanınmadığını göreceksiniz. Bunun için terminali kapatıp tekrar admin yetkileriyle başlatarak deneyiniz lütfen.

---

**oh-my-posh is a cross platform tool to render your prompt.
It can use the same configuration everywhere to offer a consistent
experience, regardless of where you are. For a detailed guide
on getting started, have a look at the docs at https://ohmyposh.dev**

---

gibi bir çıktıyla karşılaştığınızda Oh My Posh kurulmuş demektir.

Terminali açıp kapatmanıza rağmen

```powershell
oh-my-posh
```

komutunu terminal tanımazsa Oh My Posh'u path e eklemeniz gerekecektir.

```powershell
$env:Path += ";C:\Users\user\AppData\Local\Programs\oh-my-posh\bin"
```

Aşağıdaki komutla Oh my Posh'u default temayla başlatalım.

```powershell
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\jandedobbeleer.omp.json" | Invoke-Expression
```

#### 3.3 Oh My Posh'u Terminal Açılırken Otomatik Başlatma ve Tema Ayarı

Oh My Posh'un hangi tema ile çalışacağını seçmek için yüklü temaları listemek için komutu kullanınız:

```powershell
Get-PoshThemes
```

Beğendiğiniz temanın ismini terminal profiline kaydedeceğiz.

PowerShell profil dosyanıza Oh My Posh'u ekleyerek temanızı kalıcı hale getirebilirsiniz. Profil dosyanızı açmak için:

```powershell
notepad $PROFILE
```

Bu işlemi ilk defa yapıyorsanız muhtemelen Notepad : "Sistem Belirtilen Yolu Bulamıyor." diye bir uyarı fırlatacaktır.
Bunun için ise bu dosyayı zorla oluşturmak gerekir.

```powershell
New-Item -Path $PROFILE -Type File -Force
```

Tekrar profile dosyasını açmayı deneyelim.

```powershell
notepad $PROFILE
```

Açılan dosyanın sonuna şu satırı ekleyin:

```powershell
oh-my-posh init pwsh --config "$env:POSH_THEMES_PATH\jandedobbeleer.omp.json" | Invoke-Expression
```

Burada jandedobbeleer default temanın ismidir, tema listesinden beğendiğiniz temanın ismini bununla değiştirmelisiniz.

Bu şekilde, her yeni terminal açtığınızda seçtiğiniz tema otomatik olarak yüklenecektir.

## Sonuç

Oh My Posh ile terminalinizi renklendirip daha efektif hale getirerek çalışma deneyiminizi geliştirebilirsiniz. Görsel açıdan zengin ve bilgilendirici promptlar, iş akışınızı hızlandırır ve kişiselleştirme imkanı sunar. Hemen Oh My Posh'u kurun ve terminalinizi dönüştürün!

Umarım bu rehber sizin için faydalı olmuştur. Sorularınız veya geri bildirimleriniz için benimle iletişime geçebilirsiniz.
