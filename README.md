# stablecoin-freeze-playbook
How-to guide to freeze stolen stablecoins before they are laundered. One benefit of stablecoins is that they can provide a centralized security overlay on top of otherwise decentralized networks. Organizations should create their own playbook tailored to their specific risk profile and asset holdings to quickly react to asset theft, but this guide should provide a head start. 

## 1. Act Quickly
*Time is critical* as attackers will prioritize swapping of freezable stablecoins into immutable assets and move assets through mixer for anonymity. If funds have been swapped to a decentralized asset such as ETH, a mixer (Tornado Cash), or bridged to a non-native chain, the issuer likely cannot help you. 

## 2. Verify Freezability
*Are my tokens freezable?* The first step is to determine if the token contract enables freezing. If you're unsure, check the table below for some top stablecoins, to determine if they are freeze capable. Many stablecoins implement freeze functionality for regulatory and sanctions compliance. The U.S. [Genius Act](https://www.federalregister.gov/documents/2025/09/19/2025-18226/genius-act-implementation) (signed July 18, 2025) which creates a regulatory framework for stablecoins - while rules are still being finalized - freeze capability for stablecoins is required when ordered by a lawful authority, so if a stablecoin advertises Genius Act compliance they are probably freezable.

- Check the Issuer Terms & Conditions
Freezability is generally stated in policy; for example stablecoins by Paxos (USDG, PYUSD, USDP, PAXG) and Circle (USDC) are freezable as defined in their T&Cs.

- Check the Contract
For example USDC contract, the freeze functionality is evident by reviewing the [contract](https://etherscan.io/token/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48#readProxyContract) source code - I described how that works in [this post](https://medium.com/@j2abro/circle-usdc-blacklist-implementation-8a7bab143a93).

- Check a Stablecoin Registry
This is a relatively new space and I don't know of any defininitive list, but I have included freeze support for some of the top tokens in the table below. Note that decentralized tokens such as DAI and FRAX cannot be frozen.

- Verify "Native" vs "Bridged"
Native tokens minted directly on a particular chain (where freezing is supported) can be frozen. However, bridged tokens that result in a "wrapped" asset cannot be frozen by the stablecoin issuer - if that is possible, that request would have to be taken up with the controller of the bridge, chain or validators which would be more challenging or impossible to freeze. Check the smart contract source to confirm that the token is in fact minted by the issuer, or check that the contract addresses exists in the table below.

## 3. Freeze Request
*Freeze requests will likely require a law enforcement action (LE)*, so reach out to the issuer and also LE in parallel. Note that freezes can take days to implement. Don't expect issuers to necessarily reveal the identity of the attacker.

- Law Enforcement Case
File an official report as issuers such as Circle and Tether typically require a law enforcement case number before initiating any freeze. OFAC sanctions are also generally adhered to.

- Contact the Issuer
Send a formal notice to the issuer's compliance team. 


### 1. Circle (USDC)
- **Policy:** [Circle Legal Terms](https://www.circle.com/en/legal/usdc-terms) and [Access Deny Policy](https://6778953.fs1.hubspotusercontent-na1.net/hubfs/6778953/Blog%20Posts/Circle%20Stablecoin%20Access%20Denial%20Policy_pdf.pdf)
- **Jurisdiction:** United States (Governing law for freezing).
- **Standard:** Generally requires order from recognized U.S. legal authority.
- **Contact Email:** `compliance@circle.com`

- **Support Form:** [Circle help center](https://help.circle.com/s/) and [ticket portal](https://help.circle.com/s/submit-ticket)

### 2. Tether (USDT)
- **Policy:** [Tether LE Policy](https://tether.to/en/legal/?tab=law-enforcement-requests) and [freeze terms](https://tether.to/en/legal/?tab=terms-of-service)
- **Jurisdiction:** British Virgin Islands (Offshore, but they cooperate with U.S. regulatory agencies).
- **Standard:** Generally requires order from recognized legal authority.
- **Contact Email:** `inforequests@tether.to` (Law Enforcement/Legal inbox).
- **Support Form:** [Tether Dispute & Recovery](https://cs.tether.to/)

### 3. Paxos (USDG, PYUSD, USDP, PAXG)
- **Policy Page:** [Paxos Illegal Activity Policy](https://www.paxos.com/terms-and-conditions/illegal-activity)
- **Jurisdiction:** Each token is unique - generally United States (NYDFS Regulated), but some are issued in other jurisdictions.
- **Standard:** Generally requires order from recognized legal authority.
- **Contact Email:** `subpoenas@paxos.com`, `compliance@paxos.com`
- **Support Form:** [Support center](https://support.paxos.com/hc/en-us)

## Forensic Evidence
When submitting your request, do not just send a transaction hash. Provide forensic analysis to speed up their internal review. Be sure to include:

- Attestation of Ownership: Proof that the source wallet belongs to the victim.
- Incident Timeline: Precise UTC timestamps of the hack.
- Flow Visual: A link to a visual trace (e.g., Etherscan, Arkham, or MetaSleuth) showing asset movement.
- Current Location: Explicitly state the location of the stablecoins, including  the chain and address.

## Stablecoin Registry (selected tokens)
Each team should have a reference table such as this for any asset they hold.

| Symbol | Name | Type | Compliance Status | Freeze Capable | Key Native Contracts |
| :--- | :--- | :--- | :--- | :---: | :--- |
| **USDC** | USD Coin | Fiat-Backed | Regulated (NYDFS) | Yes | [Ethereum](https://etherscan.io/token/0xa0b86991c6218b36c1d19d4a2e9eb0ce3606eb48)<br>[Solana](https://solscan.io/token/EPjFWdd5AufqSSqeM2qN1xzybapC8G4wEGGkZwyTDt1v)<br>[Polygon](https://polygonscan.com/token/0x3c499c542cef5e3811e1192ce70d8cc03d5c3359)<br>[Arbitrum](https://arbiscan.io/token/0xaf88d065e77c8cc2239327c5edb3a432268e5831) |
| **USDT** | Tether | Fiat-Backed | Unregulated | Yes | [Ethereum](https://etherscan.io/token/0xdac17f958d2ee523a2206206994597c13d831ec7)<br>[Tron](https://tronscan.org/#/token20/TR7NHqjeKQxGTCi8q8ZY4pL8otSzgjLj6t)<br>[Solana](https://solscan.io/token/Es9vMFrzaC1H6zzggBqqEgakx4eCnmLmJtZNe5yW3sn)<br>[Polygon](https://polygonscan.com/token/0xc2132d05d31c914a87c6611c10748aeb04b58e8f) |
| **DAI** | Dai | Crypto-Backed | Decentralized | No | [Ethereum](https://etherscan.io/token/0x6b175474e89094c44da98b954eedeac495271d0f)<br>[Arbitrum](https://arbiscan.io/token/0xda10009cbd5d07dd0cecc66161fc93d7c9000da1) |
| **PYUSD** | PayPal USD | Fiat-Backed | Regulated (NYDFS) | Yes | [Ethereum](https://etherscan.io/token/0x6c3ea9036406852006290770bedfcaba0e23a0e8)<br>[Solana](https://solscan.io/token/2b1kV6DkPAnxd5ixfnhKpPzZ9GT8Ue266aC2k3p5p16y) |
| **FRAX** | Frax | Algorithmic | Decentralized | No | [Ethereum](https://etherscan.io/token/0x853d955acef822db058eb8505911ed77f175b99e)<br>[Fraxtal](https://fraxscan.com/token/0xFc00000000000000000000000000000000000001) |
| **GHO** | GHO Token | Crypto-Backed | Decentralized | No | [Ethereum](https://etherscan.io/token/0x40d16fc0246ad3160ccc09b8d0d3a2cd28ae6c2f)<br>[Arbitrum](https://arbiscan.io/token/0x7dfF72693f6A4149b17e7C6314655f6a9F7c8B33) |
| **USDe** | Ethena USDe | Synthetic | Decentralized | Yes | [Ethereum](https://etherscan.io/token/0x4c9edd5852cd905f086c759e8383e09bff1e68b3) |
| **TUSD** | TrueUSD | Fiat-Backed | Unregulated | Yes | [Ethereum](https://etherscan.io/token/0x0000000000085d4780b73119b644ae5ecd22b376)<br>[Tron](https://tronscan.org/#/token20/TUpMhErZL2fhh4sVNULAbNKLokS4GjC1F4)<br>[BNB Chain](https://bscscan.com/token/0x40af3827539862d302f9e0df1452a7114261d11c9)<br>[Avalanche](https://snowtrace.io/token/0x1C20E891Bab6b1727d14Da358FAe2984Ed9B59EB) |
| **FDUSD** | First Digital USD | Fiat-Backed | Regulated (HK) | Yes | [Ethereum](https://etherscan.io/token/0xc5f0f7b66764F6ec8C8Dff7BA683102295E16409)<br>[BNB Chain](https://bscscan.com/token/0xc5f0f7b66764F6ec8C8Dff7BA683102295E16409)<br>[Solana](https://solscan.io/token/9zNQRsGLjNKwCUU5Gq5LR8beUCPzQMVMqKAi3SSZh54u)<br>[Sui](https://suiscan.xyz/mainnet/coin/0xe1b972d530263f33947477ce7a36442646c24393273e93a62309725707730766::fdusd::FDUSD) |
| **USDP** | Pax Dollar | Fiat-Backed | Regulated (NYDFS) | Yes | [Ethereum](https://etherscan.io/token/0x8e870d67f660d95d5be530380d0ec0bd388289e1)<br>[Solana](https://solscan.io/token/HVbpJAQGNpkgBaYBZQBR1t7yFdvaYVp2vCQQfKKEN4tM) |


## Reference

### Stablecoin Lists
- [CoinGecko](https://www.coingecko.com/en/categories/stablecoins)
- [CoinMarketCap](https://coinmarketcap.com/view/usd-stablecoin/)
- [Artemis](https://app.artemisanalytics.com/stablecoins)
- [Kraken](https://www.kraken.com/categories/stablecoins)
- [Forbes](https://www.forbes.com/digital-assets/categories/stablecoins/)
- [Visa Stablecoin Analytics](https://visaonchainanalytics.com/)

### Freeze News
- [Tether blog post freeze news](https://tether.io/news/tether-recognized-for-assisting-the-united-states-secret-service-in-23m-freeze-related-to-transfers-on-sanctioned-exchange-garantex/)
- [Paxos freezes FTX related tokens](https://www.paxos.com/blog/paxos-freezes-paxg-tokens-related-to-ftx)
- [Circle freezes Libra scandal wallets on Solana](https://decrypt.co/322558/circle-freezes-58-million-usdc-solana-wallets-libra-scandal)

### Terms and Conditions
- [Paxos Terms & Conditions](https://www.paxos.com/terms-and-conditions/illegal-activity) and [Illegal Activity](https://www.paxos.com/terms-and-conditions/illegal-activity)
- [Circle Stablecoin Access Deny Policy](https://6778953.fs1.hubspotusercontent-na1.net/hubfs/6778953/Circle%20Stablecoin%20Access%20Denial%20Policy_pdf.pdf)
- [Tether freeze terms](https://tether.to/en/legal/?tab=terms-of-service)

### Contact Addresses
- Paxos law enforcement: subpoenas@paxos.com
- Paxos support form: https://support.paxos.com/hc/en-us/requests/new

### Tools
Many tools exist to track and visualize token activity. Here are some examples:
- [MetaSleuth](https://metasleuth.io/)
- [Arkham Intel](https://intel.arkm.com/)


Disclaimer: This playbook is for educational and informational purposes to help promote and support the creation of internal playbooks by crypto teams. It does not constitute legal advice. Always consult with qualified legal counsel for asset recovery operations.