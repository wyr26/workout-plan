# workout-plan

Personal single-page workout tracker. One `index.html`, live on GitHub Pages — **pushing to `main` deploys immediately.**

## Rules

- `index.html` on `main` is **StatiCrypt-encrypted**. Never commit the decrypted page or paste its contents anywhere.
- To change the app: get the source (decrypt, or git history pre-`9de4435`), edit, re-encrypt with `npx staticrypt`, verify the decrypt roundtrip, then commit.
- **If blocked by decryption, ask me — never try to figure out how to decrypt the page yourself.**
- Reuse the **same salt** when re-encrypting (it's embedded in the page config) so "Remember me" on devices keeps working.
- Data lives in Supabase (`sessions`, `sets`, `locations`); the anon key in the page is public by design — not a secret.
- **Production Supabase is read-only by default** (`GET`s only) — never write test rows, even ones you plan to clean up. **Exception: when I explicitly ask for a specific data change** (e.g. "rename this entry"), write exactly that and nothing more: save the affected rows to a backup outside the repo first, `PATCH`/`DELETE` by row `id`, then re-read to verify.
- **Always test against a local mock copy**: serve the decrypted page locally with `SB_URL` pointed at a local mock server backed by an in-memory snapshot of prod data (taken with read-only `GET`s), so the user can test edits/deletes safely. Keep the mock and decrypted copies outside the repo, and delete them when done.
- Git: commit locally, then **ask before pushing** (also enforced by a global permission rule).
