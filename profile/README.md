# xchain-mev-research

Open source infrastructure for MEV analysis, cross-chain arbitrage research, and high-resolution DeFi data collection across EVM and Substrate blockchains.

The focus is on data and tooling that go beyond what traditional subgraphs provide — sub-block granularity, cross-chain asset identity, and MEV-relevant metrics.

---

## Projects

### [xchain-dex-indexer](./xchain-dex-indexer)

A TypeScript framework for indexing DEX liquidity pools with sub-block granularity. Built on [Subsquid SDK](https://docs.subsquid.io/), it reconstructs the exact state evolution of pools within each block and exposes it via a unified GraphQL API.

**Key features:**
- Intra-block snapshots ordered by `transactionIndex`
- Priority fee tracking (`baseFee + priorityFee`) for MEV analysis
- Unified schema across Uniswap V2/V3/V4 forks and Substrate XYK pallets
- Cross-chain asset registry (XCM-aware canonical token identity)
- Token whitelist for filtering low-quality or malicious pools
- Data integrity checks against official subgraphs

**Current deployment:** Moonbeam — StellaSwap (V2/V3/V4), Beamswap (V2/V3), Nimbus stDOT vault.

---

## Contributing

Open an issue before large changes. Keep PRs focused. Documentation in English.

---

## License

MIT unless otherwise specified.
