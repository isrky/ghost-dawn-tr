# Dawn

Okuyucunun tercihlerine göre uyum sağlayan, son derece işlevsel bir [Ghost](https://github.com/TryGhost/Ghost) teması. Kolaylıkla okumalarını, aramalarını, abone olmalarını, gezinmelerini ve daha fazlasını yapmalarını sağlayın.

**Demo: https://dawn.ghost.io**

---

## 🌍 Türkçe (tr) ve Azerbaycan Türkçesi (az) Dil Desteği

Bu sürümle birlikte Dawn temasına **Türkçe (tr)** ve **Azerbaycan Türkçesi (az)** dil destekleri eklenmiştir! Artık ziyaretçileriniz temayı tamamen kendi dillerinde deneyimleyebilir.

### Dil Desteğini Etkinleştirme
Ghost yönetim panelinizde bu dilleri aktif hale getirmek için:
1. Ghost sitenizin yönetim paneline (Admin) gidin.
2. **Settings (Ayarlar) > General (Genel) > Publication Language (Yayın Dili)** bölümüne gidin.
3. Türkçe için `tr`, Azerbaycan Türkçesi için `az` yazarak değişiklikleri kaydedin.

---

## Kurulum Talimatları

1. [Bu temayı indirin](https://github.com/TryGhost/Dawn/archive/main.zip)
2. Ghost yönetim paneline giriş yapın ve zip dosyasını yüklemek için `Settings > Design (Tasarım)` ayarlarına gidin.

## Geliştirme

Stiller, gelecekteki CSS özelliklerini polyfill etmek için Gulp/PostCSS kullanılarak derlenir. Bilgisayarınızda global olarak [Node](https://nodejs.org/), [Yarn](https://yarnpkg.com/) ve [Gulp](https://gulpjs.com) kurulu olmalıdır. Ardından, temanın kök dizininde şu komutları çalıştırın:

```bash
# Bağımlılıkları Yükle
yarn

# Derleme Yap ve Değişiklikleri İzle
yarn dev
```

Artık `/assets/css/` altındaki dosyaları düzenleyebilirsiniz. Bu dosyalar otomatik olarak `/assets/built/` dizinine derlenecektir.

Temayı sitenize yüklemeye hazır bir paket haline getirmek için `zip` Gulp görevini kullanabilirsiniz. Bu görev tema dosyalarını `dist/dawn.zip` olarak paketler:

```bash
yarn zip
```

## Katkıda Bulunma

Bu depo, [TryGhost/Themes](https://github.com/TryGhost/Themes) monorepo deposuyla otomatik olarak senkronize edilmektedir. Katkıda bulunmak veya bir sorun bildirmek istiyorsanız, resmi temalarımızın geliştirildiği ana depo olan [TryGhost/Themes](https://github.com/TryGhost/Themes) adresini ziyaret edin.

### Tema Çevirileri
Çevirileri nasıl düzenleyeceğiniz veya yeni çevirilerle nasıl katkıda bulunacağınız hakkında bilgi edinmek için lütfen `@Tryghost/Themes/theme-translations/README.md` dosyasını inceleyin.

## Telif Hakkı ve Lisans

Copyright (c) 2013-2026 Ghost Foundation - [MIT lisansı](LICENSE) kapsamında lisanslanmıştır.
