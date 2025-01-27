# TikTok-like Web MVP (100% Free Stack)

## 1. Core Services

### Frontend Hosting

- Cloudflare Pages (Unlimited requests)
- GitHub Pages (Fallback)

### Backend & APIs

- Cloudflare Workers (100k req/day)
- Vercel Serverless Functions (1000h/mo)
- Supabase (Free tier DB + Auth)

### Media Processing

- FFmpeg.wasm (Browser-side)
- Cloudflare Stream (10 mins free/mo)
- Cloudflare R2 (10GB storage)

### Database

- Supabase PostgreSQL (500MB)
- Neon.tech (Free Postgres tier)
- Cloudflare D1 (SQLite)

## 2. Adjusted Tech Stack

### Frontend

- Next.js (Static Export)
- Preact (Lightweight React)
- PartyKit (WebSocket free tier)
- react-use (Essential hooks)

### Backend

- Cloudflare Workers (JavaScript)
- Hono.js (Lightweight framework)
- Drizzle ORM (TypeScript ORM)
- Zod (Validation)

### Media Pipeline

1. Browser: FFmpeg.wasm (trim/filter)
2. Upload: R2 Direct (Presigned URLs)
3. Transcoding: WASM Workers
4. Streaming: HLS.js (Client-side)

## 2. Technology Stack

### Frontend

- Next.js 14 (App Router)
- React 18 + TypeScript
- Zustand (State)
- react-query (Data Fetching)
- Video.js (Player)
- Uppy (File Uploads)

### Backend
- Node.js 20 (ESM)
- NestJS (Framework)
- PostgreSQL (Main DB)
- Redis (Cache/Sessions)
- BullMQ (Queues)
- Mux.com (Video API)

### 3. Free Service Limits

| Service          | Free Tier Limits              |
|------------------|-------------------------------|
| Cloudflare Pages | Unlimited sites, 500 builds/mo|
| Cloudflare R2    | 10GB storage, 1M operations   |
| Supabase         | 500MB DB, 50k users           |
| Vercel           | 1000 serverless hrs/mo        |
| Neon.tech        | 3 projects, 500MB storage     |
| GitHub Actions   | 2000 mins/mo                  |

## 4. Cost Optimization Strategies

### Client-side Processing:

- FFmpeg.wasm for trimming
- Canvas API for thumbnails
- WebAssembly for filters

### Edge Caching:

- Cache API (Workers)
- Stale-while-revalidate
- Pre-render feed pages

### Storage Optimization:

- WebP images (80% smaller)
- HEVC video (50% smaller)
- Gzip/Brotli compression

## 5. Revised Architecture

sequenceDiagram
    Browser->>Cloudflare: Static Assets
    Browser->>Supabase: Auth
    Browser->>R2: Direct Upload
    Cloudflare Worker->>D1: Store Metadata
    Cloudflare Worker->>R2: Serve Video
    Browser->>HLS.js: Video Playback

## 6. Critical Free Services

### Auth

- Supabase Auth (Email/Magic Link)
- Cloudflare Turnstile (Captcha)

### Database

- D1 (SQLite) for feed data
- KV (Metadata cache)

### Analytics

- Plausible (10k/mo free)
- Cloudflare Web Analytics 

## 7. Feature Adjustments

- Video Duration: Max 60s
- Resolution: 720p max
- Storage: Auto-delete after 30d
- Rate Limits: 5 req/min/user
- No CDN Fallback (R2 direct)

## 8. Development Plan

### Week 1: Core Setup

- Static Next.js site
- Supabase auth integration
- R2 direct upload flow

### Week 2: Video Pipeline

- Browser-side trimming
- WASM thumbnail generator
- HLS.js player

### Week 3: Social Features

- Likes (KV counters)
- Comments (D1)
- Basic profile pages

### Week 4: Optimization

- Edge caching
- Bundle size reduction
- Lazy loading

## 9. Monitoring

- Cron triggers (DB cleanup)
- Sentry Free (Error tracking)
- Healthchecks.io (Uptime)

## 10. Limitations

- No CDN fallback
- No AI features
- No monetization
- No ads
- No push notifications
- Max 1000 daily users
- 100 videos/day upload
- No advanced recommendations
- Basic moderation only
- Limited geographic reach

This architecture can run indefinitely for free if:
- Stay under all free tier limits
- Use client-side processing
- Implement aggressive caching
- Automate cleanup jobs
- Monitor usage daily