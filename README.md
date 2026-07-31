# 🛸 Cockpit CRM

> **Şirketinizin Dijital Kontrol Kokpiti** — Müşteri ilişkileri, satış kanalları, ekip yönetimi ve akıllı otomasyonları tek bir platformda birleştiren nesil yeni SaaS CRM platformu.

---

## 🌟 Cockpit CRM Nedir?

**Cockpit CRM**; modern işletmelerin, büyümekte olan SaaS girişimlerinin ve kurumsal ekiplerin müşteri yönetiminden satış süreçlerine, çalışan rollerinden entegrasyonlara kadar tüm operasyonlarını tek bir merkezden yönetmesini sağlayan bütüncül bir CRM ve şirket yönetim sistemidir.

- **Özel Şirket Subdomain'leri (`*.app.cockpitcrm.io`):** Her şirket kendisine özel alt alan adında izole bir CRM alanına sahip olur.
- **Şirket & Lisans Yönetimi (`manager.cockpitcrm.io`):** Şirket sahipleri için çalışan davetleri, lisanslar, tehlikeli alan yönetimi ve 2FA güvenlik ayarları.
- **Süper Admin Paneli (`masters.cockpitcrm.io`):** Tüm platform istatistikleri, abonelikler, sistem logları ve kiracı (tenant) izolasyonu.
- **Yüksek Güvenlik & Yetkilendirme:** Granüler (ince taneli) rol ve izin matrisi, Google Authenticator (2FA) desteği, güvenli oturum yönetimi.

---

## 📐 Mimari Yapı (Monorepo)

Cockpit CRM projesi yüksek performans, modülerlik ve ölçeklenebilirlik için **pnpm Workspaces** ve **Turborepo** altyapısıyla geliştirilmiştir:

```text
cockpit-crm/
├── apps/
│   ├── gateway-api/       # NestJS + TypeORM + PostgreSQL API Gateway (cockpit-gw.cockpitcrm.io)
│   ├── user-dashboard/    # Next.js 16 + React 19 Şirket Yönetim Paneli (manager.cockpitcrm.io)
│   ├── crm-dashboard/     # Next.js 16 + React 19 Müşteri & Satış Workspace (app.cockpitcrm.io)
│   └── admin-dashboard/   # Next.js 16 + React 19 Süper Admin Paneli (masters.cockpitcrm.io)
```

---

## 🔑 Öne Çıkan Özellikler

### 👥 1. Müşteri & Fırsat Yönetimi (Sales Pipeline)
- Sürükle-bırak destekli görsel satış boru hatları (Kanban & Tablo görünümü)
- Müşteri segmentasyonu, etiketleme ve çifte kayıt (duplicate) tespiti
- Fırsat takibi, teklif hazırlama ve sipariş dönüşümü

### 🛡️ 2. Şirket & Çalışan Rol Yönetimi
- Şirket kurucuları için özelleştirilebilir rol matrisi (`Yönetici`, `Satış Temsilcisi`, `Destek`, vb.)
- Çalışan ekleme/çıkarma, şifre sıfırlama ve anlık durum güncelleme
- SMS (OTP) ve E-posta doğrulamalı güvenli davet sistemi

### 🔒 3. Güvenlik & Doğrulama
- **2-Factor Authentication (2FA):** Google Authenticator / Authy ile ekstra güvenlik katmanı
- **Özel Header Güvenliği:** `x-cockpit-app` ve `x-tenant-slug` başlık doğrulama
- **Oturum Yönetimi:** Tüm aktif cihaz oturumlarını görüntüleme ve tek tıkla sonlandırma

### 🎨 4. Sosyal Medya & Link Önizleme Uyumlu (OpenGraph)
- WhatsApp, iMessage, LinkedIn, Twitter ve Google tarayıcıları için %100 uyumlu statik `<head>` OpenGraph etiketleri
- Dinamik sayfa başlıkları (`document.title`) ve yüksek çözünürlüklü marka ikonları

---

## 🛠️ Kurulum ve Geliştirme

### Ön Gereksinimler
- Node.js (>= 20.x)
- pnpm (>= 9.x veya 11.x)
- PostgreSQL & Redis

### 1. Bağımlılıkları Yükleyin
```bash
pnpm install
```

### 2. Çevre Değişkenlerini Ayarlayın
Kök dizinde ve ilgili `apps/` klasörlerinde yer alan `.env.example` dosyalarını kopyalayarak `.env.local` oluşturun:
```bash
# gateway-api için
DATABASE_URL="postgresql://postgres:postgres@localhost:5432/cockpit_crm"
REDIS_URL="redis://localhost:6379"

# user-dashboard & crm-dashboard için
NEXT_PUBLIC_API_URL="https://cockpit-gw.cockpitcrm.io"
```

### 3. Geliştirici Sunucularını Başlatın
```bash
pnpm dev
```

---

## 📄 Lisans

Bu proje **UNLICENSED** (Özel / Lisanslı) olarak geliştirilmektedir. Tüm hakları saklıdır.

© 2026 **Cockpit CRM Team** — [cockpitcrm.io](https://cockpitcrm.io)
