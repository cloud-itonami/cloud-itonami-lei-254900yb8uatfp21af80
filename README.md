# cloud-itonami-lei-254900yb8uatfp21af80

> **Independent third-party archive/analysis. Not affiliated with, endorsed by, or sponsored by SM INVESTMENTS CORPORATION.**

This repository archives the publicly published Privacy Policy of **SM INVESTMENTS CORPORATION** (PH), with source-url and retrieval-date provenance, per
ADR-2607110300 (`cloud-itonami-lei-corporate-tos-catalog`, `com-junkawasaki/root`).
Read-only reference/archive repository — not a governed Advisor/Governor actor.

- LEI: `254900YB8UATFP21AF80` (GLEIF entity status ACTIVE, registration ISSUED)
- Source: https://www.sminvestments.com/privacy-policy/
- Retrieved: 2026-07-25T05:18:38Z
- SHA-256 of archived text: `31cdc7c2fae1474a76f04b458326213766cd64547789447c20cb27d85678ad44`

Acquired by `scripts/lei-acquire.cljs` as part of the worldwide-broadening
continuation that followed the 2026-07-25 coverage audit, which found the
catalog's real reach was 27 countries with the United States at 55%.

## Verified citations (`facts/catalog.edn`)

`facts/catalog.edn` records **65 citations** to public sources that attest facts about
this legal entity. Every row is checked against the live web:

```sh
nbb tools/verify_citations.cljs facts/catalog.edn --min 60
```

Exit codes are three-valued on purpose — *"nothing was checked"* and *"nothing was
wrong"* must not share one:

| exit | meaning |
|------|---------|
| `0`  | answered; every citation fetched and every substring found; floor met |
| `1`  | answered; at least one citation drifted (`DRIFT <id> <why>`) |
| `2`  | **could not answer** — missing/unparseable catalog, zero checks, or fewer rows than `--min` |

### What the row kinds mean, and how they were decided

- `:cite/row-kind :identity` — the claim is **specific to this entity**. If the URL
  pointed at a different company, this row would fail.
- `:cite/row-kind :attribute` — the claim is true of this entity but **generic**. It
  would survive being pointed at a comparable company.

This split was **measured, not asserted**. Every row was re-run against a swapped URL
pointing at **Ayala Corporation** (LEI `254900QJ68UH8GKNGI69`, PSE `cmpy_id=57`) —
chosen because it matches on every generic attribute a swap could ride on: also
Philippine, also registered at RA000483, also `ACTIVE`, also legal form `WHGH`, also
the same managing LOU, also a PSE-listed conglomerate holding company. Only the URL
lines were swapped; the expected substrings still describe SM Investments.

The result: **the set of rows that failed the swap equals the set marked `:identity`,
exactly, for both authorities tested** — 20 of 34 GLEIF rows, 16 of 21 PSE rows, and
no `:attribute` row failed. Two rows were reclassified *because* of the swap:
`gleif-ocid-null` (Ayala carries `"ocid":null` too, so it is generic) and
`gleif-no-direct-parent-reason` (SM files `NON_CONSOLIDATING`, Ayala files
`NATURAL_PERSONS`, so the reason really does discriminate).

Final split: **43 `:identity`, 22 `:attribute`.**

### What is cited, and what is not

Four authorities are cited: **GLEIF**, **ACRA** (Singapore), the **Philippine Stock
Exchange**, and the **issuer** itself.

**The home register is not cited, and this catalog says so.** GLEIF names `RA000483`
— the Companies Register of the Philippine Securities and Exchange Commission — as
both register of record and validation authority, and gives the registration number
as `0000016342`. `www.sec.gov.ph` answers **HTTP 403 behind a Cloudflare
interstitial**, and that was not worked around. The Commission's other surfaces were
measured and none is a register lookup (eFAST is a JavaScript shell behind a login;
eSPARC's search takes an application reference number and covers pending
applications only). **So `0000016342` rests on GLEIF's word alone**, and no row is
written against a Philippine SEC URL.

**A register of record *is* cited — one level down.** GLEIF records a direct child,
`SMIC SG HOLDINGS PTE. LTD.`, with Singapore UEN `202219950R`. Singapore publishes
ACRA's register as open data, it answers a plain GET, and it returns the same name
GLEIF gives — byte for byte — plus an issue date, entity type and registered address
GLEIF does not carry. That is a national register attesting a number GLEIF only
quotes. The catalog is explicit that this covers the child, not the subject.

**GLEIF and the exchange agree on the ISIN.** `PHY806761029` appears in GLEIF's
`/isins` response and in the PSE's own listing page, queried independently. They also
agree on the name, the address, the 15 January 1960 incorporation date, and the
identity of the property subsidiary (`SM Prime Holdings, Inc.`, listed as `SMPH`).

**One contradiction is recorded and not reconciled.** The exchange's company page
states the incorporation date twice and disagrees with itself: its prose says
*"incorporated on January 15, 1960"* (matching GLEIF), while its structured
*Incorporation Date* field on the same page says *May 15, 1960*. Both strings are
kept as rows so neither can be quietly dropped.

Sources that answer but carry nothing usable — the Philippine SEC, SEC eFAST, eSPARC,
the US SEC's EDGAR search, Open Data Philippines, and the PSE's volatile
price/filing figures — are listed under `:catalog/unreachable` with what was measured
and why no row was written. No bot challenge was passed and no User-Agent was spoofed.
