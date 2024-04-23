---
layout: post
title: "Campaign to Continue ETH-XMR Atomic Swap Development"
excerpt: "noot is raising funds through the MAGIC Monero Fund to continue ETH-XMR atomic swap development"
date: 2022-08-11
author: magicboard
---

The MAGIC Monero Fund is raising funds for noot to continue development on ETH-XMR atomic swaps. View [the campaign here](https://www.gofundme.com/f/noot-ethxmr-atomic-swap-development-4-months).

### To donate with crypto (and credit/debit with lower fees), [click here](https://magicgrants.budibase.app/app/magic-monero-fund-donations).
 
You can also donate with credit/debit directly on GoFundMe.

This proposal covers 4 months of work focused on the following:

### Relayer support

The current implementation of the protocol requires the ETH-recipient to have some ETH in their claiming account to pay for the transaction fees to claim the swap ETH. However, this is bad for UX and privacy, as users cannot withdraw to fresh ETH accounts.

To allow for users to claim ETH into a fresh account, integration with a relayer service can be implemented. This will allow users to withdraw to a fresh account by paying a small fee to a relayer to submit the transaction on their behalf.

### Ethereum privacy improvements

On the ETH side of the swap, there is no privacy, and which accounts and amounts participating in the swap are visible.

### ERC20 support

To support swaps for ERC20s without hurting liquidity, the swap contract can be integrated with a DEX such as Uniswap to automat-ically swap received ETH for the desired ERC20 token.

### Disk permanence

The current implementation of the swap does not store anything to disk apart from information needed for recovery of swap funds in case of failure. However, there are other components that should be stored to disk and restored upon reload, such as current swap of-fers made, historic swap information, and peer information. This will require a simple key-value database implementation.

### General maintenance and bugfixes

See https://github.com/noot/atomic-swap/issues for open issues on the repo. Issues not covered by the above work are part of this sec-tion. This includes RPC calls and documentation, codebase maintenance, testing, and fixes of any bugs found during testing.

This campaign is being done through the [MAGIC Monero Fund](/funds/monero), and all donations go to it. Should this proposal fail for any reason, donations will support this Fund. 
 
**Your donation is tax-deductible** to the amount allowable by law.
  
MAGIC Grants is a 501(c)(3) nonprofit focused on expanding education and research in cryptocurrencies, and for supporting public, permissionless payment infrastructure.
