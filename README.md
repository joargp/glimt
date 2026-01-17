# Glimt ⚡️

Et minimalistisk alternativ til Glympse. Fokus på fart, enkelhet og personvern.

## Konsept
Del din posisjon i sanntid via en unik URL som utløper automatisk. Vi beholder det norske navnet **Glimt**, og bruker begrepet **"glints"** for de individuelle delingene på engelsk.

## Tech Stack
- **iOS:** Swift (Native SwiftUI)
- **Backend:** Cloudflare Workers med **SQLite-backed Durable Objects**
- **Sanntid:** **WebSockets** med Hibernation API for batterivennlig og kostnadseffektiv oppdatering
- **Web:** Cloudflare Pages (for mottakerens kartvisning)

## MVP Funksjonalitet (Spec)
1. **iOS App:**
   - Én stor knapp: "Start Glimt".
   - Velg varighet (15m, 30m, 1t).
   - Generer unik lenke og åpne "Share Sheet".
   - Sender GPS-koordinater i bakgrunnen via WebSocket til backend mens aktiv.

2. **Backend (Cloudflare):**
   - Durable Object per økt for å håndtere WebSocket-tilkoblinger og tilstand.
   - API-endepunkt for å hente gjeldende tilstand for web-klienter.
   - Automatisk opprydding av Durable Object og data etter utløpt tid via `setAlarm()`.

3. **Web Visning:**
   - Enkel Leaflet/MapLibre-basert kartvisning som kobler seg på samme WebSocket.
   - Viser markør for gjeldende posisjon i sanntid.
   - Viser "Sist sett" og "Utløper om X min".

## Prinsipp
- Ingen brukerkontoer.
- Ingen lagring av historikk etter at økten er ferdig.
- Maksimal brukervennlighet: "Open, Tap, Share".
