## Unclaimed rewards for KyberSwap Elastic Liquidity Mining

This project shows the unclaimed rewards for KyberSwap Elastic Liquidity Mining across chains, at `2023-04-18 16:00:00 UTC`.

For detail records of unclaimed rewards for each NFT for each chain, please visit [`snapshots`](/snapshots) folder, or click to the following links:
- [Arbitrum](/snapshots/arbitrum.json)
- [Avalanche](/snapshots/avalanche.json)
- [Ethereum](/snapshots/ethereum.json)
- [Optimism](/snapshots/optimism.json)
- [Polygon](/snapshots/polygon.json)

For the total unclaimed rewards for each reward token for each chain, please visit [`group_unclaimed_total.json`](/group_unclaimed_total.json)


## How we get this data

1. We get the snapshot of unclaimed rewards near `2023-04-18 16:00:00 UTC`. For the exact value, we get the snapshot at these block numbers:
    - Arbitrum: `81794760`
    - Avalanche: `28912368`
    - Ethereum: `17074602`
    - Optimism: `91968300`
    - Polygon: `41677128`

2. We use our KyberSwap Elastic Subgraphs, to get all `joinedPositions` at the snapshot block.

    The KyberSwap Elastic Subgraphs we are using:
    - [Arbitrum](https://api.thegraph.com/subgraphs/name/kybernetwork/kyberswap-elastic-arbitrum-one)
    - [Avalanche](https://api.thegraph.com/subgraphs/name/kybernetwork/kyberswap-elastic-avalanche)
    - [Ethereum](https://api.thegraph.com/subgraphs/name/kybernetwork/kyberswap-elastic-mainnet)
    - [Optimism](https://api.thegraph.com/subgraphs/name/kybernetwork/kyberswap-elastic-optimism)
    - [Polygon](https://api.thegraph.com/subgraphs/name/kybernetwork/kyberswap-elastic-matic)

3. For each `joinedPositions` in step 2, we call the function of the farming contract `getUserInfo(nftId, pId)` with `block_identifier=<snapshot_block_number>` to get the pending rewards at the snapshot time.
