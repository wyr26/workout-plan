# workout-plan

Personal single-page workout tracker. One `index.html`, live on GitHub Pages — **pushing to `main` deploys immediately.**

## Rules

- `index.html` on `main` is **StatiCrypt-encrypted**. Never commit the decrypted page or paste its contents anywhere.
- To change the app: get the source (decrypt, or git history pre-`9de4435`), edit, re-encrypt with `npx staticrypt`, verify the decrypt roundtrip, then commit.
- **If blocked by decryption, ask me — never try to figure out how to decrypt the page yourself.**
- Reuse the **same salt** when re-encrypting (it's embedded in the page config) so "Remember me" on devices keeps working.
- Data lives in Supabase (`sessions`, `sets`, `locations`); the anon key in the page is public by design — not a secret.
- Git: commit locally, then **ask before pushing** (also enforced by a global permission rule).
