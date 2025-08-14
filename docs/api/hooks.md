# Hooks API

## useAuth
- Import: `@/hooks/useAuth`
- Returns: `{ state, setState }` where `state.auth` is `AuthData | null`
- Throws: if used outside `AuthProvider`
- Example:
```tsx
import { AuthProvider } from "@/components/providers/AuthProvider";
import { useAuth } from "@/hooks/useAuth";

function Profile() {
  const { state } = useAuth();
  return <div>{state.auth ? state.auth.company?.name : "Logged out"}</div>;
}
```

## useCreateProposalState
- Import: `@/hooks/useCreateProposalState`
- Returns: `{ state, setState }` where `state.proposal` is `CreateProposalRequest`
- Throws: if used outside `CreateProposalProvider`
- Example:
```tsx
import { CreateProposalProvider } from "@/components/providers/CreateProposalStateProvider";
import { useCreateProposalState } from "@/hooks/useCreateProposalState";

function EditorTitle() {
  const { state, setState } = useCreateProposalState();
  return (
    <input
      value={state.proposal.title_md ?? ""}
      onChange={(e) => setState(s => ({ ...s, proposal: { ...s.proposal, title_md: e.target.value } }))}
    />
  );
}
```

## useServerProposalSaveStatus
- Import: `@/hooks/useServerProposalSaveStatus`
- Returns: `ServerProposalSaveStatus | null`
- Reacts to `server-proposal-save-status-updated` events and localStorage changes
- Example:
```tsx
import { useServerProposalSaveStatus } from "@/hooks/useServerProposalSaveStatus";

function SaveBadge() {
  const status = useServerProposalSaveStatus();
  if (!status) return null;
  return <span>{status.isSaved ? "Saved on server" : "Not saved"}</span>;
}
```

## useIsMobile
- Import: `@/hooks/use-mobile`
- Returns: `boolean` — `true` when viewport < 768px
- Example:
```tsx
import { useIsMobile } from "@/hooks/use-mobile";

function Responsive() {
  const isMobile = useIsMobile();
  return <div>{isMobile ? "Mobile" : "Desktop"}</div>;
}
```