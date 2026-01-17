# Glimt ⚡️

Et minimalistisk alternativ til Glympse. Fokus på fart, enkelhet og personvern.

## Konsept
Del din posisjon i sanntid via en unik URL som utløper automatisk.

## Tech Stack
- **iOS:** Swift (Native)
- **Backend:** Cloudflare Workers (Edge runtime)
- **Database/Storage:** Cloudflare KV eller Durable Objects (for sanntidskoordinater)
- **Web:** Cloudflare Pages (for mottakerens kartvisning)

## MVP Funksjonalitet (Spec)
1. **iOS App:**
   - Én stor knapp: "Start Glimt".
   - Velg varighet (15m, 30m, 1t).
   - Generer unik lenke og åpne "Share Sheet".
   - Sender GPS-koordinater i bakgrunnen til backend mens aktiv.

2. **Backend (Cloudflare):**
   - API-endepunkt for å motta koordinater (`POST /update`).
   - API-endepunkt for å hente koordinater (`GET /view/:id`).
   - Automatisk sletting av data etter utløpt tid.

3. **Web Visning:**
   - Enkel Leaflet/MapLibre-basert kartvisning.
   - Viser markør for gjeldende posisjon.
   - Viser "Sist sett" og "Utløper om X min".

## Prinsipp
- Ingen brukerkontoer.
- Ingen lagring av historikk etter at økten er ferdig.
- Maksimal brukervennlighet: "Open, Tap, Share".
