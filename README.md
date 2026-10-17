# CollabSphere 2.0 (starter slice)
Setup: `npm install && npm run dev` → http://localhost:3000 · Tests: `npm test`
Env: copy `.env.example`; service-role and Gemini keys stay server-side.
Built: Aurora tokens (tailwind.config.ts), Community Orb (SVG, reduced-motion safe), VenueVote UI + API with server-side tally, tie→runoff, organizer-confirm logic, unit tests, Supabase migration with unique-vote + RLS.
Demo notes: votes live in server memory (resets on restart); venues are fictional; no live AI is called.

## API key setup (AI Copilot)
1. Create a key in Google AI Studio.
2. `cp .env.example .env.local` and set `GEMINI_API_KEY=...` (no quotes, no NEXT_PUBLIC_ prefix).
3. Restart `npm run dev`. POST `/api/copilot` with `{"prompt":"..."}`.
4. On Vercel: Project Settings > Environment Variables, add `GEMINI_API_KEY`, redeploy.
Without a key, or if Gemini fails or returns invalid JSON, the route returns a labelled demo fallback.
