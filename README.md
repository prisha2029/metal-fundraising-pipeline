# Metal Fundraising Pipeline: a Claude skill

A [Claude skill](https://docs.claude.com/en/docs/agents-and-tools/agent-skills/overview) that runs a founder's pre-seed or seed raise on **[Metal](https://app.metal.so)**, from prep through the close.

> Unofficial and community-made. Not affiliated with Metal or LinkedIn.

## What it does

1. **Prep:** checks your deck and data room, sketches how the round could be filled, and sanity-checks the valuation.
2. **Competitors:** maps your 5 closest competitors, flags their investors as conflicts, and drafts your "how are you different?" answer.
3. **Pipeline:** builds a filtered Metal pipeline ordered by region, relatability or strong fit, with a boost for Content Signals.
4. **Warm paths:** maps routes to each investor and sends paced LinkedIn connection invites to founders from the investor's last 5 deals.
5. **Follow-ups:** drafts warm-intro requests for you to send and keeps pipeline stages current.
6. **Meetings:** prepares briefs, runs mock calls, and turns your notes into pipeline updates.
7. **After the raise:** investor updates and follow-on prep.

### Built-in guardrails
- **No cold outreach to investors.** No cold emails, InMails or email Sequences. Investors are reached only through warm intros. Claude drafts; you send.
- **Dry-run mode.** Say "dry run" and Claude goes through every step, labels each planned action "WOULD:", and changes nothing. It ends with a pass/fail check against your rules.
- Approval before each Richard AI pipeline edit and before each LinkedIn batch.
- LinkedIn pacing of about 15–20 invites a day and about 80 a week.
- Unverified data, estimates and web-only data are always labelled.
- Competitor founders are never contacted, and the closest competitor's lead investors are never pitched.

## Requirements
- Claude with skills enabled (claude.ai, the Claude desktop app or Claude Code).
- A browser Claude can drive (Claude in Chrome or the built-in browser), signed in to **app.metal.so** and **linkedin.com**.
- A Metal account with your company set up.

## Install

**claude.ai / Claude app:** download this repo as a ZIP (or use `metal-fundraising-pipeline.zip` from Releases), then go to *Settings → Capabilities → Skills → Upload skill* and upload the `metal-fundraising-pipeline` folder as a ZIP.

**Claude Code:**
```bash
git clone https://github.com/prisha2029/metal-fundraising-pipeline.git
cp -r metal-fundraising-pipeline/metal-fundraising-pipeline ~/.claude/skills/
```

## Usage
```
Run my Metal fundraising pipeline for <Company> — dry run
```
Claude confirms which company is raising, asks for any missing details (raise size, ordering, regions, exclusions, invite note), and then works through the steps above. Drop "dry run" when you want it to make changes.

## A note on LinkedIn
Automating actions on LinkedIn may conflict with LinkedIn's User Agreement. The skill keeps invites slow, asks for approval on each batch, and stops at any limit or verification warning. You're responsible for how you use it.

## License
MIT. See [LICENSE](LICENSE).
