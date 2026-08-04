# Buzzsprout (buzzsprout)

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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
