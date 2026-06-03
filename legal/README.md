# SpeakUp Kids — legal documents

`privacy.md` and `terms.md` are the formal versions of the in-app summaries. They are written to be **hostable as public URLs** — Google Play Console requires a privacy-policy URL on every listing for apps that target children, and Apple App Store does the same. Without these URLs the app cannot launch.

## What you need to do (one-time setup, ~10 minutes)

The fastest free path is GitHub Pages. If you already have any GitHub account:

1. Create a new public repo named `speakup-kids-legal` (or any name — the URL just needs to be stable).
2. Copy `privacy.md` and `terms.md` into the repo root.
3. Repo → **Settings** → **Pages** → Source: **Deploy from a branch** → `main` / `/(root)` → Save.
4. Wait ~60 seconds. GitHub Pages publishes to `https://<your-github-username>.github.io/speakup-kids-legal/privacy` and `/terms`.
5. Paste those two URLs into the SpeakUp Kids project's docs / Play Console listing.

If you'd rather use a custom domain later (e.g. `speakupkids.app/privacy`), you can — but this is OPTIONAL and adds a ~$15/year domain cost. For v1.0 launch, GitHub Pages is enough. If/when you do want a custom domain:

- Host on Cloudflare Pages, Netlify, or Vercel — all free for static sites
- Add a CNAME or DNS A record pointing the subdomain at the host
- Point Play Console at `https://speakupkids.app/privacy`

## Keeping these in sync with the app

Two places need to match this content:

- `lib/features/parent/presentation/privacy_screen.dart` — the in-app summary shown to mentors
- The hosted URLs (Play Console + App Store listing)

When this document changes, update the "Last updated" date at the top of BOTH `privacy.md` AND the in-app screen. For material changes (collecting a new data type, adding a third-party service, changing the ads policy) also notify signed-in mentors by email.

## What to NOT do

- Don't host these inside an authenticated dashboard. The URL must work for anyone, including Play Console reviewers.
- Don't redirect the URL to a different host without leaving the original live for 30 days — reviewers re-check existing apps on policy updates.
- Don't strip out the Malaysia-specific PDPA mention or the SST line. Those are country-of-record requirements.
