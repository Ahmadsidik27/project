# 🏷️ Panduan Konfigurasi Logo AutoTech Academy

Panduan lengkap untuk mengelola logo dan branding website AutoTech Academy.

## 📁 Struktur File Logo

```
src/config/
├── logos.ts           # Konfigurasi semua logo
src/components/
├── Logo.tsx           # Komponen logo yang dapat digunakan kembali
src/hooks/
├── useLogo.ts         # Hook untuk mengelola logo
```

## 🖼️ Jenis Logo yang Tersedia

### 1. **Logo Utama**
- **With Text**: Logo dengan teks "AutoTech Academy"
- **Icon Only**: Hanya icon/simbol tanpa teks
- **Berbagai Ukuran**: Small, Medium, Large, XLarge

### 2. **Logo Berdasarkan Tema**
- **Light**: Untuk background terang
- **Dark**: Untuk background gelap  
- **Color**: Logo berwarna penuh

### 3. **Logo Khusus**
- **Favicon**: Icon untuk browser tab
- **Social Media**: Logo untuk platform sosial
- **Email**: Logo untuk email dan signature
- **Watermark**: Logo transparan untuk watermark

## 🔧 Cara Mengubah Logo

### 1. **Mengubah Logo Utama**

```typescript
// Edit src/config/logos.ts
export const logos = {
  main: {
    withText: {
      light: 'URL_LOGO_DENGAN_TEKS_TERANG',
      dark: 'URL_LOGO_DENGAN_TEKS_GELAP',
      color: 'URL_LOGO_DENGAN_TEKS_BERWARNA'
    },
    iconOnly: {
      light: 'URL_ICON_TERANG',
      dark: 'URL_ICON_GELAP', 
      color: 'URL_ICON_BERWARNA'
    }
  }
}
```

### 2. **Mengubah Logo Berdasarkan Ukuran**

```typescript
export const logos = {
  main: {
    sizes: {
      small: 'URL_LOGO_KECIL',    // 120x40px
      medium: 'URL_LOGO_SEDANG',  // 200x60px
      large: 'URL_LOGO_BESAR',    // 300x100px
      xlarge: 'URL_LOGO_SANGAT_BESAR' // 400x120px
    }
  }
}
```

### 3. **Mengubah Favicon**

```typescript
export const logos = {
  favicon: {
    ico: '/favicon.ico',
    png16: '/favicon-16x16.png',
    png32: '/favicon-32x32.png',
    png192: '/android-chrome-192x192.png',
    png512: '/android-chrome-512x512.png',
    appleTouchIcon: '/apple-touch-icon.png'
  }
}
```

## 🎯 Menggunakan Logo di Komponen

### 1. **Menggunakan Komponen Logo**

```typescript
import Logo from '../components/Logo';

// Logo untuk header desktop
<Logo 
  context="header"
  device="desktop"
  className="h-8 w-auto"
/>

// Logo untuk header mobile
<Logo 
  context="header"
  device="mobile" 
  className="h-8 w-8"
/>

// Logo custom
<Logo 
  variant="iconOnly"
  theme="color"
  size="medium"
  className="h-10 w-10"
/>
```

### 2. **Menggunakan Hook useLogo**

```typescript
import { useLogo } from '../hooks/useLogo';

const MyComponent = () => {
  const { logoUrl, isLoading, error } = useLogo({
    context: 'header',
    device: 'desktop',
    preload: true
  });

  if (isLoading) return <div>Loading logo...</div>;
  if (error) return <div>Error loading logo</div>;

  return <img src={logoUrl} alt="Logo" />;
};
```

### 3. **Menggunakan Helper Functions**

```typescript
import { getLogo, getLogoBySize, getFavicon } from '../config/logos';

// Mendapatkan logo berdasarkan konteks
const headerLogo = getLogo('header', 'desktop');

// Mendapatkan logo berdasarkan ukuran
const mediumLogo = getLogoBySize('medium');

// Mendapatkan favicon
const favicon = getFavicon('png32');
```

## 📱 Logo Responsive

### Konfigurasi Responsive

```typescript
// src/config/logos.ts
export const logoConfig = {
  usage: {
    header: {
      desktop: { variant: 'withText', theme: 'color', size: 'medium' },
      mobile: { variant: 'iconOnly', theme: 'color', size: 'small' }
    }
  }
}
```

### Implementasi Responsive

```typescript
import { useResponsiveLogo } from '../hooks/useLogo';

const ResponsiveHeader = () => {
  const { logoUrl } = useResponsiveLogo('header');
  
  return <img src={logoUrl} alt="AutoTech Academy" />;
};
```

## 🎨 Konteks Penggunaan Logo

### 1. **Header**
- Desktop: Logo dengan teks, ukuran medium
- Mobile: Icon only, ukuran small

### 2. **Footer**  
- Logo dengan teks, tema light, ukuran small

### 3. **Loading**
- Icon only, tema color, ukuran medium

### 4. **Email**
- Logo dengan teks, tema color, ukuran medium

## 📋 Checklist Penggantian Logo

### ✅ Persiapan File Logo

- [ ] Logo dengan teks (light, dark, color)
- [ ] Icon only (light, dark, color)
- [ ] Berbagai ukuran (small, medium, large, xlarge)
- [ ] Favicon (.ico, .png 16x16, 32x32, 192x192, 512x512)
- [ ] Apple touch icon (180x180px)
- [ ] Logo untuk social media

### ✅ Format dan Ukuran

- [ ] Format: PNG dengan background transparan
- [ ] SVG untuk scalability (opsional)
- [ ] Ukuran sesuai dengan spesifikasi
- [ ] Optimasi file size

### ✅ Testing

- [ ] Logo tampil dengan benar di header
- [ ] Logo responsive di mobile
- [ ] Favicon muncul di browser tab
- [ ] Logo di footer terlihat jelas
- [ ] Kontras yang baik di berbagai background

## 🛠️ Tools dan Tips

### Rekomendasi Tools
- **Canva**: Untuk design logo sederhana
- **Figma**: Untuk design profesional
- **SVGOMG**: Untuk optimasi SVG
- **TinyPNG**: Untuk kompres PNG

### Tips Design Logo
1. **Simplicity**: Logo harus sederhana dan mudah dikenali
2. **Scalability**: Harus terlihat baik di ukuran kecil dan besar
3. **Versatility**: Berfungsi di berbagai background dan konteks
4. **Memorable**: Mudah diingat dan unik
5. **Relevant**: Sesuai dengan brand otomotif

### Tips Teknis
1. **Format PNG**: Untuk logo dengan detail dan transparansi
2. **Format SVG**: Untuk scalability sempurna
3. **Optimasi**: Kompres file tanpa mengurangi kualitas
4. **Naming**: Gunakan nama file yang deskriptif
5. **CDN**: Gunakan CDN untuk loading yang cepat

## 🔍 Troubleshooting

### Logo Tidak Muncul
1. Cek URL logo valid dan accessible
2. Pastikan format file didukung (PNG, JPG, SVG)
3. Periksa CORS policy untuk external images
4. Cek console browser untuk error

### Logo Blur atau Pixelated
1. Gunakan ukuran yang sesuai dengan display
2. Pertimbangkan menggunakan format SVG
3. Pastikan resolusi cukup tinggi
4. Gunakan format yang tepat (PNG untuk transparansi)

### Logo Tidak Responsive
1. Cek konfigurasi responsive di `logoConfig`
2. Pastikan hook `useResponsiveLogo` digunakan dengan benar
3. Test di berbagai ukuran layar
4. Periksa CSS untuk responsive behavior

## 📞 Support

Untuk bantuan konfigurasi logo:
1. Periksa dokumentasi ini
2. Cek file `src/config/logos.ts`
3. Test menggunakan komponen `Logo`
4. Buat issue untuk bantuan teknis

## 🎯 Best Practices

### Performance
- Preload logo penting untuk loading cepat
- Gunakan format yang optimal (WebP jika didukung)
- Kompres file tanpa mengurangi kualitas
- Implementasi lazy loading untuk logo non-critical

### Accessibility
- Selalu sediakan alt text yang deskriptif
- Pastikan kontras yang cukup
- Support untuk screen readers
- Keyboard navigation friendly

### SEO
- Gunakan nama file yang SEO-friendly
- Tambahkan structured data untuk logo
- Optimasi untuk search engines
- Consistent branding across pages

### Maintenance
- Dokumentasikan semua perubahan logo
- Backup file logo original
- Version control untuk tracking changes
- Regular audit untuk broken images