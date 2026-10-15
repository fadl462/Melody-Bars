# Melody Bars — AI Music Studio Prototype

A responsive, premium dark-theme front-end concept for an AI music creation platform.

## Included
- Responsive workspace layout with navigation and creator workspace
- Song / instrumental / beat-loop mode selection
- Prompt composer, character counter, prompt suggestions and Surprise Me
- Genre, mood, language and duration controls
- Advanced creative direction fields for tempo, energy, instruments and exclusions
- Prompt guide modal
- Inspiration cards and session-only demo project list
- Toast feedback, mobile navigation, keyboard shortcuts and accessibility basics

## Important: prototype vs. production
This is a **front-end prototype**. The Create button creates a local demo project entry; it does not generate actual audio. Real generation requires a backend and a licensed music-generation model/API. Do not expose provider API keys in browser JavaScript.

## Suggested production architecture
1. Front end: React / Next.js or similar, with this design system adapted into reusable components.
2. Backend API: authenticated endpoints for generation jobs, project metadata, edits, exports and billing.
3. Music generation: select a provider that explicitly permits your intended commercial use, or negotiate a model/API licence. Keep the provider behind a server-side adapter so it can be changed without rebuilding the app.
4. Storage: object storage for audio, stems, cover art and user uploads; relational database for users, projects, rights records and generation history.
5. Queue: asynchronous job queue for generation, retries, status updates, rate limits and usage accounting.
6. Identity and billing: secure sign-in, account recovery, plan entitlements, payment integration and abuse controls.
7. Rights and safety: prompt/input rights confirmation, upload scanning, artist-imitation restrictions where required, reporting/takedown workflow, clear commercial-use terms and generation audit trail.
8. Release workflow: audio preview, version history, WAV/MP3 export, stems where supported, metadata and distribution-partner integration only after licensing is cleared.

## Suggested differentiators to build in phases
- Section regeneration: change a verse, hook or bridge without recreating the whole track.
- Version compare: A/B audition and restore earlier versions.
- Lyrics and pronunciation editor with multilingual support (Twi, Ga, Ewe, Hausa, English and Pidgin as target-market priorities; quality must be validated).
- Voice identity controls only with consent and documented rights.
- Stem export, MIDI or DAW handoff where model capabilities/licences allow.
- Transparent rights dashboard per track: plan, creation date, permitted use and restrictions.
- Collaboration, feedback comments, project folders and release checklist.
- Creator marketplace only after rights, payouts, moderation and fraud controls are ready.

## Run locally
Open `index.html` in a modern browser. For best results use a local static server, e.g. `python -m http.server 8000` from this folder.

No build step is required. Google Fonts are loaded remotely; system fallbacks are provided.
