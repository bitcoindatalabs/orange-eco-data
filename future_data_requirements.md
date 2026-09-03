# Future Data Requirements for Orange Eco Data

This document tracks gaps and improvement opportunities identified during the integration
of project-level data across the orange-* ecosystem.

Last Updated: 2026-09-02

---

## 1. Taxonomy Repos Not in Eco-Data Pipeline

These repositories are listed in `project_taxonomy.json` but are NOT currently tracked
in the eco-data BigQuery pipeline. They need to be added to `GOLD_STANDARD_REPOS` or
`TARGET_GITHUB_ORGS` in `src/config.py` for the next pipeline run.

| Repo | Project | Action Needed |
|---|---|---|
| `bitcoindevkit/bdk-rn` | Bitcoin Dev Kit | Add to `GOLD_STANDARD_REPOS` |
| `bitcoinfuzz/bitcoinfuzz` | bitcoinfuzz | Add to `GOLD_STANDARD_REPOS` |
| `coracle-social/coracle` | Coracle | Add to `GOLD_STANDARD_REPOS` |
| `fiatjaf/nak` | nak | Add to `GOLD_STANDARD_REPOS` |
| `grapheneos/os-issue-tracker` | GrapheneOS | Add to `TARGET_GITHUB_ORGS` (grapheneos) |
| `hsjoberg/blixt-wallet` | Blixt Wallet | Add to `GOLD_STANDARD_REPOS` |
| `minibits-cash/minibits_wallet` | Minibits | Add to `GOLD_STANDARD_REPOS` |
| `mostrop2p/mostro` | Mostro | Add to `GOLD_STANDARD_REPOS` |
| `skot/bitaxe` | Bitaxe | Add to `GOLD_STANDARD_REPOS` |
| `torproject/tor` | The Tor Project | Add to `GOLD_STANDARD_REPOS` |
| `utreexo/utreexod` | utreexod | Add org `utreexo` to `TARGET_GITHUB_ORGS` |
| `validating-lightning-signer/vls` | Validating Lightning Signer | Add to `GOLD_STANDARD_REPOS` |
| `vinteumorg/floresta` | Floresta | Add org `vinteumorg` to `TARGET_GITHUB_ORGS` |
| `vitorpamplona/amethyst` | Amethyst | Add to `GOLD_STANDARD_REPOS` |
| `wireguard/wireguard-linux` | WireGuard | Add to `GOLD_STANDARD_REPOS` |

**Impact:** After adding these, the next pipeline run will ingest their activity data
and `project_profiles.json` will automatically include richer metrics for these projects.

---

## 2. Funded Projects with No Identified Repositories

These projects exist in funding data (`orange-funding-data/data/raw/`) and have entries
in `project_taxonomy.json`, but we haven't identified their GitHub repositories yet.
If repositories are found, add them to the taxonomy.

| Project | Layer | Notes |
|---|---|---|
| 0xchat | Nostr & Social | Likely `0xchat-app/0xchat` or similar; need to verify |
| ASmap | Core & Protocol | Likely `sipa/asmap`; need to verify |
| Amber | Nostr & Social | Likely `greenart7c3/Amber`; need to verify |
| Applesauce | Nostr & Social | Needs research |
| Bitcoin Ecosystem | Ecosystem Tooling | Catch-all category; no specific repos |
| Bitcoin Research Kit | Developer Education | Needs research |
| Bitshala | Developer Education | Likely has a GitHub org; need to verify |
| Blitz Wallet | Wallets & UX | Needs research |
| ContextVM | Sidechains & L2s | Needs research |
| Cove | Wallets & UX | Likely `bitcoinppl/cove`; need to verify |
| Dana Wallet | Wallets & UX | Needs research |
| Frostr | Nostr & Social | Likely a FROST signing project; need to verify |
| Jumble | Unknown | Needs research |
| OpenCash | Ecash & Privacy | Needs research |
| Routstr | Nostr & Social | Needs research |
| Satoshi Nakamoto Institute | Developer Education | Likely `NakamotoInstitute/nakamotoinstitute.org` |
| Soapbox | Nostr & Social | Likely `soapbox-pub/soapbox`; need to verify |
| Splicing | Lightning Network | Protocol work, may not have a dedicated repo |
| Stable Channels | Lightning Network | Needs research |
| Summer of Bitcoin | Developer Education | Education program; may not have a public codebase |
| Zapstore | Nostr & Social | Likely `zapstore/zapstore`; need to verify |
| ngit | Nostr & Social | Needs research |

**Priority:** Focus on projects with active funding first (check `sponsors_merged.json`
for currently active grants).

---

## 3. Significant GitHub Orgs Not in Taxonomy

These orgs have multiple repos tracked in eco-data but no corresponding project entry
in the taxonomy. Consider adding project entries for the most significant ones.

| Org | Repos in Eco-Data | Likely Project |
|---|---|---|
| `stacks-archive` | 24 | Stacks (historical/archived repos) |
| `blockchain` | 6 | Blockchain.com explorer/wallet |
| `bitpay` | 9 | BitPay payment processor |
| `chaintope` | (in TARGET_GITHUB_ORGS) | Chaintope |

---

## 4. Layer Taxonomy Alignment

The layers used in `project_taxonomy.json` should align with the layers defined in
`repo_categories.json`. Current layer taxonomy:

- Core & Protocol
- Lightning Network
- Ecash & Privacy (note: `repo_categories.json` uses "Ecash / Privacy")
- Nostr & Social (note: `repo_categories.json` uses "Nostr Social")
- Metaprotocols
- Mining Infrastructure
- Ecosystem Tooling
- Wallets & UX (not a layer in `repo_categories.json`)
- Hardware & Signers (not a layer in `repo_categories.json`)
- Libraries & SDKs (not a layer in `repo_categories.json`)
- Developer Education (not a layer in `repo_categories.json`)
- Payments & Commerce (not a layer in `repo_categories.json`)
- Sidechains & L2s (not a layer in `repo_categories.json`)
- Data & Indexers (not a layer in `repo_categories.json`)

**Decision needed:** Should `project_taxonomy.json` layers strictly match
`repo_categories.json` layers, or is it fine to use a richer set? The current approach
uses a richer set since projects have more nuanced categorization needs than individual repos.
