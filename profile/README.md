# xchain-mev-research

Open source infrastructure for MEV analysis, cross-chain arbitrage research, and high-resolution DeFi data collection across EVM and Substrate blockchains.

The focus is on data and tooling that go beyond what traditional subgraphs provide — sub-block granularity, cross-chain asset identity, and MEV-relevant metrics.

---

## Projects

### [xchain-dex-indexer](https://github.com/xchain-mev-research/xchain-dex-indexer)

A TypeScript framework for indexing DEX liquidity pools with sub-block granularity. Built on [Subsquid SDK](https://docs.subsquid.io/), it reconstructs the exact state evolution of pools within each block and exposes it via a unified GraphQL API.

**Key features:**
- Intra-block snapshots ordered by `transactionIndex`
- Priority fee tracking (`baseFee + priorityFee`) for MEV analysis
- Unified schema across Uniswap V2/V3/V4 forks and Substrate XYK pallets
- Cross-chain asset registry (XCM-aware canonical token identity)
- Token whitelist for filtering low-quality or malicious pools
- Data integrity checks against official subgraphs

**Current deployment:** Moonbeam — StellaSwap (V2/V3/V4), Beamswap (V2/V3), Nimbus stDOT vault.

### [xchain-mev-simulator](https://github.com/xchain-mev-research/xchain-mev-simulator)

A cross-chain MEV simulator for research and strategy analysis on Polkadot parachains. Given a market state at a specific block, it discovers all profitable circular arbitrage routes across Moonbeam and Hydration, determines the optimal input size per route, plans the flash loans to fund them, and computes full expected value including cross-chain execution risk. Designed to run against indexed historical snapshots from `xchain-dex-indexer`.

**Key features:**
- Multi-hop swap simulation with full tick math (Uniswap V2/V3/V4, Algebra V3/V4, LST vault)
- DFS-based circular route discovery across all pool pairs
- Flash loan planning with lowest-fee-first source selection across V2/V3/V4/Stable pools
- EV model (inclusion probability, bridge reliability, price survival, MEV tax, CVaR95) — structured pseudocode, not yet wired to live data
- Vaadin + React UI for interactive route simulation and Mermaid-rendered arbitrage flow diagrams

**Current deployment:** Moonbeam — StellaSwap (V2/V3/V4), Beamswap (V2/V3), Nimbus stDOT vault. Hydration integration is planned but not yet implemented.

---

## Contributing

Open an issue before large changes. Keep PRs focused. Documentation in English.

[alessiogiannini.dev](https://alessiogiannini.dev)

---

## License

MIT unless otherwise specified.
