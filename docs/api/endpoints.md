# Low-level Endpoints

These are constructors for HTTP calls used by Next.js route handlers or clients.

## Base URLs
- Module: `@/app/api/client/config/baseUrl`
- `API_ENVIRONMENT`: `dev|prod|test`
- `API_BASE_URL`: base for Proposales API
- `FILE_UPLOAD_BASE_URL`: base for Uploadcare REST

## Key Locations
- Module: `@/app/api/client/config/keyLocations`
- `AUTH_KEY`, `DRAFT_KEY`, `SERVER_PROPOSAL_SAVE_STATUS_KEY`
- `OPENAI_API_KEY`, `UPLOADCARE_PUB_API_KEY`

## `endpoints`
- Module: `@/app/api/client/config/endpoints`
- Export: `endpoints` object with builder functions. All functions return `{ method, url, expectedStatus, body?, responseData }`.

### Content
- `content.list(params?: ContentListParams)` → GET `v3/content`
- `content.create(payload: CreateContentRequest)` → POST `v3/content`

### Companies
- `companies.list()` → GET `v3/companies`

### Proposals
- `proposals.create(payload: CreateProposalRequest)` → POST `v3/proposals`

### Uploadcare
- `uploadcare.directUpload(payload: UploadcareDirectUploadPayload)` → POST `${FILE_UPLOAD_BASE_URL}/base/` with FormData
- `uploadcare.info({ file_id, pub_key })` → GET `${FILE_UPLOAD_BASE_URL}info/?...`