# API Clients

High-level fetchers used by the app. These call Next.js API routes under `/api/*` and handle auth headers.

## Content
- Module: `@/app/api/client/contentApi`
- `listContent(params?: ContentListParams, authData?: AuthData): Promise<ContentListResponse>`
- `createContent(payload: CreateContentRequest, authData?: AuthData): Promise<CreateContentResponse>`
- Example:
```ts
import { listContent } from "@/app/api/client/contentApi";
const result = await listContent({ include_archived: false });
```

## Proposals
- Module: `@/app/api/client/proposalApi`
- `createProposal(payload: CreateProposalRequest): Promise<CreateProposalResponse>`
- Example:
```ts
import { createProposal } from "@/app/api/client/proposalApi";
await createProposal({ language: "en", title_md: "Hello" });
```

## Uploadcare
- Module: `@/app/api/client/uploadFileApi`
- `uploadFile(formData: FormData): Promise<UploadcareDirectUploadResponse>`
- `getFileInfo(fileId: string): Promise<UploadcareFileInfo>`

## OpenAI
- Module: `@/app/api/client/openAiApi`
- `getResponse(payload: OpenAIRequest): Promise<OpenAIResponse>`
- Example:
```ts
import { getResponse } from "@/app/api/client/openAiApi";
const res = await getResponse({ model: "gpt-4.1", input: "Hello" });
```