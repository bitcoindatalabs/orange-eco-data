# Orange Ecosystem Map

This project processes data from `anvaka/map-of-github-data` to extract, cluster, and map Bitcoin and Bitcoin-adjacent repositories (Core, Lightning, Mining, Nostr, Wallets, DLCs, Ecash, etc.).

## Directory Structure

- `data/raw/`: Raw downloads from `anvaka/map-of-github-data` (ignored by git).
- `data/processed/`: Filtered Bitcoin JSONs, node coordinates, graph edges.
- `scripts/`: Pipeline scripts (e.g., `01_fetch_data.py`, `02_filter_clusters.py`).
- `src/`: Reusable Python modules and utilities.
- `docs/`: Documentation and project context.

## Data Pipeline

1. **Fetch Data**: Raw data is downloaded and stored in `data/raw/`.
2. **Process and Filter**: The data is filtered to identify Bitcoin and Bitcoin-adjacent repositories and saved to `data/processed/`.
3. **Map Generation**: The processed data is used to generate graphs, node coordinates, and edges for the ecosystem map.
