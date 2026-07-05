# Buzzsprout (buzzsprout)

Buzzsprout is a podcast hosting platform that handles hosting, distribution, promotion, and analytics for podcasters - uploading and optimizing audio, publishing an RSS feed, listing shows in directories like Apple Podcasts and Spotify, and reporting on plays. Buzzsprout also exposes a documented public REST API (base `https://www.buzzsprout.com/api`) so third parties can programmatically read and manage the podcasts and episodes on an account.

**APIs.json:** [https://raw.githubusercontent.com/api-evangelist/buzzsprout/refs/heads/main/apis.yml](https://raw.githubusercontent.com/api-evangelist/buzzsprout/refs/heads/main/apis.yml)

## Access Model

The Buzzsprout API is a **documented public REST API** intended for third parties integrating with the platform. Its official reference lives in the public GitHub repository [buzzsprout/buzzsprout-api](https://github.com/buzzsprout/buzzsprout-api). Key characteristics:

- **RESTful and JSON-serialized**, over **SSL only**. Base URL: `https://www.buzzsprout.com/api`.
- **Token authentication.** Send the token as the header `Authorization: Token token=YOUR_TOKEN` (the token is prefixed by the literal `token=` with no whitespace), or as an `api_token` query parameter. Tokens come from the Buzzsprout admin account section.
- **Account-scoped, not open access.** You operate only on the podcasts and episodes belonging to your own account; the podcast id in the episode paths comes from your account.
- **Client requirements.** A custom `User-Agent` is required (some default agents are blocked). POST/PUT requests must use `Content-Type: application/json; charset=utf-8` or the API returns `415`. Responses carry `ETag` / `Last-Modified` for conditional (`304`) requests, and clients should retry on `5xx` errors.
- **No WebSocket.** Buzzsprout's own API is request/response REST; distribution happens through the RSS feed and downstream directories. See [review.yml](review.yml).

## Tags

- Podcasting
- Podcast Hosting
- Audio
- Media
- Episodes
- RSS

## Timestamps

- **Created:** 2026-07-05
- **Modified:** 2026-07-05

## APIs

### Buzzsprout Episodes API

List, retrieve, create, and update the episodes on a Buzzsprout podcast. Episodes are scoped to a podcast id at `/api/{podcast_id}/episodes.json`, and audio can be attached by URL (`audio_url`) or file upload (`audio_file`) with optional email notification after processing.

- **Human URL:** [https://github.com/buzzsprout/buzzsprout-api/blob/master/sections/episodes.md](https://github.com/buzzsprout/buzzsprout-api/blob/master/sections/episodes.md)
- **Base URL:** `https://www.buzzsprout.com/api`

#### Tags

- Episodes
- Audio
- Publishing

#### Properties

- [Documentation](https://github.com/buzzsprout/buzzsprout-api)
- [API Reference](https://github.com/buzzsprout/buzzsprout-api/blob/master/sections/episodes.md)
- [OpenAPI](openapi/buzzsprout-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/buzzsprout.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buzzsprout.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

### Buzzsprout Podcasts API

List the podcasts on a Buzzsprout account at `/api/podcasts.json`, returning each show's title, author, description, contact email, categories, language, timezone, artwork, and website. Used to discover the podcast ids that scope the Episodes API.

- **Human URL:** [https://github.com/buzzsprout/buzzsprout-api/blob/master/sections/podcasts.md](https://github.com/buzzsprout/buzzsprout-api/blob/master/sections/podcasts.md)
- **Base URL:** `https://www.buzzsprout.com/api`

#### Tags

- Podcasts
- Directories
- Metadata

#### Properties

- [Documentation](https://github.com/buzzsprout/buzzsprout-api)
- [API Reference](https://github.com/buzzsprout/buzzsprout-api/blob/master/sections/podcasts.md)
- [OpenAPI](openapi/buzzsprout-openapi.yml) — [OpenAPI Specification](https://spec.openapis.org/oas/latest.html)
- [Postman Collection](collections/buzzsprout.postman_collection.json) — [Postman Collection 2.1](https://schema.getpostman.com/json/collection/v2.1.0/collection.json)
- [Open Collection](collections/buzzsprout.opencollection.json) — [Open Collection 1.0](https://schema.opencollection.com/opencollection/v1.0.0.json)

## Common Properties

- [GitHub Organization](https://github.com/buzzsprout)
- [LinkedIn](https://www.linkedin.com/company/buzzsprout)
- [Website](https://www.buzzsprout.com)
- [Documentation](https://github.com/buzzsprout/buzzsprout-api)
- [Plans](plans/buzzsprout-plans-pricing.yml)
- [Rate Limits](rate-limits/buzzsprout-rate-limits.yml)
- [Fin Ops](finops/buzzsprout-finops.yml)

## Maintainers

**FN:** Kin Lane
**Email:** kin@apievangelist.com
