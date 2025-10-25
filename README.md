# 🚀 Crypto AI Predictor

Website prediksi harga cryptocurrency berbasis AI dengan analisis teknikal real-time. Aplikasi ini menggunakan React.js, deep learning predictions, dan data pasar dari CoinGecko API.

## ✨ Fitur Utama

### 📊 Dashboard
- **Real-time Price Tracking**: Harga cryptocurrency dari 6 koin utama (BTC, ETH, SOL, ADA, DOT, AVAX)
- **AI Predictions**: Prediksi harga 24 jam ke depan dengan confidence intervals
- **Interactive Charts**: Grafik harga dengan indikator teknikal (MA7, MA25)
- **Price Cards**: Tampilan harga saat ini, prediksi AI, dan confidence range

### 🔍 Analisis Teknikal
- **RSI (Relative Strength Index)**: Indikator momentum untuk oversold/overbought
- **Moving Averages**: MA7 dan MA25 untuk trend analysis
- **AI Insight Box**: Analisis otomatis berbahasa Indonesia dengan rekomendasi trading
- **Technical Signals**: Signal BULLISH, BEARISH, atau SIDEWAYS

### 📈 Market Data
- **Market Overview Table**: Tabel lengkap dengan sorting dan filtering
- **Watchlist**: Tandai cryptocurrency favorit (tersimpan di LocalStorage)
- **Real-time Updates**: Data diperbarui setiap 60 detik
- **Detailed Metrics**: Volume, market cap, dan perubahan harga 24 jam

### 🤖 AI Analytics
- **Model Performance**: Metrik akurasi model (R², RMSE, MAE, MAPE)
- **Model Comparison**: Perbandingan performa LSTM, CNN-LSTM, NARX, GRU
- **Visual Charts**: Grafik perbandingan antar model

### 🎨 UI/UX
- **Dark Theme**: Design modern dengan dominan warna gelap (seperti TradingView)
- **Inter Font**: Typography profesional dan clean
- **Responsive Design**: Optimal di desktop dan mobile
- **Smooth Animations**: Transisi halus dan micro-interactions

## 🛠️ Teknologi

- **Frontend**: React 18 + TypeScript + Vite
- **Styling**: Tailwind CSS
- **Charts**: Recharts
- **Icons**: Lucide React
- **API**: CoinGecko (market data)
- **State Management**: React Hooks (useState, useEffect)

## 📦 Instalasi

### Prerequisites
- Node.js 16+ dan npm/yarn
- Git

### Langkah Instalasi

1. **Clone repository**
```bash
git clone <repository-url>
cd crypto-ai-predictor
```

2. **Install dependencies**
```bash
npm install
```

3. **Konfigurasi Environment Variables** (Opsional)

Buat file `.env` di root project:

```env
# URL API Model AI Anda (opsional)
VITE_MODEL_API_URL=https://your-model-api.com

# Jika tidak diset, aplikasi akan menggunakan demo predictions
```

4. **Jalankan development server**
```bash
npm run dev
```

Aplikasi akan berjalan di `http://localhost:5173`

5. **Build untuk production**
```bash
npm run build
```

Output akan ada di folder `dist/`

## 🔗 Integrasi API Model AI

### Endpoint yang Diperlukan

Jika Anda ingin mengintegrasikan model AI Anda sendiri, API harus menyediakan endpoint berikut:

#### 1. Prediction Endpoint
```
GET /predict?coin=BTC&interval=1h
```

**Response Format:**
```json
{
  "coin": "BTC",
  "predicted_price": 45000.00,
  "confidence_lower": 44500.00,
  "confidence_upper": 45500.00,
  "timestamp": "2024-10-24T10:00:00Z",
  "interval": "1h"
}
```

#### 2. Model Metrics Endpoint
```
GET /metrics?model=LSTM
```

**Response Format:**
```json
{
  "model_name": "LSTM",
  "r2_score": 0.8523,
  "rmse": 542.34,
  "mae": 412.56,
  "mape": 3.45
}
```

### Menggunakan Demo Mode

Jika tidak ada API model, aplikasi akan otomatis menggunakan **mock predictions** yang realistis untuk demonstrasi. Tidak perlu konfigurasi tambahan!

## 📁 Struktur Project

```
crypto-ai-predictor/
├── src/
│   ├── components/          # Komponen React
│   │   ├── AIAnalytics.tsx      # AI model analytics
│   │   ├── AIInsightBox.tsx     # Technical insight widget
│   │   ├── CoinSelector.tsx     # Dropdown pemilih coin
│   │   ├── MarketTable.tsx      # Tabel market data
│   │   ├── MetricsDisplay.tsx   # Model metrics display
│   │   ├── PriceCard.tsx        # Card harga
│   │   └── PriceChart.tsx       # Grafik dengan indicators
│   ├── hooks/               # Custom React hooks
│   │   ├── useTheme.ts          # Dark/light mode
│   │   └── useWatchlist.ts      # Watchlist management
│   ├── services/            # API services
│   │   └── api.ts               # CoinGecko & Model API
│   ├── types/               # TypeScript types
│   │   └── index.ts
│   ├── utils/               # Utility functions
│   │   └── technicalIndicators.ts  # RSI, MA calculations
│   ├── App.tsx              # Main app component
│   ├── main.tsx             # Entry point
│   └── index.css            # Global styles
├── public/                  # Static assets
├── .env                     # Environment variables (optional)
├── package.json
├── tailwind.config.js
├── vite.config.ts
└── README.md
```

## 🎯 Cara Menggunakan

### 1. Dashboard
- Pilih cryptocurrency dari dropdown
- Lihat harga real-time dan prediksi AI
- Analisis grafik dengan indikator teknikal (MA7, MA25)
- Baca AI Insight Box untuk rekomendasi

### 2. Market Data
- Klik bintang (⭐) untuk menambahkan ke watchlist
- Klik coin untuk melihat detail di dashboard
- Sort kolom dengan klik header tabel

### 3. AI Analytics
- Pilih model AI dari dropdown (LSTM, CNN-LSTM, NARX, GRU)
- Lihat performa model dan metrik akurasi
- Bandingkan antar model dengan chart

### 4. Theme Toggle
- Klik icon matahari/bulan di header untuk dark/light mode
- Preferensi tersimpan otomatis

## 🔧 Kustomisasi

### Menambah Cryptocurrency
Edit `AVAILABLE_COINS` di `src/App.tsx`:

```typescript
const AVAILABLE_COINS = [
  { id: 'bitcoin', symbol: 'btc', name: 'Bitcoin' },
  { id: 'ethereum', symbol: 'eth', name: 'Ethereum' },
  // Tambahkan coin baru (gunakan ID dari CoinGecko)
  { id: 'ripple', symbol: 'xrp', name: 'Ripple' },
];
```

### Mengubah Interval Update
Edit interval di `src/App.tsx`:

```typescript
// Default: 60 detik (60000 ms)
const interval = setInterval(loadMarketData, 60000);

// Ubah ke 30 detik:
const interval = setInterval(loadMarketData, 30000);
```

### Custom Styling
Edit `src/index.css` untuk mengubah color scheme atau font:

```css
@layer base {
  body {
    @apply bg-[#0B1426] text-gray-100;
    /* Ubah warna background */
  }
}
```

## 📊 Technical Indicators

### RSI (Relative Strength Index)
- **< 30**: Oversold - Potensi Buy Signal
- **30-70**: Neutral
- **> 70**: Overbought - Potensi Sell Signal

### Moving Averages
- **MA7**: Short-term trend (7 hari)
- **MA25**: Medium-term trend (25 hari)
- **Price > MA7 > MA25**: BULLISH
- **Price < MA7 < MA25**: BEARISH

## 🐛 Troubleshooting

### Port sudah digunakan
```bash
# Ubah port di vite.config.ts atau jalankan:
npm run dev -- --port 3000
```

### API Rate Limit (CoinGecko)
CoinGecko free API memiliki limit ~50 requests/minute. Jika terkena limit, tunggu 1-2 menit.

### Build Error
```bash
# Hapus node_modules dan reinstall
rm -rf node_modules package-lock.json
npm install
npm run build
```

## 📝 Scripts

```bash
npm run dev          # Jalankan development server
npm run build        # Build untuk production
npm run preview      # Preview production build
npm run lint         # Run ESLint
npm run typecheck    # TypeScript type checking
```

## 🚀 Deployment

### Vercel (Recommended)
1. Push code ke GitHub
2. Import project di [Vercel](https://vercel.com)
3. Set environment variables (jika ada)
4. Deploy!

### Netlify
1. `npm run build`
2. Upload folder `dist/` ke [Netlify](https://netlify.com)

### Custom Server
```bash
npm run build
# Upload folder dist/ ke server
# Serve dengan nginx/apache
```

## 📄 License

MIT License - Bebas digunakan untuk project pribadi atau komersial.

## 🤝 Contributing

Contributions welcome! Silakan buat issue atau pull request.

## 📧 Support

Jika ada pertanyaan atau issue, silakan buat GitHub issue atau hubungi developer.

---

**Made with ❤️ using React + TypeScript + AI**
