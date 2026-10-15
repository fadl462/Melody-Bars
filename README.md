# Melody Bars — Connected AI Music Studio

## What is implemented
- Composer now calls `/api/generate` and displays actual audio when the backend is configured.
- Loading state, errors, audio playback and MP3 download.
- Prompt includes genre, mood, vocal language, tempo, energy, instruments and avoid instructions.
- Cloudflare Worker proxy keeps the provider key server-side.

## Required before live generation
This is an integration-ready build, not a deployed service. You must provide an ElevenLabs API key, deploy the Worker and configure the API URL. No secret is included in this ZIP.

## Deploy the backend
1. Install Node.js and npm, then run `npm install -g wrangler`.
2. Open a terminal in this folder and run `npx wrangler login`.
3. Edit `wrangler.toml`; set `ALLOWED_ORIGIN` to the exact origin of the live site, without a trailing slash.
4. Add the provider key securely: `npx wrangler secret put ELEVENLABS_API_KEY`. Never put this key in browser files.
5. Deploy with `npx wrangler deploy`.
6. Open `https://YOUR-WORKER.workers.dev/health`; expect `status: ok` and `providerConfigured: true`.
7. In `api-config.js`, set `apiUrl` to `https://YOUR-WORKER.workers.dev/api/generate`.
8. Upload the static website to Cloudflare Pages or your host, then test a short instrumental generation.

## Provider implementation
Uses ElevenLabs Music `POST /v1/music`, model `music_v2_5`, MP3 output, `music_length_ms`, optional instrumental mode and a request for C2PA signing. Duration must be 3 seconds–10 minutes. Review your account entitlements, current provider terms, commercial licence and cost before public launch.
Official docs: https://elevenlabs.io/docs/api-reference/music/compose and https://developers.cloudflare.com/workers/configuration/secrets/

## Current limitations
Generated tracks stay in browser memory for this session. Persistent accounts/library, database, R2 storage, billing, authentication, per-user rate limits, job queue, section regeneration, stem export, and collaboration are not implemented yet. CORS is not authentication; add user authentication, rate limiting and spending caps before public use. Beat/loop mode prompts for a loop-like result but does not guarantee seamless looping.
