# Context: T7-Mythic-Immortal-Combinations/README.md

This document explains what the `T7-Mythic-Immortal-Combinations/README.md` page is, so a future LLM session can maintain it without re-deriving everything.

## What this page is

A **visual reference of unit build recipes** for the high-end units in the 3 Kingdoms EUD map (삼랜디, StarCraft Brood War). It is a standalone sub-page of the main guide, linked from the main `README.md` (Shop Spending Tips + Individual Units Translated both point to it).

Its whole purpose is to show, unit by unit, **what you combine to build each end-game unit**, backed by a screenshot. The author's own disclaimer at the top (line 7) says to trust the **screenshots over the text recipes**, because the text is hand-entered and error-prone. That framing matters: the images are the source of truth; the bullet lists are a best-effort transcription.

## Structure

Three top-level (`#`) unit sections plus two `##` bonus sections at the end:

1. **`# Tier 7 Units`** — the 10 T7 units (Civilian, Dark Templar, Dark Archon, Ghost, Zealot, Tassadar, Dragoon, Hydralisk, Ultralisk, Zerg Kerrigan). Headings are **not** numbered.
2. **`# Mythics`** — 7 Mythic units, headings **numbered `## 1.`–`## 7.`** (Marine, SCV, Sarah Kerrigan, Blue Archon, Zergling, Defiler, Medic). Some credited to "Mister.K".
3. **`# Immortals`** — 8 Immortal units, headings **numbered `## 1.`–`## 8.`** (Civilian, Lighter Dark Templar, Dark Archon, Zealot, Templar, Hydralisk, Darker Dark Templar, Zerg Kerrigan/Zerrigan). Some are still `No Data` placeholders. Credited to Scroto.Baggins and TKKTKK.
4. **`## Mythic Bonuses`** and **`## Immortal Bonuses`** — flat `No.X - <unit>: <effect>` lists (NOT per-unit `##` entries, no images). The `No.X` numbers **must line up** with the numbered Mythic/Immortal headings above (e.g. Mythic Bonus No.7 = Medic = Mythic #7; Immortal Bonus No.3 = Dark Archon = Immortal #3).

The numbering on Mythic/Immortal headings is load-bearing: the credits block and both Bonuses sections reference units by `No.X`, so heading numbers and those references must stay in sync.

### Per-unit entry format

```markdown
## [N.] <Unit Name> (optional "(aka ...)" / "(Templar)" alias)
> [!NOTE]  (optional — special rules, e.g. healer-only, no-T7-required)
- <recipe line: quantity + tier + unit, "+" joins multiple on one line>
- ...
- (Builds from ...)  ← notes which component is the "base" unit that upgrades into this one

Active Ability (Q): <description>   ← optional; most units have one. Key is (Q) EXCEPT Mythic Medic which is (E) — this is CORRECT, confirmed by the author (her blink-heal is on E).

![](/media/<image-file>)
```

Entries with no screenshot yet say `No Data` (sometimes with a reason, e.g. "No Data until I unlock on BETA 22 patch") or `No Screenshot Available (I don't have it yet)` instead of an image.

**Alias note:** "T7 Tassadar" is also called "Templar" in-game — written as `T7 Tassadar (Templar)` and referenced that way in the Immortal Templar and Mythic Sarah Kerrigan recipes. There is no separate "T7 Templar" unit (that was a past bug).

## Image conventions

- Images live in the repo-root `media/` folder, referenced with **root-relative paths** `![](/media/...)` (renders correctly on GitHub from this subfolder).
- Filename prefixes: `T7-*`, `mythic-*`, `immortal-*`. Extensions are mixed (`.jpg` / `.png`) — match whatever is actually on disk, don't assume.
- Note: filenames don't always match headings exactly (e.g. heading "T7 Hydralisk" uses image `T7-Hydra.jpg`). That's fine — the filename is internal and not user-facing.

## How to review / maintain this page (consistency checklist)

When the user adds units and asks to "check for inconsistencies," run these checks — this is the routine we've converged on:

1. **Broken image links** — every `![](/media/x)` must resolve to a real file. Quick check (works for either README.md or README-KR.md — same paths):
   ```bash
   for f in $(grep -oE '/media/[^)]+' T7-Mythic-Immortal-Combinations/README.md | sed 's#/media/##'); do [ -f "media/$f" ] || echo "MISSING: $f"; done
   ```
   Also list `ls media | grep -iE '^(T7-|mythic-|immortal-)'` to see what exists.
2. **Tier sanity** — a recipe line's tier must be a tier that unit actually exists at, per the unit table in the main `README.md` (see below). Past real bugs: "T2 Marine" (Marine is T1/T5), "T2 Defiler" (Defiler is T3), "T2 Dark Templar"/"T2 Zergling" in Immortal Civilian (both should be T1).
3. **Spelling** — recurring typos to watch: "Defilier"→"Defiler", "Wriath"→"Wraith", "Avaiable"→"Available", "smal"→"small".
4. **Naming consistency** — the same unit should be called the same thing everywhere. Past issues: Interceptor vs "interceptor" vs "Intercepter"; "T7 Hydra" vs "T7 Hydralisk"; "T7 Kerrigan" vs "T7 Zerg Kerrigan"; credits-block labels drifting from headings (e.g. "Light DT" vs heading "Lighter Dark Templar", "Hydralisk" vs heading "Hydra").
5. **Numbering sync** — Mythic/Immortal heading numbers (`## N.`) must match the `No.N` references in the credits block and the two Bonuses sections. Watch malformed forms like `No1.` vs `No.1`.
6. **Structural** — Immortals must stay under their own `# Immortals` header (they were once nested under `# Mythics`).
7. **No "T7 Templar"** — that unit doesn't exist; it's `T7 Tassadar (Templar)`.

**Important working style the user prefers:** report the findings and let *them* fix, or fix only the clear-cut spelling/structural/naming issues. **Do not silently change tier numbers or recipe quantities** — only the author knows the correct values (the screenshots are ground truth, and the LLM can't always read them precisely). Offer, then wait. This report-then-confirm loop has run several times and works well.

## Unit tier reference (from main README.md "Individual Units Translated")

- **T6:** Zhang Fei 장비 = SCV · Son Gyeon 손견 = Probe · Xiahou Yuan 하후연 = Drone
- **T5:** Jo Un 조운 = Marine · Sun Ce 손책 = Corsair · Jang Ryo 장료 = Zergling · Dong Tak 동탁 = Ursadon ("Bear")
- **T4:** Hwang Chung 황충 = Ghost · Gwan Pyeong 관평 = Firebat · Gam Nyeong 감녕 = Dark Templar · Yuk Son 육손 = Dragoon · Gwak Ga 곽가 = Queen
- **T3:** Seo Seo 서서 = Wraith · Bang Tong 방통 = Dropship · Son Sang-hyang 손상향 = Probe · Neung Tong 능통 = Scout · Heo Jeo 허저 = Guardian · Sun Uk 순욱 = Defiler
- **T2:** Wi Yeon 위연 = SCV · Ma Cho 마초 = Vulture · Ju Tae 주태 = Zealot · So Gyo 소교 = Interceptor · Ga Hu 가후 = Hydra · Gyeon Hui 견희 = Scourge
- **T1:** Changbyeong 창병 = Drone · Geombyeong 검병 = Dark Templar · Gungbyeong 궁병 = Marine · Gibyeong 기병 = Zergling · Bangpaebyeong 방패병 = Broodling
- **Special:** Choseon 초선 = Medic (+1 mineral per round)

## Korean version — `T7-Mythic-Immortal-Combinations/README-KR.md`

This page now HAS a Korean translation (created for a friend), living beside the English in the same folder. **Keep the two in sync**: whenever the English page changes, mirror it into README-KR.md (the user asks for this explicitly, same as the main guide).

Conventions used in the KR version:
- Same structure, numbering, and `/media/...` image paths as the English — unchanged.
- Bilingual headings: Korean name + English in parens, e.g. `## 1. 신화 마린 (Mythic Marine)`, `## T7 시빌리언 (Civilian)`.
- Standard header note (AI-translated disclaimer + `영어 원문: [README.md](README.md)` link), matching the main README-KR style.
- Section names: `# 티어 7 (T7) 유닛` / `# 신화 (Mythic) 유닛` / `# 불멸 (Immortal) 유닛`; bonuses `## 신화 보너스` / `## 불멸 보너스`.
- Unit terminology matches the main guide glossary (see `README-KR-localization-context.md`): 프로브, SCV, 드론, 마린, 저글링, 다크 템플러, 디파일러, 가디언, 히드라리스크, 스커지, 인터셉터, 벌처, 질럿, 드라군, 고스트, 파이어뱃, 퀸, 레이스, 드랍십, 스카웃, 커세어, 브루들링, 태사다르, 케리건, 아콘, 울트라리스크.
- "Active Ability (Q/E)" → "액티브 스킬 (Q/E):"; "(Builds from X)" → "(X에서 제작)"; "No Data" → "데이터 없음"; "No Screenshot Available" → "스크린샷 없음".
- **Naming choice to remember:** "T5 Bear" is translated **T5 베어** here (the English page uses "Bear"), even though the main guide calls the same unit **우르사돈** (동탁/Ursadon). Left as 베어 to match this page's source; the user is aware.
- The malformed `No1.` typo in the English credits was written **correctly as `No.1`** in the KR version.

## Related

- Main guide: `README.md` (English) and `README-KR.md` (Korean translation, kept in sync — see `ai-context/README-KR-localization-context.md`).

## Status

- Page is actively being filled in; a few entries are still `No Data` (Immortal Dark Archon — pending BETA 22 unlock; Immortal Darker Dark Templar).
- Both English and Korean versions are currently **in sync**. All ~22 image links resolve, tiers are consistent with the unit table, numbering/credits/bonuses line up, and spelling/naming is clean.
- **Confirmed non-bug:** Mythic Medic's active ability is on the **(E)** key (all other units use Q) — intentional, verified by the author.
- Uncommitted: this page, the KR version, their `media/` images, and other repo changes were not yet committed at last check.
