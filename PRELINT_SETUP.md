# Prelint Setup — How to Trigger a Review

## One-time Setup (do this first)

1. Go to https://app.prelint.com → sign in with GitHub (`jl1955`)
2. Click **Install GitHub App** → select `megha444/aurora-clarity-extension`
3. Done — Prelint is now watching all PRs on this repo

---

## How to Open a PR to Trigger Prelint

### Option A — Browser (no CLI needed)

1. Go to: https://github.com/megha444/aurora-clarity-extension/compare/main...jing-v1
2. Click **"Create pull request"**
3. Title: `Clarity — full build (jing-v1)`
4. Click **"Create pull request"**
5. Wait ~10 seconds — Prelint posts a review comment automatically

### Option B — Terminal

```bash
cd /Users/jli-cims/ai/aurora-clarity-extension
git checkout -b prelint-test     # create a small test branch
echo "# test" >> specs/product.md
git add specs/product.md
git commit -m "Trigger Prelint review"
git push origin prelint-test
# Then open PR at:
# https://github.com/megha444/aurora-clarity-extension/compare/main...prelint-test
```

---

## What Prelint Checks

Prelint reads these spec files on every PR:

| File | What it enforces |
|---|---|
| `specs/product.md` | 5 pattern types only, scoring rules, API contract, overlay limits |
| `specs/architecture.md` | Folder structure, no build step, ports, .env rules |
| `README.md` | Overall project scope and constraints |

---

## What a Passing Review Looks Like

```
prelint/check — passed ✅
All changes align with specs/product.md and specs/architecture.md
```

## What a Failing Review Looks Like

```
prelint/check — 1 conflict found ⚠️

specs/product.md: "Exactly 5 pattern types"
Your change adds a 6th pattern type `dark_ux` which is
explicitly excluded from scope.
```

---

## Current Branch Status

- Main branch: `main`
- Your build branch: `jing-v1` (already pushed)
- Spec files: `specs/product.md`, `specs/architecture.md`
- Prelint config: `.prelint.yml` (already committed)

**Next action:** open PR from `jing-v1` → `main` at the URL above.

