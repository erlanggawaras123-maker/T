# Stremio Hentai Hub

Stremio addon based on the stable v2.5.4-wide build, updated to v2.5.5 with two additional catalogs: Iwara Community and Hanime.red Studio HD. The existing providers and global genre labels are retained.

## Providers

- HentaiMama
- Hentaigasm
- HentaiSmile
- HentaiCity
- Iwara Community (API-first, short-timeout HTML catalog fallback)
- Hanime.red Studio HD (server-rendered catalog, limited-depth direct-stream extraction)

Hanime.red currently labels its library as 720p/1080p and identifies studio names on episode pages. The addon only displays stream quality when the source or playlist explicitly reports it.

## Deploy

1. Put `index.js`, `package.json`, `test.js`, `README.md`, and `render.yaml` directly in the repository root.
2. Install dependencies with `npm install`.
3. Start with `npm start`.
4. Install the public HTTPS URL ending in `/manifest.json` in Stremio.

## Tests

Run `npm test`. The provider additions use the existing Axios/Cheerio stack only; no Chromium, Puppeteer, or headless-browser process is added. Iwara API errors and stream-resolution errors are caught and returned as empty results, so an upstream outage does not terminate the addon process.

## Optional environment variables

`PORT`, `USER_AGENT`, `HTTP_TIMEOUT_MS`, `CACHE_CATALOG_SECONDS`, `CACHE_DETAIL_SECONDS`, `CACHE_STREAM_SECONDS`, `EMBED_DEPTH`, `EMBED_PAGE_LIMIT`, `HENTAIMAMA_BASE`, `HENTAIGASM_BASE`, `HENTAISMILE_BASE`, `HENTAICITY_BASE`, `HANIMERED_BASE`, `IWARA_WEB_BASE`, `IWARA_API_BASE`, `IWARA_FILES_BASE`, `IWARA_IMAGES_BASE`, and `IWARA_RATING`.
