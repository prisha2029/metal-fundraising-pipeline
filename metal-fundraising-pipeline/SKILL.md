---
name: "metal-fundraising-pipeline"
description: "Run a founder's raise on Metal (app.metal.so): competitor conflicts, filtered pipeline, LinkedIn invites to portfolio founders, warm intros, meeting prep and investor updates."
---

# Metal Fundraising Pipeline

This skill runs a founder's fundraise on **Metal (app.metal.so)**, from setup through to after the round closes:

1. **Prep:** check the deck and data room, and plan who could fill the round.
2. **Competitors:** track the 5 closest competitors, flag their investors as conflicts, and write the competitor answer.
3. **Pipeline:** build a filtered Metal pipeline, ordered by region, relatability or strong fit, and boosted by Content Signals.
4. **Warm paths:** map the best route to each investor, then send LinkedIn invites to founders from each investor's last 5 investments.
5. **Follow-ups:** draft warm-intro requests to accepted founders and keep pipeline stages up to date.
6. **Meetings:** prepare briefs, run mock calls, and turn the founder's notes into pipeline updates.
7. **After the raise:** investor updates and follow-on prep.

**This skill only works with Metal.** If Claude can't reach a working Metal session, follow section 0b. Don't rebuild the pipeline in another tool.

**No cold outreach.** Claude never cold-emails, InMails or cold-messages investors, and never sets up Metal email Sequences to investors. Investors are reached only through warm intros. The only direct contact is LinkedIn connection invites to portfolio founders, and the founder later asks them for intros themselves.

---

## Dry-run mode

If the founder says **"dry run"**, "test", "scenario" or "don't change anything", Claude goes through every step and shows what it *would* do, but makes **no writes**:

- no Metal edits (no pipelines, tags, stages or notes, and no Richard AI plans approved),
- no LinkedIn invites,
- no tracker writes (output goes in chat or a scratch file).

Richard AI may still be used for research. Start every Richard prompt with: *"READ-ONLY RESEARCH. Do not create, edit or tag anything in any pipeline, and do not propose a plan to change data."*

Every planned action is labelled "WOULD:" (e.g. "WOULD: add [Fund] to pipeline, tags UAE Priority / Lead"). End with a pass/fail list against the founder's rules and anything that blocked the run. Dry-run mode stays on until the founder explicitly turns it off.

---

## 0. Requirements

### 0a. Access
- A browser Claude can drive (Claude in Chrome or the built-in browser), signed in to **app.metal.so** and **linkedin.com** as the founder. Load the matching browser skill before the first browser step.
- The founder's company exists in Metal, with a round set up if possible.
- Optional: a Google Sheet or Excel tracker. Offer to create one if none exists (see section 8).

### 0b. If Metal doesn't load
Metal is a heavy app and sometimes renders a blank page in an automated tab, especially on first load.

1. Wait about 5 seconds, then navigate to `app.metal.so` again. Once loaded it usually lands on `/richard-ai`.
2. If the page is still blank or shows a sign-in screen, **stop after 3 attempts** and ask the founder to open app.metal.so in that same Chrome window, sign in, and wait for the dashboard. Then retry once.
3. If it still fails, tell the founder plainly. Offer a **research-only pass**: competitors and investor shortlist from web research, every item marked "unverified – not from Metal", and nothing written anywhere.

### 0c. Working with Richard AI
- Richard runs multi-step "agent mode" jobs that take **3–10 minutes**. Poll the page every 30–60 seconds; don't give up early. Read step outputs with **"View Step N output"**.
- Richard states its **assumptions** at the top of each run. Check them against the founder's rules before trusting the output, and correct Richard if one is wrong.
- Richard draws on a saved **company memory and thesis** (shown under "USING → Memory"). If that describes a different company, say so, and state the right company explicitly in every prompt (see 1d).
- Richard mixes Metal data with web data and estimates. Keep its "estimate" and "unverified" labels.

---

## 1. Gather context (don't re-ask what Claude already knows)

### 1a. Purpose check (always first)
Confirm in one line **which company is raising and that it is actually raising**. Check memory and past chats for conflicts:
- the company is being **sold**, wound down or **pivoted** into a new company,
- the founder runs **more than one company**,
- the founder already has an active raise for a different company.

If there's a conflict, ask before doing anything else, e.g. "Acme Stays is listed for sale and Acme AI is the pivot. Are we raising for Acme Stays, Acme AI, or is this a scenario test?" If the company is publicly listed for sale, warn that investors may find the listing and ask how it squares with the raise.

### 1b. Founder Brief
Fill this from memory, past chats and uploaded context docs:

| Field | Example |
|---|---|
| Company and brand name (exact spelling) | Acme Stays |
| What it does, in one line | Student accommodation and relocation marketplace for international students |
| Customer and market | International students going to the UK, Europe, Australia, Singapore and UAE |
| Stage, raise size and valuation | Pre-seed, $100K at $1M |
| Traction | Commission deals with two booking platforms (PartnerCo A, PartnerCo B) |
| **Partners, customers and distributors** | PartnerCo A, PartnerCo B |
| **Constraints** | Entity in a Sharjah free zone; founder based in India and UAE; open to relocating? |
| Founder location | India and UAE |

Ask only for the fields you can't find, in **one** AskUserQuestion. **Constraints** matter because many programmes require relocation, residency or a specific free zone (e.g. Hub71 needs a founder in Abu Dhabi).

### 1c. Preferences (one AskUserQuestion)
1. **Pipeline ordering:** By region / By relatability (they've backed companies like ours) / By strong fit (thesis + stage + cheque size + leads rounds) / A mix
2. **Preferred regions**, and which comes first (e.g. UAE first, then GCC, then global)
3. **Exclusions:** regions, countries or named funds to skip, plus accelerators the founder is applying to separately
4. **LinkedIn invites:** No note / Short note (Claude drafts it, founder approves it once) / Ask each batch

Play the Brief and preferences back in 3–5 lines. Treat them as the rules for the rest of the run, and save the durable ones to memory if the founder agrees.

### 1d. Existing Metal setup
Before creating anything:
- **Company profile:** check which company Metal's profile and Richard's memory describe. If it's a different company, either ask the founder to update the profile, or (in a dry run) state the right company in every Richard prompt and flag the mismatch.
- **Pipelines:** list existing pipelines. **Reuse** one for the same company and round instead of duplicating.
- **Cross-company overlap:** if the founder has a pipeline or tracker for **another company**, flag every investor and portfolio founder that appears in both, so the founder doesn't pitch or invite the same people for two companies without meaning to.

---

## 2. Prep before any outreach

### 2a. Deck and data room check
In Metal, check that **Round Collateral** has a current deck and that a **Data Room** exists (deck, one-pager, metrics, cap table, team bios). If anything is missing, list it and pause outreach until at least the deck is uploaded.

### 2b. Round plan and valuation check
1. Sketch how the round could be filled. Small rounds look different from large ones:
   - **Up to ~$250K:** often one angel network or syndicate as lead (it may cover the whole round), plus a few angels.
   - **$500K–$1M:** a lead at ~$300K, 1–2 anchors at ~$150K, plus followers and angels.
2. Tag the pipeline to match ("Lead", "Anchor", "Follower"). If there are fewer than 2–3 realistic leads, say so plainly. That's the main risk to the round.
3. **Valuation sanity check:** show the implied dilution (e.g. $100K at $1M post-money = 10%). Compare it with recent pre-seed marks in the region (Richard and Content Signals help here), and flag anything investors may question, such as a public sale price far below the valuation.

---

## 3. Competitors and conflicts

**Goal:** the 5 closest competitors tracked, with their investors marked as conflicts.

1. In Metal, use **Discovery → Similar Companies** on the founder's company, and ask **Richard AI** to map competitors and their investors. In the prompt, describe the company explicitly, list known competitors, and say: *"[Partner names] are partners as well as competitors: list their investors separately as 'flag', don't exclude them."* Fill gaps with WebSearch.
2. Build a long list (10–15). Rank by closeness: same customer > same channel/product > same region > same stage. Pick the **top 5**, and call out the single closest one.
3. **Partner-competitors.** Compare the list with the Brief's partners. A company that is both a competitor and a partner is marked **"Partner-competitor"**:
   - its people are **not** put on the do-not-contact list automatically,
   - its investors are flagged "conflict – founder decides", not hard-excluded,
   - the founder confirms how to treat each one.
   Check Richard's assumptions here: it tends to exclude partner-competitor investors by default.
4. **Related companies:** watch for companies sharing founders or investors with a competitor (e.g. a sister company). Flag their investors as "possible conflict".
5. **Track them in Metal** on a board called **"Competitors – [Company]"** (or with a "Competitor" tag). For each one: what it does, region, total raised, lead investor(s), all investors and founder names. Where Metal's HQ or totals disagree with public sources, note both.
6. Build two lists and keep them for the rest of the run:
   - **Conflict investors:** every backer of the top 5. **Lead investors of the closest pure competitor are a hard exclusion.** Others are flagged "conflict – founder decides". Call out any conflict investors **based in the founder's preferred region** (e.g. Dubai-based Vy Capital behind Student.com).
   - **Do-not-contact founders:** founders and C-level people at long-list pure competitors.
7. **Competitor answer.** Draft a 3–4 sentence "How we differ from [closest competitor]" answer, plus a one-line version for the other four. Get the founder's edits, and save the final version to the tracker and the Data Room.
8. Show a short table (Company · What · Backers · Closeness · Partner?) and the positioning gap. Get confirmation before moving on.

### Competitor watch (every later run)
On each run, check whether a top-5 competitor has raised again. If one has, add its new investors to the conflict list, flag any already in the pipeline, and tell the founder.

---

## 4. Build the Metal pipeline

1. Create (or reuse, see 1d) a pipeline called **"[Company] – [Round]"**. Every investor starts in **Identified**.
2. Source candidates with Richard AI and **Discovery → Investor Search**, filtering by stage, **cheque size that fits the round**, sector/thesis and region. Also check **New Funds** and the **Co-investor Network**.
3. **Local check outside Metal.** Metal's data on small local networks and government programmes can be stale or empty. Always web-check the ones nearest the founder's entity and city (e.g. for a Sharjah company: Sheraa, Sharjah angel networks, Dubai Angel Investors, in5, Hub71). Add the ones that are active, marked "from web, not Metal".
4. **Filter out** before adding: conflict investors, excluded regions/funds, accelerators the founder applies to separately (add those as Tier 2 with "apply directly"), funds inactive for 18–24 months (mark them "confirm still active"), and programmes whose requirements clash with the Brief's **Constraints** (mark them "requires relocation/residency – founder decides").
5. **Order** by the founder's choice:
   - **By region:** preferred region first, ranked by fit inside each region.
   - **By relatability:** investors with the most portfolio companies close to the founder's (same customer, channel or market, without being competitors) come first.
   - **By strong fit:** a 1–5 score each on thesis, stage, cheque size vs. the raise, whether they lead, and regional presence. Highest total first.
6. **Content Signals boost.** Check Metal's **Content Signals** for investors who've posted in the last ~60 days about the founder's space. Move them up and tag them "Signal".
7. **Tags:** "[Region] Priority", "Tier 1" (realistic leads/anchors), "Tier 2", plus the round-plan tags from 2b. Note who can **lead** versus only **follow**.
8. For each investor: **partner contact** (mark "unverified" if unsure), **why it fits** (one line, with named portfolio companies), **watch out** (one line) and **cheque size** (marked "estimate" where Metal has no data, and both figures where sources conflict).
9. Richard AI proposes a plan before editing the pipeline. Approve it only if it matches the filtered list.
10. Show the ordered pipeline (top 10–15) and get the founder's go-ahead.

**Metal quirks:**
- Richard can **add** tags but can't **remove** them. Remove wrong tags by hand, or tell the founder which ones.
- The pipeline view can keep a hidden filter. Click **Clear Filters** before counting or checking.

---

## 5. Warm-intro map and LinkedIn invites

### 5a. Warm-intro map (Tier 1 first)
For each Tier 1 investor, use Metal **Paths** and **Connections** to find every route in, and rank them:

1. Founder knows the partner directly (Metal shows "Close" or a 1st-degree connection)
2. A mutual connection who knows the partner well
3. A founder from the investor's portfolio (from 5b)
4. A co-investor who knows the fund

Record the **best route** and a **backup route** for each investor. If the founder already has a direct or strong route, mark the investor "ready for warm intro" and skip portfolio-founder invites for them.

### 5b. Last 5 investments → founder list
For investors without a strong route yet:

1. Pull the **5 most recent investments overall, by date**, not filtered by sector. Note company, stage, date, amount and who led. If Metal holds fewer than 5, use what's there and note it.
2. Find **1–3 founders or C-level people** per company on LinkedIn.
3. **Skip** and log the reason for: do-not-contact founders, existing 1st-degree connections ("already connected – can ask directly"), people **already invited** (check the tracker, including any tracker for the founder's other company), dead links or no Connect option, and non-operators.
4. Log co-investors that keep showing up on a "Co-investors" list, after conflict and exclusion checks.

### 5c. Send invites (paced, approved)
1. **Show the batch** (Name · Company · Investor link) and get approval before sending. One approval per batch.
2. Follow the founder's note preference. If they chose a note, use the one approved text (under 200 characters, no pitch, no ask).
3. **Pacing:** about 15–20 invites a day and about 80 a week. Count invites sent in the last 7 days toward the limit. Stop on any limit or verification warning. Suggest withdrawing pending invites 2+ months old.
4. Whatever doesn't fit becomes a **dated next batch**. Offer a scheduled task to send it.
5. Connection invites only. No messages to founders until they accept (see 6a).

---

## 6. Follow-ups and stage tracking

### 6a. Warm-intro follow-ups
On each run, check LinkedIn for accepted invites. For each founder who accepted **2–3 days ago or more**:

1. Draft a short message for the founder to send **themselves**: friendly, specific to that founder's company, and asking whether they'd be open to introducing them to [partner] at [fund].
2. Attach a **forwardable blurb** (4–5 lines: what the company does, traction, raise size, why this fund fits, deck or data room link).
3. Log it as "intro requested" with the date. If there's no reply after 7 days, suggest one gentle nudge, then move on.

### 6b. Stage tracking
Keep Metal pipeline stages current:

`Identified → Intro requested → Intro made → Meeting scheduled → Met → Diligence → Term sheet → Committed / Passed`

(Create these stages in Metal if they don't exist.)

- Move investors when the founder reports progress, or when Claude sees it in Metal.
- On each run, list everyone **stuck 7+ days** in an active stage, with a suggested next step.
- For **Passed**, log the reason and point out any pattern.

---

## 7. Meetings

### 7a. Meeting brief (before each investor call)
One page:
- the partner's background and focus, plus any recent Content Signals posts,
- the fund's last 5 deals, cheque size, whether it leads, and any entry requirements (pitch night, demo, incorporation, relocation),
- links between the fund and the founder's market, and any competitor exposure,
- 3–5 likely objections (always including "how are you different from [closest competitor]" and, if relevant, valuation), each with a suggested answer,
- 3–4 questions the founder should ask.

### 7b. Mock call practice
Offer a practice pitch using Metal **Mock Calls**, set up with the brief's partner profile and objections. Afterwards, sum up what landed and which answers need tightening.

### 7c. Notes after the call
When the founder shares notes:
- update the Metal pipeline: stage, next step and date, interest level, open questions,
- draft the follow-up email for the founder to send. This goes only to investors the founder has already met; it isn't cold outreach,
- add any requested materials to the data-room checklist.

---

## 8. Track everything

Keep one tracker per company (Google Sheet if connected, otherwise an Excel file) with these tabs:

- **VCs:** Fund · Region · Partner · Tier · Lead/Follow · Round slot · Cheque (est.?) · Signal · Source (Metal/web) · Best route · Backup route · Why fit · Watch out · Stage · Last touch
- **Founders contacted:** Name · Company · Linked investor · LinkedIn URL · Note? · Date sent · Status (Pending / Accepted / Intro requested / Intro made / Skipped – reason)
- **Competitors & conflicts:** Company · Backers · Closeness · Partner? · Do-not-contact founders · Last checked
- **Co-investors:** Firm · Linked targets · Contact
- **Meetings:** Date · Fund · Partner · Outcome · Next step

Colour-code by status, and update the tracker on every run (except in dry-run mode).

---

## 9. After the raise

### 9a. Investor updates
Set up a monthly update template (optionally in Metal **Investor Updates**): headline numbers, wins, misses and lessons, asks, and what's next. Each month, fill it in from what the founder shares and draft it for review. Send it to existing investors, and as a lighter version to warm pipeline investors who passed or said "too early". Offer a monthly scheduled reminder.

### 9b. Follow-on prep
Use Metal **Follow-On Intelligence** to flag which current investors are likely to put in again next round, and what they usually need to see.

---

## Run summary (end of every run)
Keep it short:
- competitors tracked, and any new competitor raises,
- investors in the pipeline (Tier 1 / Tier 2 / Signal), and leads vs. the round plan,
- invites sent, accepted, intros requested and intros made,
- investors stuck 7+ days, and upcoming meetings,
- cross-company overlaps found,
- next batch date, and the tracker link or file,
- in dry-run mode: the WOULD list, the pass/fail checks, and any blockers.

---

## Rules that always apply

- **No cold outreach to investors**, no email Sequences to investors, and no messages sent on the founder's behalf. Claude drafts; the founder sends.
- Confirm which company is raising before anything else (1a), and make sure Metal and Richard are working on that company (1d).
- Use the company's exact brand spelling everywhere.
- Never contact pure-competitor founders. Never pitch the closest competitor's lead investors. Partner-competitors are the founder's call.
- Follow the founder's region and fund exclusions without exceptions.
- Get the founder's approval before Richard AI edits the pipeline and before each LinkedIn batch.
- Mark unverified details, estimates and web-only data as such. Never make up investments, portfolio companies or partner names.
- If Metal or LinkedIn behaves unexpectedly 2–3 times in a row (errors, blank pages, captcha, limit warnings), stop and ask the founder instead of retrying.
