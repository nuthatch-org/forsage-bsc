# forsage-bsc

A [nuthatch](https://github.com/nightswatchhq/nuthatch) nest: **Forsage x2 on BNB Smart Chain**.

Registrations, matrix placements, reinvestments and upgrades.

One binary, one config file, no graph-node, no gateway, no query fees.

## What it indexes

**Chain:** `bsc`. **1 contract**, **6 tables**.

| alias | address |
|---|---|
| `forsage` | `0x5acc84a3e955bdd76467d3348077d003f00ffb97` |

## Verified

Indexed blocks **117,363,360 to 117,463,358** and sealed **575 events**. Every table below is generated from the vendored ABIs, and the run above is what this nest actually decoded, not an estimate.

## Read this before trusting it

- A third distinct proxy pattern: no EIP-1967 slot, `implementation()` reverts, and the implementation hides behind a bespoke `impl()` getter. Resolved directly the proxy gives seven ABI entries and **no events at all**.

## Run it

```sh
nuthatch init --from https://github.com/nightswatchhq/forsage-bsc
cd forsage-bsc
nuthatch dev --dir . --backfill 50000 --seal-direct
nuthatch sql --dir . "SELECT count(*) FROM \"forsage__missed_eth_receive\""
```

The endpoint in `nuthatch.toml` is keyless and public, so this file is publishable: a `nuthatch.toml` is pinned into the nest's content address and must never carry a credential. It is enough to follow the tip. A **backfill** wants archive depth it may not have: pass your own with `--rpc`, and check it first with `nuthatch doctor --rpc <url>`.

## Tables

```
forsage__missed_eth_receive
forsage__new_user_place
forsage__registration
forsage__reinvest
forsage__sent_extra_eth_dividends
forsage__upgrade
```
