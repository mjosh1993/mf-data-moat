# mf-data-moat

Pre-cleaned Indian mutual fund constituent data, keyed by scheme **ISIN**.

Each file `data/{ISIN}.json` holds that fund's latest disclosed portfolio as
`ticker → weight` pairs (weight is a fraction, 0–1), plus optional metadata keys:

```json
{
  "_disclosure_month": "2026-05",
  "_scheme_name": "Motilal Oswal Midcap Fund",
  "PAYTM": 0.0729,
  "COFORGE": 0.0612
}
```

Keys starting with `_` are metadata and are ignored by consumers.

Data is sourced from public monthly portfolio disclosures published by the AMCs
(SBI, Axis, Nippon India, Motilal Oswal, Mirae Asset, LIC MF, and others) and
normalised by `scripts/scrape_portfolio.py` in the companion app.

Consumed over raw HTTPS:
`https://raw.githubusercontent.com/<org>/mf-data-moat/main/data/{ISIN}.json`
