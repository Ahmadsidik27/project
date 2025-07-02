# 📋 Panduan Konfigurasi AutoTech Academy

Panduan lengkap untuk mengelola gambar, fitur, konten, dan tema website AutoTech Academy.

## 📁 Struktur File Konfigurasi

```
src/config/
├── images.ts      # Konfigurasi semua gambar
├── features.ts    # Konfigurasi fitur website
├── content.ts     # Konfigurasi teks dan konten
├── theme.ts       # Konfigurasi tema dan styling
└── index.ts       # Export semua konfigurasi
```

## 🖼️ Mengelola Gambar (`src/config/images.ts`)

### Mengubah Gambar Existing

```typescript
// Contoh mengubah gambar hero
export const images = {
  hero: {
    main: 'URL_GAMBAR_BARU_ANDA',
    automotive: 'URL_GAMBAR_AUTOMOTIVE_BARU',
    diagnostic: 'URL_GAMBAR_DIAGNOSTIC_BARU'
  }
}
```

### Menambah Kategori Gambar Baru

```typescript
// Tambahkan kategori baru
export const images = {
  // ... kategori existing
  newCategory: {
    image1: 'URL_GAMBAR_1',
    image2: 'URL_GAMBAR_2'
  }
}
```

### Menggunakan Gambar di Komponen

```typescript
import { images, getImageById } from '../config/images';

// Cara 1: Akses langsung
const heroImage = images.hero.main;

// Cara 2: Menggunakan helper function
const courseImage = getImageById('course', '1');
```

## ⚡ Mengelola Fitur (`src/config/features.ts`)

### Mengaktifkan/Menonaktifkan Fitur

```typescript
// Mengubah status fitur
export const features = {
  elearning: {
    quizzes: {
      enabled: true, // Ubah dari false ke true
      name: 'Kuis dan Ujian',
      description: 'Sistem evaluasi pembelajaran'
    }
  }
}
```

### Menambah Fitur Baru

```typescript
// Tambahkan fitur baru
export const features = {
  elearning: {
    // ... fitur existing
    newFeature: {
      enabled: true,
      name: 'Fitur Baru',
      description: 'Deskripsi fitur baru'
    }
  }
}
```

### Mengecek Status Fitur

```typescript
import { isFeatureEnabled } from '../config/features';

// Cek apakah fitur aktif
if (isFeatureEnabled('elearning', 'quizzes')) {
  // Tampilkan komponen kuis
}
```

## 📝 Mengelola Konten (`src/config/content.ts`)

### Mengubah Teks Website

```typescript
// Mengubah konten hero
export const content = {
  home: {
    hero: {
      title: 'Judul Baru Anda',
      subtitle: 'Subtitle baru yang menarik',
      primaryButton: 'Tombol Utama',
      secondaryButton: 'Tombol Kedua'
    }
  }
}
```

### Menambah Konten Baru

```typescript
// Tambahkan section baru
export const content = {
  // ... konten existing
  newSection: {
    title: 'Section Baru',
    items: ['Item 1', 'Item 2', 'Item 3']
  }
}
```

### Menggunakan Konten di Komponen

```typescript
import { getContent } from '../config/content';

// Mendapatkan konten dengan path
const heroTitle = getContent('home.hero.title');
```

## 🎨 Mengelola Tema (`src/config/theme.ts`)

### Mengubah Warna

```typescript
// Mengubah warna primary
export const theme = {
  colors: {
    primary: {
      500: '#your-new-color', // Warna utama
      600: '#your-darker-color', // Warna hover
      // ... shade lainnya
    }
  }
}
```

### Mengubah Komponen Styling

```typescript
// Mengubah styling button
export const theme = {
  components: {
    button: {
      primary: {
        bg: 'bg-your-color',
        hover: 'hover:bg-your-hover-color',
        // ... properti lainnya
      }
    }
  }
}
```

### Menggunakan Tema di Komponen

```typescript
import { getButtonClass, getColor } from '../config/theme';

// Mendapatkan class button
const buttonClass = getButtonClass('primary');

// Mendapatkan warna
const primaryColor = getColor('primary', 500);
```

## 🛠️ Utility Functions

### Image Helper (`src/utils/imageHelper.ts`)

```typescript
import { getCategoryImage, optimizePexelsImage } from '../utils/imageHelper';

// Mendapatkan gambar dengan ukuran optimal
const courseImage = getCategoryImage('course', '1', { width: 400, height: 300 });

// Mengoptimalkan gambar Pexels
const optimizedImage = optimizePexelsImage(imageUrl, 800, 600);
```

## 📋 Checklist Konfigurasi

### ✅ Sebelum Deploy

- [ ] Semua gambar sudah diganti dengan gambar yang sesuai
- [ ] Fitur yang tidak diperlukan sudah dinonaktifkan
- [ ] Konten sudah disesuaikan dengan brand Anda
- [ ] Warna tema sudah sesuai dengan identitas visual
- [ ] Informasi kontak sudah diperbarui

### ✅ Testing

- [ ] Semua gambar loading dengan baik
- [ ] Fitur yang diaktifkan berfungsi normal
- [ ] Teks dan konten tampil dengan benar
- [ ] Tema dan styling konsisten di semua halaman

## 🔧 Tips Optimasi

### Gambar
- Gunakan format WebP untuk performa terbaik
- Kompres gambar sebelum upload
- Gunakan CDN untuk loading yang lebih cepat
- Sesuaikan ukuran gambar dengan kebutuhan

### Fitur
- Nonaktifkan fitur yang tidak diperlukan untuk performa
- Test fitur baru di environment development dulu
- Dokumentasikan perubahan fitur

### Konten
- Gunakan teks yang SEO-friendly
- Pastikan konsistensi tone dan style
- Update konten secara berkala

### Tema
- Gunakan sistem warna yang konsisten
- Test kontras warna untuk accessibility
- Pastikan responsive di semua device

## 🆘 Troubleshooting

### Gambar Tidak Muncul
1. Cek URL gambar valid
2. Pastikan gambar accessible secara public
3. Periksa CORS policy jika menggunakan external images

### Fitur Tidak Berfungsi
1. Cek status `enabled` di konfigurasi
2. Pastikan import sudah benar
3. Periksa console untuk error

### Styling Tidak Sesuai
1. Cek konfigurasi tema
2. Pastikan Tailwind CSS classes valid
3. Clear cache browser

## 📞 Support

Jika mengalami kesulitan dalam konfigurasi, silakan:
1. Periksa dokumentasi ini kembali
2. Cek file example di folder `src/config/`
3. Buat issue di repository untuk bantuan lebih lanjut