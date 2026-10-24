# Orange Eco Data

This repository is the heavy-lifting data engine behind the [Orange Ecosystem Map](https://github.com/bitcoindatalabs/orange-ecosystem-map). 

We have processed gigabytes of historical open-source developer activity dating back to **2020** to extract, map, and analyze the Bitcoin and Bitcoin-adjacent developer ecosystem.

## 📊 The Data Pipeline

Analyzing the entire open-source world to isolate the Bitcoin ecosystem is a massive undertaking. Our data pipeline handles the extraction, cleaning, and complex relationship mapping required to build the force-directed graph. 

Because of the sheer volume of data, **this repository is designed to only publish the final results to GitHub**.

- **Gigabytes of Activity:** We ingest and process massive amounts of raw repository data, contributor networks, and commit history.
- **The `output/` Folder:** All of the intermediate and raw data is safely ignored locally. The only data pushed to GitHub lives in the `output/` folder, which contains the highly optimized, final JSON artifacts (like `graph_export.json`) that feed the frontend visualization.

## 🧠 Clustering & Segmentation

The Bitcoin ecosystem isn't a monolith. A key feature of this data engine is its ability to contextually cluster repositories into specific sub-domains. 

We use a combination of semantic tagging and "Gold Standard Anchor Repositories" to segment the ecosystem into actionable categories:
- **Core Protocol** (e.g., Bitcoin Core, libbitcoin)
- **Lightning Network** (e.g., LND, Core Lightning, Eclair)
- **Wallets & UI** (e.g., Sparrow, BlueWallet, Electrum)
- **L2s, Sidechains & Ecash** (e.g., Fedimint, Cashu, Liquid, RSK, Stacks)
- **Infrastructure & Mining** (e.g., Stratum, Braiins)
- **Metaprotocols & Adjacent Tech** (e.g., Ordinals, Nostr)

By identifying these clusters and analyzing shared contributors, we can map how talent flows across the different sectors of the Bitcoin economy.

---

## 💻 Repository Structure

- `output/`: The final, public JSON data artifacts consumed by the visualization frontend.
- `src/` & `scripts/`: The Python data pipeline code.
- `data/`: Local storage for gigabytes of raw and curated data (Ignored by Git).
- `scratch/`: Local ad-hoc queries and messy scripts (Ignored by Git).

---

## License

Data: [CC BY 4.0](LICENSE). Free to use, including commercially, with credit: "Source: Bitcoin Data Labs
(bitcoindatalabs.org)". Text written by others (repository descriptions, profile fields) belongs to its authors.
