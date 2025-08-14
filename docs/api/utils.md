# Utilities API

## `cn`
- Import: `@/lib/utils`
- Signature: `cn(...inputs: ClassValue[]): string`
- Purpose: Tailwind CSS class merge helper (clsx + tailwind-merge)

## `validateEmail`
- Import: `@/lib/validateEmail`
- Signature: `validateEmail(email: string): boolean`
- Rules enforced: single `@`, valid characters, no consecutive dots, proper domain
- Example:
```ts
import { validateEmail } from "@/lib/validateEmail";

validateEmail("user@example.com"); // true
```

## `getUploadcareUrl`
- Import: `@/lib/uploadcareUrl`
- Signature: `getUploadcareUrl(uuid: string): string`
- Example: returns `https://ucarecdn.com/<uuid>/`

## Proposal Preview
- Import roots: `@/lib/proposal-preview/*`
- `createPreviewHtml(data?: CreateProposalRequest, company?: Company): string`
- `getProposalPreview(data?: CreateProposalRequest, company?: Company): Promise<string>`
- `escapeHtml(text: string): string`
- `getHeroSection(data?: CreateProposalRequest, company?: Company): string`
- `getBlockSection(data?: CreateProposalRequest): string`
- `getMainFrameHtml(innerHtml: string, data?: CreateProposalRequest): string`

## Proposal Helpers
- `getDefaultBlock(overrides?: Partial<ProposalBlock>): ProposalBlock` from `@/lib/getDefaultBlock`
- Example:
```ts
import { getDefaultBlock } from "@/lib/getDefaultBlock";

const block = getDefaultBlock({ title: "Intro" });
```