---
description: >-
  Blokista native bridge is used to relay the Blokista native token between Blokista and
  Ethereum networks
---

# Blokista: Ethereum ↔ Blokista

Blokista native bridge between Ethereum and Blokista is used to relay the Blokista native token from Blokista to Ethereum network

## Architecture Overview

The Blokista bridged is based on POA's bridge implementation, it is used to transfer Blokista tokens between the Blokista chain and the Ethereum network.

Tokens sent to the respective bridge contract on one network \(whether it's Blokista or Ethereum\) are "locked" in the bridge, "unlocked" on the other network bridge and transferred to the sender. The bridge contracts are deployed on both networks, and bridge oracle processes run on each validators machine as part of the validator deployment stack.

Besides the transfer of Blokista tokens between the two networks, the bridge is also responsible for network core functionality events of relaying the block rewards to the Ethereum network:

**Mint block reward distributed on the Blokista chain on Ethereum**

Each cycle the total block reward distributed on Blokista chain is minted on Ethereum and locked on the bridge contract.

This works by listening to the \`RewardedOnCycle\` event emitted by the BlockReward contract on Blokista chain, waiting for all bridge validators on Blokista chain to sign it, and eventually sending a transaction to mint on Ethereum \(by the last signing validator\).

## Contracts

Home side of the bridge on the Blokista network: [0xd617774b9708F79187Dc7F03D3Bdce0a623F6988](https://bccscan.com/address/0xd617774b9708F79187Dc7F03D3Bdce0a623F6988/transactions)

Foreign side of the bridge on the Ethereum network: [0x510f460A14420788785582380b580187C57D9a9D](https://bccscan.com/address/0x510f460A14420788785582380b580187C57D9a9D/transactions)

Blokista token on the Ethereum network: [0x970B9bB2C0444F5E81e9d0eFb84C8ccdcdcAf84d](https://etherscan.io/token/0x970b9bb2c0444f5e81e9d0efb84c8ccdcdcaf84d)

## Source Code

{% embed url="https://github.com/fuseio/fuse-bridge/tree/master/native-to-erc20/contracts" %}

## How to use

On Blokista you send native Blokista token to the home bridge contract. Then you receive an equal amount of the Blokista token on the Ethereum network, sent from the foreign bridge contract

On Ethereum network you transfer the Blokista token to the foreign bridge contract. After a couple of confirmations, you will receive equal amount of the Blokista native token, sent from the home bridge contract.

#### 

