# Proposal Utilities

Utilities under `@/app/api/client/utils/proposal` and related helpers.

## Local Draft Helpers
- `getDraftProposalLocal(): CreateProposalRequest | null`
- `saveDraftProposalLocal(draft: CreateProposalRequest | null): void`
- `getServerProposalSaveStatus(): ServerProposalSaveStatus | null`
- `updateServerProposalSaveStatus(status: ServerProposalSaveStatus): void`

Example:
```ts
import { getDraftProposalLocal, saveDraftProposalLocal } from "@/app/api/client/utils/proposal/getDraftProposalLocal";
// or: from their respective files

const draft = getDraftProposalLocal();
saveDraftProposalLocal({ ...draft, title_md: "New" } as any);
```

## Transformations
- `createProposalRequestToSimplified(req: CreateProposalRequest): SimplifiedProposalTextOnly`
- `simplifiedProposalTextOnlyToCreateProposalRequest(simplified, base?): CreateProposalRequest`
- `transformProposalRequestToSimplifiedTextString(req): string` — user/AI-readable markdown-ish text

## Merge
- `mergeTwoProposalRequests(original: CreateProposalRequest, override: Partial<CreateProposalRequest>): CreateProposalRequest`

## AI Edit Flow
- `editProposalWithAI(proposal: CreateProposalRequest, instructions: string): Promise<CreateProposalRequest>`
- Internals: `getProposalResponse(input: string)` uses `@/app/api/client/openAiApi` with `responseType`=`simplifiedProposalTextOnly`.

Example:
```ts
import { editProposalWithAI } from "@/app/api/client/utils/proposal/editProposalWithAI";

const updated = await editProposalWithAI(currentProposal, "Improve clarity and add a section about pricing.");
```

## Server Save Helper
- `saveServerProposal(draft?: CreateProposalRequest): Promise<void>` — persists locally, enriches blocks with content ids, creates proposal on server, and updates `ServerProposalSaveStatus` accordingly.

Example:
```ts
import { saveServerProposal } from "@/app/api/client/utils/proposal/saveProposalServer";
await saveServerProposal(currentDraft);
```

## Content Enrichment
- `enrichProposalBlocksWithContentIds(draft: CreateProposalRequest): Promise<CreateProposalRequest>`
- `proposalBlockToContentIds(block: ProposalBlock, companyId: number): Promise<CreateContentResponse>`
- `transformProposalBlockToContentRequest(block, companyId): Promise<CreateContentRequest>`
- `uploadcareCareUuidsToContentImage(uuids: string[]): Promise<ContentImage[]>`