# BanProof AI — MCP Server

> Audit TikTok Shop and Amazon affiliate video scripts for policy violations before creators record.

## What it does

BanProof AI scans video scripts against TikTok Shop content policies, Amazon Associates Operating Agreement, and FTC disclosure guidelines. It flags the exact phrases that rack up violation points or trigger account strikes, returns safe rewrites, shows your total TikTok violation point exposure (12 points = ban), and generates ready-to-submit appeal text when you've already been hit.

## Tools

### `audit_script`

Scan a script for policy violations before recording.

**Input:**
- `script` (string, required) — full video script text
- `product_url` (string, optional) — product page URL to cross-check script claims against actual product claims

**Output:** flagged phrases with reasons and safe rewrites, overall risk level (`safe` / `elevated` / `high`), TikTok violation point total per violation and in aggregate

**Detects:**
- Medical / health claims (`cures`, `clinically proven`, `FDA approved`, before/after without disclaimer)
- Guarantee and refund guarantee claims
- False certifications and unverified endorsements
- Urgency / scarcity language (`limited time only`, `only 3 left`, countdown timers)
- Fake social proof (`going viral`, `everyone is buying`, unverified sales volume)
- Income claims (`earn $500/day`, `passive income stream`)
- Missing FTC disclosure (`#ad` / `#sponsored` absent on commercial content)
- Price claim violations (`lowest price ever`, `was $X`, `save X%` without source)
- AIGC / AI voice disclosure requirement (TikTok policy 2024, AI voice LIVE ban July 2026)
- Third-party testimonials and before/after transformations without required disclaimers
- Product overclaims vs the actual product page (when `product_url` provided)

---

### `generate_appeal`

Write a ready-to-submit appeal for a platform violation notice.

**Input:**
- `violation_notice` (string) — the full text of the violation notice you received
- `platform` (`tiktok` | `amazon` | `youtube`)

**Output:** appeal text ready to paste into the platform's appeal form, with character count vs platform limit (TikTok: 800 chars)

---

## Connect

**Hosted endpoint:** `https://banproof.io/mcp`

Auth: OAuth 2.0. Create a free account at [banproof.io](https://banproof.io) — 3 audits/month, no credit card required.

Compatible with Claude, Cursor, and any MCP-compatible client.

## Example — `audit_script`

**Input:**
```
This serum will completely cure your acne in 3 days — guaranteed results or your money back. FDA approved and clinically proven. Only 2 left in stock, limited time only! Link in bio.
```

**Output:**
```
⚠ 5 violations detected. Risk level: high — 7 TikTok violation points (12 = ban)

1. [Absolute medical claim · 2pt] "cure your acne in 3 days" → "support clearer-looking skin over time"
2. [Guarantee / results claim · 1pt] "guaranteed results or your money back" → "so many creators love how it performs"
3. [False certification claim · 2pt] "FDA approved" → "made with carefully selected ingredients"
4. [False scarcity claim · 1pt] "Only 2 left in stock" → "while supplies last"
5. [FTC disclosure required · 1pt] "Link in bio" → (add #ad or #sponsored)
```

## Pricing

| Plan | Price | Audits |
|---|---|---|
| Free | $0/month | 3/month |
| Creator | $14.99/month | 50/month |
| Brand | $34.99/month | 200/month, 5 seats |

## Links

- Website: [banproof.io](https://banproof.io)
- MCP endpoint: [banproof.io/mcp](https://banproof.io/mcp)
- Pricing: [banproof.io/pricing](https://banproof.io/pricing)
