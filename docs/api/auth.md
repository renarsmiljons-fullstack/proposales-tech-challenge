# Auth Utilities

## Local Storage Keys
- See `docs/api/endpoints.md#key-locations` for `AUTH_KEY`.

## Helpers
- `addAuthHeader(authData?: AuthData): Record<string, string>` — returns `{ Authorization: Bearer <key> }` or `{}`
- `getAuth(): AuthData | null` — reads from `localStorage`
- `saveAuth(auth: AuthData): void` — writes to `localStorage` and dispatches `auth-localstorage-changed`
- `deleteAuth(): void` — clears from `localStorage` and dispatches `auth-localstorage-changed`
- `logIn(authData: AuthData): void` — persists auth, resets server save status, syncs draft company id
- `logOut(): void` — clears auth, resets server save status, strips draft company id

## React Context
- Provider: `@/components/providers/AuthProvider`
- Hook: `@/hooks/useAuth`

Example:
```tsx
import { AuthProvider } from "@/components/providers/AuthProvider";
import { useAuth } from "@/hooks/useAuth";

export default function App({ children }: { children: React.ReactNode }) {
  return <AuthProvider>{children}</AuthProvider>;
}

function UseIt() {
  const { state, setState } = useAuth();
  // state.auth?.key
  return null;
}
```