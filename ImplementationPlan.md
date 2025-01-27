# Free Tier Implementation Plan

## Phase 1: Core Setup (Week 1)
1. **Frontend Hosting**
   - Use Cloudflare Pages instead of Vercel
   - Implement Preact for smaller bundle size

2. **Authentication**
   - Supabase Auth with magic links
   - Cloudflare Turnstile for CAPTCHA

3. **Database**
   - Supabase PostgreSQL (500MB free)
   - Cloudflare D1 (SQLite) for metadata
   ```bash
   npx wrangler d1 create tiktok-db
   ```

## Phase 2: Video Pipeline (Week 2)
1. **Client-Side Processing**
   ```javascript:components/VideoProcessor.js
   const ffmpeg = await loadFFmpeg();
   await ffmpeg.run('-i', input, '-t', '60', '-vf', 'scale=720:-2', 'output.mp4');
   ```

2. **Storage**
   - Cloudflare R2 direct uploads
   ```javascript:pages/api/get-upload-url.js
   const url = await env.R2.getPresignedUrl(`video_${Date.now()}.mp4`);
   return new Response(JSON.stringify({ url }));
   ```

## Phase 3: Optimization (Week 3)
1. **Edge Caching**
   ```javascript:functions/_middleware.js
   export async function onRequest({ request, next }) {
     const cache = caches.default;
     let response = await cache.match(request);
     if (!response) {
       response = await next();
       response.headers.set('Cache-Control', 'max-age=3600');
       cache.put(request, response.clone());
     }
     return response;
   }
   ```

2. **Cost-Saving Measures**
   - Auto-delete old videos
   ```sql:supabase/functions/cleanup.sql
   DELETE FROM videos 
   WHERE created_at < NOW() - INTERVAL '30 days'
   AND views < 100;
   ```

Full changes made to keep everything free:
1. Removed paid services (Redis, Mux.com, Socket.IO)
2. Simplified backend to use Cloudflare Workers + D1
3. Implemented client-side video processing
4. Added free-tier rate limiting
5. Optimized storage with auto-cleanup
6. Replaced Vercel with Cloudflare Pages 