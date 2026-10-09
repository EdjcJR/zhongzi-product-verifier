---
name: zhongzi-product-verifier
description: Verify Chinese capital (中資) background of brands and products from text descriptions or photo-extracted text. Use when user asks about 中資, Chinese capital, brand ownership, product origin verification, or uploads product photos/descriptions for 中資 check. Covers 3C, cosmetics, skincare, shoes, cars, toys and more. Triggers on keywords like 中資現形, 中資品牌, 查中資, 買得明白, Anker, 卡姿蘭, K-Swiss, 水羊, TOP TOY or similar brand queries.
---

# Zhongzi Product Verifier

## Overview

Perform structured verification of Chinese capital (中資) involvement in brands and products using a fixed search-and-analysis procedure derived from public investigative methods. Accept pure text input or text extracted from product photos. Output a concise risk report with evidence and confidence score. Scope is limited to Chinese capital, Chinese brands, or fake foreign brands. Pure OEM/MIC manufacturing is excluded.

**Credit**: The core methodology, evidence standards, tone, and many real-world cases are entirely from the careful public work of Threads account @unmasking.chinese.capital (中資現形記). This skill only systematizes their approach into a reusable format. Original account: https://www.threads.com/@unmasking.chinese.capital

## Instructions

### Input Handling

1. If the user provides a photo, first extract all visible text, brand names, model numbers, origin labels, and packaging claims using image description tools.
2. Convert the extracted information into a clean text summary of key entities (brand, company, model, origin claims, channel).
3. If only text is provided, parse brand name, model, official claims, and any other details directly.
4. Ask for missing critical information only if the input is too sparse to run verification (e.g. no brand name at all).

### Standard Verification Procedure (always follow this order)

1. **Extract official narrative**
   - Collect claims from brand website, packaging, advertising, or founder statements (e.g. "Hong Kong international brand", "founded in California", "French army boots", "American physician founded").

2. **Identify actual controlling entity**
   - Search for parent company full name, registered address (mainland China, Hong Kong, Taiwan, overseas).
   - Find major shareholders or actual controllers and their nationality/background.
   - Check Taiwan company registry (FindBiz / 商工登記) for local subsidiaries or agents.
   - Check Chinese company registry (GSXT / 企查查 / 天眼查 style sources) when relevant.

3. **Trace ownership and acquisition history**
   - Look for acquisition, share transfer, or privatization events with dates and amounts.
   - Note patterns such as "first act as agent, then acquire equity".
   - Distinguish controlling stake from pure financial investment.

4. **Cross-check trademarks and domain**
   - Especially useful for brands claiming Western origin. Check USPTO or other trademark databases for original registrant.

5. **Examine Taiwan market structure**
   - Identify official Taiwan agent or distributor and whether it is an independent Taiwanese company (no equity link).
   - Note presence on major platforms (momo, PChome, Shopee, physical counters).

6. **Check data and payment flows** (for connected devices or sponsorship platforms)
   - Review privacy policy for data transfer destinations and controlling entities.
   - For payment/sponsorship platforms, check registration jurisdiction, governing law, and payment processor display name.

7. **Group affiliation clarity**
   - List related brands under the same controller.
   - Explicitly separate brands that share a group name but are sold by independent Taiwanese agents with no capital link.

8. **Evidence threshold**
   - Only include facts supported by publicly verifiable sources.
   - Items with clues but insufficient evidence are excluded or marked as low confidence.
   - Pure manufacturing in China (MIC) without capital control is out of scope.

### Report Format

Always output a short structured report containing:

- **Brand / Product**: name and model if available
- **Risk level**: 低 / 中 / 高 / 極高 (or 證據不足)
- **Summary**: 1-3 sentences of the key finding
- **Key evidence**: bullet list of the strongest public facts (company, controller, acquisition, narrative discrepancy)
- **Taiwan status**: agent structure and availability
- **Confidence**: 高 / 中 / 低 + brief reason
- **Sources**: list of main public references used
- **Note**: "不是叫你抵制，只是讓你知道——買得明白就好。" (or equivalent neutral closing)

Keep the report concise and mobile-friendly. Do not recommend alternative products.

### Optional Contribution Format

After the main report, offer a short copy-paste block that the user can share to public channels (Threads, Discord, collaborative sheets) to help build collective knowledge. Format:

```
【中資查證貢獻】
品牌：
風險等級：
核心發現：
主要來源：
查證日期：
```

### Known Channel Reference (quick mode)

When the user only asks about a sales channel (especially Taiwan 3C channels), cross-reference the following snapshot ratios (data date 2026-10-08) before full verification:

- Water3F: brand 75%, product 92.5%
- 智選家: brand 70%, product 87.4%
- 先創: brand 52.9%, product 83.8%
- 東城: brand 47.6%, product 51.6%
- Others lower (see references/channel-data.md if needed)

Product-level Chinese-capital ratio is usually higher than brand-level ratio.

### Additional Rules

- Always prefer primary public records over secondary commentary.
- When narratives differ across markets (Taiwan vs Sweden/US official sites), highlight the discrepancy.
- For national-capital entities (e.g. 上海市國資委), note the state-owned background.
- Maintain neutral tone. Never call for boycotts.
- If evidence is insufficient, clearly state "證據不足，無法判定" rather than guessing.

## References

- references/channel-data.md — detailed channel ratio table and notes
- references/verification-sources.md — recommended public search targets
