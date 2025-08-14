# Shared Types

Key TypeScript types exported from `src/types`.

## Auth
- Module: `@/types/auth`
- `AuthData` — `{ key: string; company?: Company }`

## Company
- Module: `@/types/company`
- `Company` — id, name, currency, registration_number, website_url, tax_mode

## Content
- Module: `@/types/content`
- `ContentImage`, `Asset`, `ContentListParams`, `ContentListItem`, `ContentListResponse`, `CreateContentRequest`, `CreateContentResponse`, `UpdateContentRequest`, `DeleteContentRequest`, `DeleteContentResponse`

## Proposals
- Module: `@/types/proposal`
- `CreateProposalRequest`, `CreateProposalResponse`, `PatchProposalDataRequest`, `PatchProposalDataResponse`, `Proposal`, `ProposalBlock`, `ProposalAttachment`, `ProposalMedia`, `ProposalSearchResult`, `ProposalSearchResponse`, `Unit`, `UnitValues`, `MultiProductRow`, `MultiProductSubRow`, `UnitSchema`, `ProposalTracking`, `ProposalTaxOptions`, `ProposalEditor`, `ProposalSignature`, `ProposalRecipient`, `ProposalInvoicing`

## AI
- Module: `@/types/ai`
- `simplifiedProposalSectionTextOnly`, `simplifiedProposalTextOnly` (Zod schemas)
- `SimplifiedProposalSectionTextOnly`, `SimplifiedProposalTextOnly` (inferred types)
- `ResponseType` — union of supported structured output identifiers

## OpenAI
- Module: `@/types/openai`
- `OpenAIRequest` — fields: `model`, `instructions?`, `input`, `responseType?`
- `OpenAIResponse` — `{ output_text: string; output_parsed?: unknown }`
- `OpenAIChatMessage`, `OpenAIChatRole`

## API Response Wrapper
- Module: `@/types/api`
- `ApiResponse<T>` — common wrapper with `success`, `data`, `error`, `message`

## Server Proposal Save Status
- Module: `@/types/server-proposal-save-status`
- `ServerProposalSaveStatus` — `{ isSaved: boolean; proposal?: savedProposalResponse }`