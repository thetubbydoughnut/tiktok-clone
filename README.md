# TikTok-like Web App (Free Tier Edition)

[![License: MIT](https://img.shields.io/badge/License-MIT-blue.svg)](https://opensource.org/licenses/MIT)
[![Deploy with Vercel](https://vercel.com/button)](https://vercel.com/new/clone?repository-url=https%3A%2F%2Fgithub.com%2Fthetubbydoughnut%2Ftiktok-clone)

A lightweight TikTok-style web application built entirely using free-tier services. Perfect for learning modern web development with scalable architecture.

## 🌟 Features

- 📹 Video uploads with client-side processing
- ♾️ Infinite scroll feed
- 🔑 Authentication with magic links
- ❤️ Like & comment functionality
- 📊 Basic analytics
- 🚀 100% free hosting

## 🛠️ Tech Stack

**Frontend**  
[![Next.js](https://img.shields.io/badge/Next.js-14-black?logo=next.js)](https://nextjs.org/)
[![React](https://img.shields.io/badge/React-18-61DAFB?logo=react)](https://react.dev/)
[![TypeScript](https://img.shields.io/badge/TypeScript-5.0-3178C6?logo=typescript)](https://www.typescriptlang.org/)

**Backend**  
[![Supabase](https://img.shields.io/badge/Supabase-Free-3ECF8E?logo=supabase)](https://supabase.com/)
[![Cloudflare](https://img.shields.io/badge/Cloudflare-Workers-F38020?logo=cloudflare)](https://workers.cloudflare.com/)

**Media**  
[![FFmpeg.wasm](https://img.shields.io/badge/FFmpeg.wasm-0.10-green)](https://ffmpegwasm.netlify.app/)
[![Cloudflare R2](https://img.shields.io/badge/R2-10GB_free-FF6714)](https://www.cloudflare.com/products/r2/)

## 🚀 Quick Start

1. **Clone the repository**
   ```bash
   git clone https://github.com/thetubbydoughnut/tiktok-clone.git
   cd tiktok-clone
   ```

2. **Install dependencies**
   ```bash
   npm install
   ```

3. **Set up environment variables**
   ```bash
   cp .env.example .env.local
   ```
   Fill in your credentials from:
   - Supabase (NEXT_PUBLIC_SUPABASE_*)
   - Cloudflare (R2_*)

4. **Run development server**
   ```bash
   npm run dev
   ```

## 🔧 Project Structure
├── components/ # React components
├── lib/ # Utility functions
├── pages/ # Next.js routes
│ ├── api/ # Edge API routes
│ ├── upload.tsx # Video upload page
│ └── index.tsx # Main feed
├── styles/ # CSS modules
├── types/ # TypeScript definitions
└── worker/ # Cloudflare Workers scripts

## 🌍 Deployment

1. **Vercel (Frontend)**
   ```bash
   vercel deploy --prod
   ```

2. **Cloudflare (Media)**
   - Create R2 bucket
   - Add CORS rules
   - Enable public access

3. **Supabase (Database)**
   ```sql
   -- Run initial schema
   psql -h YOUR_SUPABASE_URL -d postgres -U postgres -f schema.sql
   ```

## 🤝 Contributing

1. Fork the repository
2. Create your feature branch:
   ```bash
   git checkout -b feature/amazing-feature
   ```
3. Commit your changes:
   ```bash
   git commit -m 'Add some amazing feature'
   ```
4. Push to the branch:
   ```bash
   git push origin feature/amazing-feature
   ```
5. Open a Pull Request

## 📄 License

Distributed under the MIT License. See `LICENSE` for more information.

## 📸 Screenshots

| Feed Page | Upload Page | Profile Page |
|-----------|-------------|--------------|
| ![Feed Preview](/public/screenshots/feed.png) | ![Upload Preview](/public/screenshots/upload.png) | ![Profile Preview](/public/screenshots/profile.png) |

## 🙏 Acknowledgements

- [FFmpeg.wasm](https://github.com/ffmpegwasm/ffmpeg.wasm) team
- Cloudflare Workers documentation
- Next.js community examples