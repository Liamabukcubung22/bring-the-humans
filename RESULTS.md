# Bring the humans — entry build notes

Competition: bring-the-humans-01 ("Bring the humans", $1,000, entries close
Tue 17 Nov 2026 01:00 WIB / Mon 16 Nov 2026 18:00 UTC).
Account: @sunny-wren-22. Referral code: `jxspwz52`,
link: https://make.fun/r/jxspwz52.
Built in this session only, from scratch. The kit starter's index.html and
ad.png were never opened; only RULES.txt, competition.yaml, kit.json and the
CLI help were read.

## Files

- `index.html` — the ad page (single self-contained file, inline CSS only,
  no external dependencies, no JavaScript).
- `ad.png` — a real screenshot of that page (see below).
- `.makefun/owner.json` — `{"wallet":"27NVLKGQP2Hj6LQ836RRunmwSzYpdT9L5T1c1zxobRfi"}`
- `LICENSE` — MIT, with `SPDX-License-Identifier: MIT` header line.

## Page design

Dark navy page with a yellow/green accent scheme, built to read as a
confident invite rather than a generic landing page:

- Header: `make.fun` wordmark + "$1,000 prize pool · Top 100 paid" badge.
- Hero: "Your AI agent can build. You can win real money." — plain-language
  explanation of make.fun (people + their AI agents build real programs,
  enter paid bounties, get scored and ranked in the open, win USDC on
  Solana), a big yellow CTA button linking to the referral link, and a
  dashed referral box showing the full link
  https://make.fun/r/jxspwz52 and the bare code `jxspwz52`.
- "What you can win": three bounty cards — Bring the humans ($1,000,
  1st place $250), a tiny chess engine ($500, example bounty), best free
  AI model aggregator ($500, example bounty).
- "How it works — 3 steps": 1) Sign up free via the referral link,
  2) Build & enter a bounty, 3) Get scored & win USDC.
- "Why make.fun is different": scored in the open, humans + agents
  together, new bounties all the time, paid in crypto fast.
- Final CTA panel repeating the referral link and code, plus a footer
  with the link and code once more. The code/link appears 7 times in the
  HTML (6× the full link), so it is unmissable in both the page and the
  screenshot.

## How ad.png was produced

Tool: Playwright + headless Chromium (installed in this session with
`npm i playwright` / `npx playwright install chromium`; the first download
attempt failed and the retry succeeded). Script
`../shot/shot.js` (kept outside the entry dir) opened the local
`index.html` in Chromium at viewport 1280×800 and took a full-page
screenshot to `entry/ad.png`. No image editor was used; the PNG is the
rendered page itself.

Verified: `ad.png` is a valid PNG, 1280×2407 px, 724,982 bytes, and was
visually inspected — the rendered page shows the headline, CTA, and the
referral box with `https://make.fun/r/jxspwz52` and code `jxspwz52`
clearly visible near the top, plus the link again in the steps and the
final CTA panel.

## Verification (kit check)

Ran `node <kit>/cli/makefun.mjs check --kit <kit> --repo entry`
(no transcripts — see below):

- competition_open: pass (checked inside the window).
- snapshot: pass (4 files, ~735 KB, within caps).
- license_osi: pass after adding the SPDX identifier line.
- ad_page: pass — index.html carries referral code `jxspwz52` and ad.png
  is a PNG image.
- transcripts_present: FAIL — no transcripts were supplied with this
  check run. This is expected at this stage: transcripts are bundled by
  the parent agent at submission time; this subagent was told not to
  submit. All other transcript-gate checks skipped (nothing to read).
- Repo checks (public, owner, created-after-open, commit in repo,
  duplicate snapshot) are marked "at submission" — they can only be
  decided when the repo is created and the commit submitted, which is
  parent-side work (not done here, per task).

## Honest note on the score

There is nothing to trial-grade locally for this competition: the score
is the number of VERIFIED human signups bound to referral code
`jxspwz52` during the window (14 Nov 18:00 UTC – 16 Nov 18:00 UTC),
decided by make.fun's referral check after the deadline. Fake, bot,
self, same-network, idle or lurker signups never count, and an undecided
signup at the final check never counts. So this entry's score is 0 until
real humans sign up through the link — the page can only help by being
shared. Nothing in this build guarantees any signup.

## Still needed before submission (parent-side)

1. Create a new public GitHub repo (created after 2026-11-14T18:00:00Z),
   commit these files, push.
2. Bundle the agent sessions that built this entry (transcripts) and
   re-run the kit check with `--transcripts`.
3. Submit before the deadline (Tue 17 Nov 2026 01:00 WIB) — do not
   submit from this subagent session.
