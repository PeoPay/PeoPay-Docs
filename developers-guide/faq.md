# FAQ

This FAQ addresses some of the most common questions about PeoPay-Core, its contracts, configuration, and best practices. If you have a question not covered here, feel free to open a GitHub Issue or ask in our community channels.

### General

**Q: What is PeoPay-Core?**\
**A:** PeoPay-Core is the foundational repository for the PeoPay ecosystem, including the PeoCoin (PEO) token, staking, governance, DCS scoring, and crypto-to-mobile conversion logic.

**Q: Which blockchain networks are supported?**\
**A:** The code is EVM-compatible. It can be deployed on networks like Polygon or Ethereum testnets. Adjust RPC URLs and `.env` settings accordingly. See Deployment & Configuration for details.

**Q: Where can I find more technical information?**\
**A:** Check out the Contracts Overview page for contract logic and [docs.peopay.io](https://docs.peopay.io/) for extensive documentation.

### PeoCoin & ERC-20

**Q: How can I get the PeoCoin (PEO) token?**\
**A:** Initially, PEO is minted to the deployer. You can transfer, mint (owner-only), or burn tokens after deployment. For testing, deploy locally and call `mint()` to allocate tokens.

**Q: Is PeoCoin ERC-20 compliant?**\
**A:** Yes. PeoCoin follows the ERC-20 standard, so any ERC-20 compatible wallet or DeFi tool can interact with it.

### Staking

**Q: How do I stake tokens?**\
**A:** Call `approve()` on PeoCoin to allow the Staking contract to spend your tokens, then call `stake(amount)` on the Staking contract. Once staked, tokens are locked until the lock period ends.

**Q: How are rewards calculated?**\
**A:** Rewards are based on APY, staked duration, and potentially tier multipliers. For details, see Staking.

**Q: Why can’t I unstake immediately?**\
**A:** The contract enforces a lock period. You must wait until this period ends before calling `unstake()`.

### Governance

**Q: How do proposals work?**\
**A:** PEO holders with a nonzero balance can create proposals using `createProposal(description)`. Voting is open for a set period, and voters weight is determined by DCS scores. If quorum and majority thresholds are met, `executeProposal()` finalizes it.

**Q: How can I change governance parameters?**\
**A:** The owner can call `updateParameters()` on the Governance contract to adjust `votingPeriod`, `quorum`, or `majorityPercentage`. See Governance & DCS Parameters.

### DCS (Dynamic Contribution Scoring)

**Q: How is my DCS score computed?**\
**A:** `getScore(user)` considers token balances, staked amounts, and time staked, weighted by `tokenWeight`, `stakeWeight`, and `timeWeight`. The owner can update these weights.

**Q: Why did my DCS score change?**\
**A:** Scores change if you stake/unstake tokens, if your token balance changes, or if the owner updates DCS weights.

### Conversion (Crypto-to-Mobile)

**Q: How do I request a conversion?**\
**A:** Approve the Conversion contract to spend your tokens, then call `requestConversion(amount, mobileNumber, currency)`. The backend service will confirm the conversion off-chain and call `confirmConversion()` once completed.

**Q: Who confirms conversions and why can’t I confirm my own request?**\
**A:** The `backendService` address, authorized by the contract, confirms conversions after verifying off-chain transactions. This ensures a secure and controlled bridging process.

### Troubleshooting & Common Issues

**Q: My transaction reverted with “Transfer failed” or “Insufficient allowance.”**\
**A:** Ensure you’ve approved the contract to spend tokens before calling functions like `stake()` or `requestConversion()`.

**Q: I can’t execute a proposal.**\
**A:** Check if voting has ended, quorum is met, and majority is reached. Also ensure the proposal is not already executed.

**Q: Coverage is low; how do I improve it?**\
**A:** Add more tests targeting uncovered lines or branches. Use `npx hardhat coverage` and review `coverage/index.html` to see which areas need more testing.

### Getting Help

* **Community Channels:**\
  Join our Discord or Telegram groups (links on the main website) to ask questions and share feedback.
* **GitHub Issues:**\
  If you’ve identified a bug or have a feature request, open a GitHub Issue with details.

***

If this FAQ doesn’t address your question, check the other wiki pages, main docs at [docs.peopay.io](https://docs.peopay.io/), or open a new issue for further assistance.
