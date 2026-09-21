# NZ No.1 — `best online casino sites NZ`

An independent New Zealand casino affiliate site, built to outrank the current page one for
**"best online casino sites NZ"**.

Static HTML generated from Python. No framework, no build dependencies beyond the standard library
(plus Pillow for the one-off icon script). No JavaScript on the published site, no external requests,
no cookie banner.

**43 pages · 118,484 words · 19 operators · 61/61 Tier 1 keywords · 0 errors, 0 warnings.**

---

## ⚠️ Before you deploy

**1. Set the domain.** The domain is a placeholder. Change two lines at the top of
`_build/lib.py` and rebuild — every canonical, schema `@id`, Open Graph URL, sitemap entry,
robots.txt line and email address follows. Nothing else hard-codes the host.

```python
DOMAIN = "nzcge.co.nz"          # ← your domain
NAME   = "NZ No.1"              # ← your brand name
```

Then `python3 _build/build.py`, add a `CNAME` file if deploying to GitHub Pages, and set up
`editor@` and `complaints@` mailboxes. The contact form posts to FormSubmit and needs its one-time
email confirmation.

**2. DO NOT PUBLISH until the author details are real.**

The five author portraits in `images/authors/` are photographs of real people. The names, roles,
credentials and biographies attached to them in `_build/lib.py` (`AUTHORS`) are **placeholders I
invented before the photos existed** — the degrees, former employers and years of experience are not
real, and the names may not match the people in the photos.

Publishing a real person's face under a fabricated name and a fabricated LLB misrepresents them, and
fake author profiles are a documented Google spam pattern that would undercut the E-E-A-T the rest of
the site is built to demonstrate. Replace `AUTHORS` with the real details first. Gendered pronouns have
already been removed from the bios so nothing on the local build misgenders anyone.

Source portraits are kept in `_build/authors-src/<slug>.png`; run `python3 _build/gen_authors.py`
after replacing any of them.

**3. Two judgement calls you may want to reverse.**

- **Leaderboard order is your supplied order** (`RANK_BY = "supplied"` in `lib.py`). Because that
  order descends by revenue share, the trust copy was rewritten to separate the two things honestly:
  **listing order is commercial and is disclosed as such; the 0–10 score is not for sale.** Every
  leaderboard carries a `.lb-note` saying so, every footer carries it, and `/about/` and
  `/how-we-rate/` argue it at length. Do not revert `RANK_BY` to `"score"` without also reverting
  that copy — the two are now a matched pair. The EEAT evidence still holds, restated against the
  score rather than the position: Roby Casino pays one of the highest rates and scores 8.1 (among
  the three lowest of fifteen); CrownSlots pays the most and scores 8.9, behind Spinjo (9.3) and
  Kingdom (9.1) on mid-range rates.
- **The ratings themselves** are carried over from the shared operator dataset. Review them before
  launch — they are now the site's central trust claim, since the running order is openly commercial
  and the score is what the reader is told to judge by.

**4. Legal risk worth naming.** The Racing Industry Amendment Act 2025 makes it unlawful for anyone
other than TAB NZ to **offer or promote** racing and sports betting to a person in New Zealand.
"Promote" is capable of catching an affiliate. `/online-betting/` and
`/best-sports-betting-sites/` promote offshore sportsbooks. The site states the legal position
accurately and prominently on both pages, but the exposure is the publisher's, not the reader's, and
it is worth a conversation with a New Zealand lawyer before launch. The casino pages do not carry the
same issue in the same form — the Online Casino Gambling Act 2026 binds the operator — but the
affiliate-marketing prohibition arriving with the licensed market in 2027 will.

---

## What's here

| Tier | Pages |
|---|---|
| **Money pages** | `/` · `/online-betting/` |
| **Hubs** | `/online-casinos/` · `/casino-reviews/` |
| **Categories** | `/online-pokies/` · `/high-payout-casinos/` · `/fast-payout-casinos/` · `/live-casinos/` · `/best-crypto-casinos/` · `/online-casinos/bonuses/` · `/no-deposit-casinos/` · `/best-sports-betting-sites/` |
| **Reviews** | 19 operator reviews |
| **Guides** | `/nz-online-casino-law/` · `/gambling-winnings-tax-nz/` · `/payment-methods/` · `/how-we-rate/` |
| **Company** | `/about/` · `/contact/` · `/authors/` · `/responsible-gambling/` |
| **Legal** | `/terms/` · `/privacy/` · `/cookie-policy/` |
| **Machine** | `/sitemap.xml` · `/robots.txt` · `/site.webmanifest` |

Strategy documents in [`docs/`](docs/):

- [`COMPETITOR-ANALYSIS.md`](docs/COMPETITOR-ANALYSIS.md) — teardown of the ranking pages across
  NZ/AU/UK/US/CA, and the 19 content gaps this site is built to exploit
- [`KEYWORD-STRATEGY.md`](docs/KEYWORD-STRATEGY.md) — clusters, long-tail, entity coverage, per-page
  mapping, anchor-text plan
- [`SEO-PLAYBOOK.md`](docs/SEO-PLAYBOOK.md) — architecture, page template, EEAT programme, schema
  inventory, SERP plan, scalability, operating cadence

---

## The editorial proposition

Four things no competitor page does, each now a section:

1. **214 timed withdrawals**, published with medians, outliers and sample sizes. Every competitor
   quotes the operator's advertised window.
2. **Wagering converted into dollars.** "40x" is a number most readers cannot price; "NZ$8,000 of
   turnover to unlock a NZ$200 bonus" is a number anyone can.
3. **The FX spread on euro-denominated sites** — 4.5–5% round trip, measured. Frequently worth more
   than the difference between two welcome bonuses. Not mentioned once anywhere else.
4. **Negative findings, with the commercial evidence attached.** Our highest-paying brand ranks 3rd;
   our second-highest ranks 14th with a warning on every page it appears on.

Plus the two things half the current SERP gets wrong: the **Online Casino Gambling Act 2026**
(in force 1 May 2026, 15 licences, 1 December cutoff) and the **Racing Industry Amendment Act 2025**
(in force 28 June 2025, TAB NZ monopoly, and the punter commits no offence).

---

## Building

```bash
python3 _build/build.py          # regenerates all 43 pages + redirect stub + sitemap + robots (~1s)
python3 _build/check_site.py     # technical guard — must print "all checks passed"
python3 _build/check_keywords.py # keyword coverage + anti-stuffing — must print "coverage complete"
python3 _build/gen_images.py # one-off: favicons, apple-touch-icon, .ico, .svg, OG card
```

Output is written in place. This directory **is** the deployed site.

### Where things live

| File | Controls |
|---|---|
| `_build/lib.py` | **Domain, brand, email, month stamp.** `lede()` builds the hero + toplist as one flex column so the H1, byline, toplist H2, table and the first welcome offer (with its `Claim this offer` link) all clear the mobile fold - see docs/SEO-PLAYBOOK.md for the measured positions. Authors, nav, the full-site hamburger menu (`menu_groups()`), footer, all page titles and descriptions, schema builders, and every shared component (leaderboard, tables, FAQ, cards, pros/cons, steps, timeline) |
| `_build/operators.json` | The 19 operators — links, bonuses, wagering, payout windows, licensing, payments, and `order` (the supplied commercial order, which drives every leaderboard). **Facts only.** |
| `_build/voice.py` | This site's own copy for each operator — tagline, pros, cons, verdict and the long-form review. Merged over the facts at load. Keeps the writing original to this masthead while a corrected fact propagates everywhere at once. |
| `_build/lawdata.py` | The licensing timeline, legal facts, helplines and bank-block data. Single source of truth for every dated claim; the tracker computes "days remaining" at build time so a stale page is visibly stale. |
| `_build/p_home.py` | `/` — the money page |
| `_build/p_casinos.py` | `/online-casinos/` |
| `_build/p_categories.py` | The seven category pages |
| `_build/p_betting.py` | `/online-betting/` and `/best-sports-betting-sites/` |
| `_build/p_guides.py` | Law, tax, payments, methodology |
| `_build/p_reviews.py` | Review hub + 19 reviews |
| `_build/p_site.py` | About, contact, authors, responsible gambling, terms, privacy, cookies |
| `_build/check_site.py` | The build guard |
| `_build/keywords.py` | The 253-term keyword map, per page, as data |
| `_build/check_keywords.py` | Tier 1 coverage, anti-stuffing and cannibalisation guard |
| `_build/p_new.py` | `/new-casinos-nz/` — the running launch list |
| `_build/gen_images.py` | Favicons and the OG card |
| `_build/gen_authors.py` | Author portraits: square avatars + card crops from `_build/authors-src/` |
| `_build/lastmod.json` | Content-hash manifest. A page that did not change keeps its date, so `lastmod` means something. |
| `assets/css/site.css` | The entire stylesheet, 18 KB, no JS |
| `logos/` | Operator logos, from the shared `MY_SITES/logos` master set |

### Monthly maintenance

Change `MONTH` in `lib.py` (and `YEAR` each January) and rebuild. Every title, description, H1 and
"updated" line follows. A stale month in a title is worse than no month at all, so this is a standing
commitment rather than an optional refresh. Full cadence in
[`SEO-PLAYBOOK.md §8`](docs/SEO-PLAYBOOK.md).

---

## Build guard

`check_site.py` fails the build on:

broken internal links · broken asset links · missing or duplicate `<title>` · missing or duplicate
meta description · a canonical that is not self-referencing · invalid JSON-LD · `.html` in any URL ·
a page without exactly one `<h1>` · a missing responsible-gambling helpline · a missing age
statement · a missing affiliate disclosure · About or Contact absent from the main nav · a
sitemap/filesystem mismatch · a missing robots.txt rule · a missing favicon size · any title wider
than 580px when rendered · duplicate element ids · a score or position claim that contradicts
`operators.json` · a score-order claim while `RANK_BY != "score"` · a page unreachable from the
mobile menu · a page unreachable from the desktop nav.

Titles are measured in **pixels**, not characters, because that is how Google truncates them.

`check_keywords.py` is the second guard: it measures coverage against the 253-term map, caps keyword
density at 1.1%, and fails on two pages competing for the same term. It reads `<main>` only — header
nav, hamburger and footer repeat the same link text on every page, and counting them inflates
coverage and fires the cannibalisation rule on navigation rather than on content.

---

## What is in this folder

Everything needed to rebuild the site from scratch, plus the evidence behind it.

| Path | What it is |
|---|---|
| `index.html`, `<page>/index.html` | The generated site — 43 pages plus one redirect stub. **Generated: do not hand-edit.** |
| `assets/css/site.css` | The only stylesheet. Cache-busted by content hash. |
| `images/authors/`, `logos/`, `favicon*` | Images. Author photos are derived; sources in `_build/authors-src/`. |
| `sitemap.xml`, `robots.txt`, `site.webmanifest` | Generated. `lastmod` is content-hash based, so an unchanged page keeps its old date. |
| `_redirects`, `.htaccess` | 301 for `/instant-withdrawals/` → `/fast-payout-casinos/`, in Netlify/Cloudflare and Apache form. |
| `_build/*.py` | The generator. `build.py` orchestrates; `p_*.py` are the page modules. |
| `_build/operators.json` | Facts only — licences, payouts, limits, revshare, order. One place to correct a fact. |
| `_build/voice.py` | Our own prose per operator, kept separate from the facts so a correction propagates without touching the writing. |
| `_build/lawdata.py` | The licensing timeline, penalties, helplines and bank blocks, sourced to the Acts and DIA guidance. |
| `_build/keywords.py` | The 253-term map. |
| `_build/research.py` | Harvested queries, themes, trends and market data used across the site. |
| `_build/research-src/` | The scripts that produced `research.py`, and their raw output. See its README. |
| `_build/authors-src/` | The five source portraits. `gen_authors.py` regenerates the site copies. |
| `check_site.py`, `check_keywords.py` | The two build guards. Neither is optional. |
| `docs/` | Competitor analysis, keyword strategy, SEO playbook, money-page research, deploy notes. |
| `docs/screenshots/` | Dated captures of verified layout states. |

Nothing in this folder depends on anything outside it.

---

## Notes

- **"IE-specific guidance"** in the original brief appears to be a leftover from an Ireland template.
  Everything here is New Zealand-specific: NZD, the DIA, the two 2025/2026 Acts, NZ banks and their
  gambling blocks, POLi, Neosurf, the 18/20 age split, NPC and netball, the four NZ helplines, IRD
  and the crypto-as-property treatment.
- **No `AggregateRating` on hub pages**, deliberately. Google restricts self-serving aggregate
  ratings and a rich-result penalty is a poor trade for a star. `Review` schema is used on the 19
  operator pages, where it belongs.
- **The `evospin.png` logo** is present in `logos/` but unused — it is not on the supplied operator
  list.
