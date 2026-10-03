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

### Other sub-guides (added after the original localization work)

The repo has grown several sub-guide folders beyond the main guide + T7 page. Their sync status as of 2026-09-22:

| Folder | EN | KR | Notes |
|---|---|---|---|
| `3man-normal-guide/` | yes | yes | in sync |
| `hard-mode-guide/` | yes | yes | KR created 2026-09-22 |
| `newbie-quick-start/` | yes | **no** | English only; main README links to it |
| `aws-for-KR-servers/` | yes | **no** | English only (AWS setup for KR servers) |
| `geforcenow-for-KR-servers/` | yes | **no** | English only; linked from `# End` |

Sub-guide KR files follow the same header convention:
```markdown
영어 원문: [README.md](README.md)

> [!NOTE]  
> 이 가이드는 AI를 통해 원문 영어 가이드에서 번역되었습니다.
```
Cross-guide links that point at a main-README anchor should point at the **KR** anchor from a KR page (e.g. `README-KR.md#rd-100-보스`), since GitHub anchors keep the Korean heading text.

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
| Tier 1–7 | 1티어 - 7티어 (also 1성/6성 etc. in chart) | see tilde gotcha below |
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
| Sarah Kerrigan | 사라 케리건 | verified |
| Medic / Combat Medic | 메딕 | verified; SC2 완역 is 의무관 — do NOT use |
| Infested Terran | 인페스티드 테란 (자폭맨) | verified; SC2 완역 is 감염된 테란. 자폭맨 is the everyday BW community name and is worth glossing on first use |
| Dark Templar / DT | 다크 템플러 (다템) | verified; SC2 완역 is 암흑 기사 — do NOT use. Never leave a bare English "DT" in KR text |

### Verified BW 음역 vs SC2 완역 (verified 2026-09-23)

**The rule:** StarCraft: Remastered ships **two** Korean name sets — 음역 (transliteration of the English) and 완역/의역 (fully translated). The Korean BW community overwhelmingly uses 음역, and **this project uses 음역 everywhere.** SC2's official Korean names are the 완역 forms and are wrong for this audience.

**Why this is worth writing down:** Korean reference pages are inconsistent, so "checking a wiki" can actively mislead you. On ko.wikibooks, the **Zerg and Terran** unit pages list only 완역 names, while the **Protoss** page lists 음역 names. Copying names off whichever page you happened to open will produce a mixed, wrong glossary.

Units that appear in these guides, with the 완역 form to avoid:

| Unit | Use this (음역) | NOT this (완역 / SC2) |
|---|---|---|
| Marine | 마린 | 해병 |
| SCV | SCV | 건설로봇 |
| Firebat | 파이어뱃 | 화염방사병 |
| Medic / Combat Medic | 메딕 | 의무관 |
| Ghost | 고스트 | 유령 |
| Vulture | 벌처 | 시체매 |
| Wraith | 레이스 | 망령 |
| Dropship | 드랍십 | 수송선 |
| Drone | 드론 | 일벌레 |
| Queen | 퀸 | 여왕 |
| Defiler | 디파일러 | 파멸충 |
| Scourge | 스커지 | 갈귀 |
| Guardian | 가디언 | 수호군주 |
| Broodling | 브루들링 | 공생충 |
| Infested Terran | 인페스티드 테란 | 감염된 테란 |
| Dark Templar | 다크 템플러 | 암흑 기사 |
| Zealot | 질럿 | 광전사 |
| Dragoon | 드라군 | 용기병 |
| Probe | 프로브 | 탐사정 |
| Interceptor | 인터셉터 | 요격기 |
| Corsair | 커세어 | 해적선 |

Same in both sets (no trap): 저글링, 히드라리스크, 울트라리스크, 태사다르, 케리건, 우르사돈.

All of these were already correct in the guides. The table exists so a future session does **not** "fix" them toward SC2 wording.

**Community nicknames worth glossing** (the guides' readers use these in chat):
- **Infested Terran** → **자폭맨** is what players actually say; the formal name is considered awkward ("이름이 어렵고 보기도 쉽지 않아서 별명인 자폭맨으로 통용된다"). Glossed on first use in the hard-mode guide.
- **Dark Templar** → 다크 / **다템** / 닥템. **Never leave a bare English "DT" in Korean prose** — that was a real miss, fixed 2026-09-23 in `hard-mode-guide/README-KR.md` and the main guide heading (now `## RD 90/90 다크 템플러(DT) 보스 패턴`).

**Two open spelling judgment calls** (left as-is, author's call — do not change unilaterally):
- **Archon**: guides use **아콘** (블루 아콘, 다크 아콘); ko.wikibooks uses **아칸**. Both circulate in the BW community.
- **Scout**: guides use **스카웃**; ko.wikibooks uses **스카우트**.

Sources checked:
- https://ko.wikibooks.org/wiki/스타크래프트/유닛과_건물_목록/저그 (완역 Zerg names)
- https://ko.wikibooks.org/wiki/스타크래프트/유닛과_건물_목록/테란 (완역 Terran names)
- https://ko.wikibooks.org/wiki/스타크래프트/유닛과_건물_목록/프로토스 (음역 Protoss names)
- https://namu.wiki/w/스타크래프트/용어 (community nicknames: 자폭맨, 다템)
- https://namu.wiki/w/암흑%20기사(스타크래프트%20시리즈) (Dark Templar 음역 vs 완역)
- https://ko.wikipedia.org/wiki/사라_케리건 (Sarah Kerrigan = 사라 케리건)

Hero names in the unit table keep both the Korean name and a romanization, e.g. `장비 (Zhang Fei) = T6 SCV`.

## GOTCHA: never use `~` for ranges in Korean text

Korean writing normally uses `~` for ranges (`T3~T4`, `8~10개`, `RD 19~25`), but **GitHub Flavored Markdown treats a single `~` as a strikethrough delimiter.** Two tildes anywhere in the same paragraph or list item pair up and everything between them renders crossed out. This shipped as a real bug in `hard-mode-guide/README-KR.md` and Korean players in-game noticed the crossed-out text before we did.

**Rule: use `-` for every range in the Korean files** (`T3-T4`, `8-10개`, `RD 19-25`). This also matches the English source, which already uses hyphens.

Check before committing any KR file:
```bash
for f in $(find . -name '*.md' -not -path './.git/*'); do awk -v F="$f" '{n=gsub(/~/,"~"); if(n>=2) printf "%s:%d: %s
", F, NR, $0}' "$f"; done
```

## GOTCHA: loan words from English confuse actual Korean players

Real in-game feedback (2026-09-22) from Korean players reading `hard-mode-guide/README-KR.md`: they could not parse **스폰** ("스폰이 뭔뜻이오"), and were unsure what **토큰** referred to. Another player translated for them: **스폰 = 소환**, **토큰 = 선택(권)** (the scarab that lets you pick a unit of that star tier). One summed the guide up as "한국말이긴한데 이상하게써있어서 이해하기어렵소" — *it's Korean, but it's written strangely so it's hard to understand.*

Conventions adopted in response, to reuse in every KR guide:
- **소환** for "spawn" (not 스폰). **소환을 끄다 / 켜다** for pausing and unpausing a line boss (not 정지).
- **선택권** for the token/scarab, defined on first use. Main-guide glossary term **스캐럽 (선택 토큰)** stays, but sub-guides should gloss it as 선택권.
- Make implied subjects explicit. English "pause the medic" means *the medic **line boss** spawn* — write **메딕 라인 보스 소환을 꺼두세요**, not just 메딕을 정지시키세요.
- "line is 30/80" means enemies remaining on your lane — write **라인에 남은 적이 30/80**.
- Korean players talk in **성** (2성, 3성, 7성), not 티어. Prefer 성급 in sub-guides; the main guide's unit table already uses `|3성|` notation.
- `hard-mode-guide/README-KR.md` now opens with an `> [!IMPORTANT]` **용어 안내** glossary block (라인 보스 / 소환 / 소환 끄기·켜기 / 선택권 / 깃발 / 딜 / 합치기 / 성급). Copy that pattern into any sub-guide that leans on loan words.
- **플래시 (flash)**: **confirmed by the author** — it is the bonus for combining to a given tier *first*, ahead of other players. Gloss it as **"남들보다 먼저 조합해서 받는 보너스"** on first use in a guide, then keep the loan word 플래시. Already applied in `hard-mode-guide/README-KR.md` (glossary block) and `3man-normal-guide/README-KR.md`.

## Consistency reviews (both guides)

The user also periodically asks to "check the main guide/sub-page for inconsistencies" (not just sync). Same report-then-confirm style as the sub-page: flag issues, fix the clear-cut ones, leave tier/quantity judgment calls for the author. Checks that have caught real bugs in the **main** README:
- **Bilingual mission tags** — in the "Individual Missions" section, English unit names carry a bold Korean tag (e.g. `T1 Dark Templar **검병**`). The tag must match the unit: **검병**=Dark Templar, **기병**=Zergling/Cavalry, **궁병**=Marine/Archer, **창병**=Drone/Spearman. A real bug was `T1 Dark Templar **기병**` (should be 검병). This gotcha is unique to the bilingual lists.
- **Tier sanity** — same as the sub-page (e.g. a "T1 Hydralisk" tip that should be T2; Hydralisk is T2/가후).
- **Naming/spelling** — "Interceptor" (not Intercepter/Intercepters); "Hydralisk" vs "Hydra" drift.
- When the English is fixed, mirror every fix into `README-KR.md` (the KR mission lines carry the same Korean tags, so the 검병/기병-type fixes apply there too).

Difficulty caps (now stated in the guide, handy context for the boss-section naming): **Easy → RD 70**, **Normal → RD 90** (RD 80/90 & RD 90/90 bosses), **Hard → RD 100** (RD 100 boss).

## Sync round — 2026-09-22

The user asked to bring every Korean file up to date with English and to create the hard-mode KR guide. What changed:

**`README-KR.md`**
- Added the newbie-quick-start pointer to the top NOTE block.
- Line Bosses: added the missing "Vespene Gas = time remaining" line.
- Scarabs: restored the "second most important part" framing and added the missing token-color list (회색/파란색/노란색/초록색 토큰 = T2/T3/T4/T5).
- Individual Missions: replaced the stale T1/T3/T4 tips with the current English ones (T1 → turn on auto T1; T2 → completes naturally, turn on auto T2; T3 → Guardian helps, both missions give a T3 token), dropped the KR-only "프로브는 다목적입니다" T4 tip that English no longer has, and added the Keikaku missions chart (`/media/keikakus-missions.png`) under T5.
- **Deleted `## RD 55 보스 치즈(꼼수) 공략`** to match commit `1e6d1f5` ("Remove RD 55 Boss Cheesing Guide").
- Rewrote `## RD 100 보스` to the current English text (new video link, 5,000,000 HP bubbles, invulnerability tanking rotation, SCV/Archon 3-tank limit). The old KR text still said the author had never beaten it.
- Added `## RD 110 보스`.
- Conclusion: channel fixed from `boss hunt` / `/join boss hunt` → `srd` / `/join srd`.
- Unit table: `T2 히드라` → `T2 히드라리스크`.

**`T7-Mythic-Immortal-Combinations/README-KR.md`**
- Added the `# 불멸 (Immortal) 유닛` intro sentence about lootbox items.
- Added `- 필요한 루트박스 아이템: X` to all 8 Immortals (브루들링 / 다크 템플러 / 프로브 / 질럿 / 파이어뱃 / 저글링 / 퓨마(벵갈라스) / 메딕).
- Immortal No.7 Darker Dark Templar: `데이터 없음` → full recipe (English now has one).
- Added `# Keikaku의 영웅 요약 차트` and `# 아이템 확률 상점`.

**`hard-mode-guide/README-KR.md`** — created from the English guide.

**`3man-normal-guide/README-KR.md`** — checked, already in sync, untouched.

**Known open issue (flagged to the user, NOT auto-fixed):** both `3man-normal-guide/README.md` and its KR version link to `starcraft-srd-3kingdoms-guide#rd-55-boss-cheesing-guide`, which is now a dead anchor since that section was removed from the main English README. The fix belongs in the English source first.

## Status

- Original localization (full translation, terminology check, OCR captions) is **complete**.
- The main `README-KR.md` has since been kept in sync through several rounds of English edits (RD 55 cheese, RD 80/90 + RD 100 boss patterns, gameplay demo links, Mythic-list rework, New Map Versions reorder).
- The `T7-Mythic-Immortal-Combinations` English+Korean pair is also complete and in sync.
- **Both main guides are date-free now.** The "Date Authored / Date Last Modified" lines were removed from the `# End` section of `README.md` at the user's request, and removed from `README-KR.md` to match. Do NOT re-add them.
- **The earlier work HAS since been committed** (the repo is on `main` with commits through `b726e9f`). The 2026-09-22 sync above was left uncommitted at the end of that session — offer a commit, don't assume.
- **`ai-context/` is now tracked (no longer gitignored).** There used to be a `.gitignore` whose only entry was `ai-context/`; the user decided these handoff docs are safe to commit, so the `.gitignore` was deleted and this folder should be included in the eventual commit.

## Possible next steps

- Commit everything if/when the user approves (READMEs, the sub-page + its images, the `ai-context/` docs, and the `.gitignore` deletion).
- Optionally translate the on-screen **English UI labels** in `a8-gatcha.png`, `a9-pointspending.png`, `a10-mythicbonuses.png` (currently skipped because they have no red annotations).
- Keep both README-KR files in sync whenever their English counterparts change.

## Author context

- Guide author: **StarFroz** (US West + KR servers).
- A NOTE blockquote near the top of `README-KR.md` discloses that the Korean guide was AI-translated from the English original.
- Short URLs: English `https://urls.starfroz.com/srd`, Korean `https://urls.starfroz.com/srd-kr`.
