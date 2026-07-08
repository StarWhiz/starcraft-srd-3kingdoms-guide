# Session Handoff: README-KR.md Localization

This document captures the full context of the localization work on the **3 Kingdoms EUD Map** guide so a future LLM session can continue seamlessly.

## Project

- **Repo:** `starcraft-srd-3kingdoms-guide` (StarWhiz / StarFroz)
- **Game:** Korean StarCraft Brood War custom map — "3 Kingdoms EUD Map" (삼랜디 / 삼국지 랜덤 디펜스)
- **Goal:** Maintain a Korean-language version of the English guide for Korean players.
- **Key constraint:** This is **Brood War (SC1)**, so prefer SC1 transliteration terminology over SC2 official translations.

## Files

- `README.md` — English source guide. **This is the source of truth for content** and the user edits it directly, then asks to sync KR.
- `README-KR.md` — Korean translation of the main guide. Created from scratch, hand-edited by the user, annotated with screenshot caption translations, and **kept in sync** as the English evolves.
- `media/` — screenshots referenced by both READMEs via root-relative paths `![](/media/filename)`. Paths must be preserved exactly in both files.
- **`T7-Mythic-Immortal-Combinations/README.md` + `README-KR.md`** — a separate sub-page (unit build recipes) that ALSO now has an English+Korean pair kept in sync. It has its own dedicated context doc: `ai-context/T7-Mythic-Immortal-Combinations-context.md`. Read that before touching it.

## Recurring task pattern (IMPORTANT for future sessions)

The steady-state work here is: **the user edits an English README, then says "I added more stuff, update the KR version."** The routine:
1. Read both the English and Korean files fully.
2. Diff them mentally to find what's new/changed/moved in English.
3. Apply the same change to the Korean file, reusing the established glossary + caption format.
4. Report exactly what was synced.

Changes seen so far include: new sections (RD 55 Boss Cheesing, RD 80/90 & RD 100 Boss patterns, Gameplay Demo links), reworked bullet lists (Mythic build descriptions), section **reordering** (New Map Versions moved to just before `# End`), and small link/stub additions. Watch for moves, not just additions.

## Work completed (3 sequential requests)

### Request 1 — Translate guide to Korean (DONE)
Produced `README-KR.md` as a full Korean translation of `README.md`. Preserved all image paths, URLs, and structure. Kept Korean hero names + romanizations in the unit reference table.

### Request 2 — Verify StarCraft terminology (DONE)
Verified via web search that key terms match the Brood War Korean community's usage:
- **psi emitter** → **사이오닉 방출기** (correct; official term. Do NOT confuse with 사이오닉 분열기 = Psi Disruptor)
- **mineral** → **미네랄** (SC1 transliteration, correct for BW; SC2 uses 광물)
- **scarab** → **스캐럽** (community term, correct for BW; official term is 갑충탄)

All three confirmed correct for the target audience. No changes were required.

### Request 3 — OCR red annotation text on screenshots (DONE)
Many screenshots have **red English annotation text** overlaid on them. Task: OCR that red text and add Korean translations into `README-KR.md` beneath each image.

**Caption format used** (consistent across all images) — a blockquote placed directly under the image, preserving the original English so readers can match labels on-screen:

```markdown
![](/media/example.png)

> 📷 **스크린샷 속 빨간 영어 설명 번역**
> - "Original English label" → 한국어 번역
```

**Images with captions added:** `1-autocombine`, `2-manualcombine`, `4-manualcombine-checkprogress`, `3-advancedcombine`, `5-upgrades`, `6-recyclet1s`, `7-kitingminibosses`, `8-tokenselection`, `9-miniquests`, `10-teamboss`, `a1` through `a7`, `z1-masterchart`, `z2-round80boss`, `z3-round90boss`.

**Images with NO red overlay** (intentionally skipped — only plain UI screenshots): `a8-gatcha.png`, `a9-pointspending.png`, `a10-mythicbonuses.png`. `0-title.png` is just the logo, no annotations.

**Image fix during the session:** `7-kitingminibosses.png` was originally the wrong image (a duplicate of the srdrecords.kr website screenshot). This was flagged to the user, who **replaced it** with the correct kiting/miniboss gameplay screenshot. Its caption was then re-OCR'd and updated to: "individual boss wave units", "Boss", health-color legend (Green=100%/Yellow=50%/Red=Almost Dead), and the kiting tip (circle the boss, press S between moves).

## Glossary / translation conventions established

| English | Korean used | Notes |
|---|---|---|
| psi emitter | 사이오닉 방출기 | verified |
| mineral(s) | 미네랄 | SC1 term |
| mineral stack | 미네랄 더미 | |
| scarab (selection token) | 스캐럽 (선택 토큰) | SC1 community term |
| Tier 1–7 | 1티어 ~ 7티어 (also 1성~7성 / 6성 etc. in chart) | |
| auto combine | 자동 조합 | |
| manual combine | 수동 조합 | |
| advanced combine | 고급 조합 | |
| hallucination | 환영 | |
| blink | 블링크 | |
| lock on | 고정 | |
| Healer | 힐러 | |
| Team Mate | 팀원 | |
| Boss | 보스 | |
| Mythics / Immortals / T7 (chart labels) | 신화 / 불멸 / 7성 | |

Hero names in the unit table keep both the Korean name and a romanization, e.g. `장비 (Zhang Fei) = T6 SCV`.

## Consistency reviews (both guides)

The user also periodically asks to "check the main guide/sub-page for inconsistencies" (not just sync). Same report-then-confirm style as the sub-page: flag issues, fix the clear-cut ones, leave tier/quantity judgment calls for the author. Checks that have caught real bugs in the **main** README:
- **Bilingual mission tags** — in the "Individual Missions" section, English unit names carry a bold Korean tag (e.g. `T1 Dark Templar **검병**`). The tag must match the unit: **검병**=Dark Templar, **기병**=Zergling/Cavalry, **궁병**=Marine/Archer, **창병**=Drone/Spearman. A real bug was `T1 Dark Templar **기병**` (should be 검병). This gotcha is unique to the bilingual lists.
- **Tier sanity** — same as the sub-page (e.g. a "T1 Hydralisk" tip that should be T2; Hydralisk is T2/가후).
- **Naming/spelling** — "Interceptor" (not Intercepter/Intercepters); "Hydralisk" vs "Hydra" drift.
- When the English is fixed, mirror every fix into `README-KR.md` (the KR mission lines carry the same Korean tags, so the 검병/기병-type fixes apply there too).

Difficulty caps (now stated in the guide, handy context for the boss-section naming): **Easy → RD 70**, **Normal → RD 90** (RD 80/90 & RD 90/90 bosses), **Hard → RD 100** (RD 100 boss).

## Status

- Original localization (full translation, terminology check, OCR captions) is **complete**.
- The main `README-KR.md` has since been kept in sync through several rounds of English edits (RD 55 cheese, RD 80/90 + RD 100 boss patterns, gameplay demo links, Mythic-list rework, New Map Versions reorder).
- The `T7-Mythic-Immortal-Combinations` English+Korean pair is also complete and in sync.
- **Both main guides are date-free now.** The "Date Authored / Date Last Modified" lines were removed from the `# End` section of `README.md` at the user's request, and removed from `README-KR.md` to match. Do NOT re-add them.
- **Nothing has been committed yet** across any of this work. The user has been offered a commit multiple times and keeps deferring — offer, don't assume.
- **`ai-context/` is now tracked (no longer gitignored).** There used to be a `.gitignore` whose only entry was `ai-context/`; the user decided these handoff docs are safe to commit, so the `.gitignore` was deleted and this folder should be included in the eventual commit.

## Possible next steps

- Commit everything if/when the user approves (READMEs, the sub-page + its images, the `ai-context/` docs, and the `.gitignore` deletion).
- Optionally translate the on-screen **English UI labels** in `a8-gatcha.png`, `a9-pointspending.png`, `a10-mythicbonuses.png` (currently skipped because they have no red annotations).
- Keep both README-KR files in sync whenever their English counterparts change.

## Author context

- Guide author: **StarFroz** (US West + KR servers).
- A NOTE blockquote near the top of `README-KR.md` discloses that the Korean guide was AI-translated from the English original.
- Short URLs: English `https://urls.starfroz.com/srd`, Korean `https://urls.starfroz.com/srd-kr`.
