# Stremio Hentai Hub v2.5.7

Stremio addon with five active sources: HentaiMama, Hentaigasm, HentaiSmile, Oppai Stream, and Iwara Community. HentaiCity and HStream are removed.

## Changes in v2.5.7

- Removed HStream while it is unavailable and replaced it with Oppai Stream. Its published extractor compatibility documents free 720p/1080p/4K variants, but each video only displays resolutions actually exposed by its player/source.
- Kept Iwara Community and corrected the API host to `apiq.iwara.tv` after Iwara’s 2026 migration, with fallback to `api.iwara.tv`; hardened API payload parsing for list responses nested under `data`, `results`, `videos`, or `items`.
- Corrected Iwara thumbnails to the `/image/original/{fileId}/thumbnail-XX.jpg` path used by existing Iwara API clients.
- Added Iwara catalog request fallbacks for recent/trending ecchi entries and a filtered all-rating fallback; general-rated entries remain excluded.
- The addon reads URLs from real API/player output only. It does not fabricate stream links or open a browser from Stremio.
- Existing HentaiMama, Hentaigasm, HentaiSmile, shared genres, and poster behavior are retained.

## Deploy

1. Put the contents of this ZIP at the repository root (including `index.js` and `package.json`).
2. Install dependencies with `npm install`.
3. Start with `npm start`.
4. Install the public HTTPS URL ending in `/manifest.json` in Stremio.

## Validation

Run `npm test` after dependencies are installed. The included tests cover manifest registration, Oppai card and quality parsing, Iwara nested API shapes, rating filtering, thumbnail paths, and existing player/catalog helpers. Live upstream requests were not available from the build environment, so verify the live Oppai and Iwara feeds in the deployment logs.

## Environment variables

`PORT`, `USER_AGENT`, `HTTP_TIMEOUT_MS`, `CACHE_CATALOG_SECONDS`, `CACHE_DETAIL_SECONDS`, `CACHE_STREAM_SECONDS`, `EMBED_DEPTH`, `EMBED_PAGE_LIMIT`, `HENTAIMAMA_BASE`, `HENTAIGASM_BASE`, `HENTAISMILE_BASE`, `OPPAI_BASE`, `IWARA_API_BASE`, `IWARA_LEGACY_API_BASE`, and optional `CHROME_PATH`.
