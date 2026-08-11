# BanProof AI — MCP Server

> Audit TikTok Shop and Amazon affiliate video scripts for policy violations before creators record.

## What it does

BanProof AI scans video scripts against TikTok Shop content policies, Amazon Associates Operating Agreement, and FTC disclosure guidelines. It flags the exact phrases that rack up violation points or trigger account strikes, and returns safe rewrites that keep the hook and CTA intact.

**MCP tool:** `audit_script`  
**Input:** `script` (string) — the full video script text  
**Output:** flagged phrases, violation categories, safe rewrites, overall risk level (safe / elevated / high)

## Connect

**Hosted endpoint:** `https://banproof.io/mcp`

Auth: OAuth 2.0 via Supabase. Create a free account at [banproof.io](https://banproof.io) — 3 audits/month, no credit card required.

Compatible with Claude, ChatGPT, Cursor, and any MCP-compatible client.

## Example

Input:
```
This serum will completely cure your acne in 3 days — guaranteed results or your money back. FDA approved and clinically proven.
```

Output:
```
3 violations detected (risk: high)
1. [Absolute medical claim] "cure your acne in 3 days" → "support clearer-looking skin over time"
2. [Guarantee claim] "guaranteed results or your money back" → "so many creators love how it performs"
3. [False certification] "FDA approved" → "made with carefully selected ingredients"
```

## Pricing

| Plan | Price | Audits |
|---|---|---|
| Free | $0/month | 3/month |
| Creator | $19.99/month | 50/month |
| Brand | $49.99/month | 200/month, 5 seats |

## Links

- Website: [banproof.io](https://banproof.io)
- MCP endpoint: [banproof.io/mcp](https://banproof.io/mcp)
- Pricing: [banproof.io/pricing](https://banproof.io/pricing)
