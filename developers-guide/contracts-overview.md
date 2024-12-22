# Contracts Overview

This page provides a high-level overview of the core contracts in the PeoPay-Core repository. By understanding the purpose and logic behind each contract, you can better integrate, extend, or audit the system.

### PeoCoin (PEO)

**Purpose:**

* The PeoCoin contract implements the PEO ERC-20 token.
* It supports minting, burning, and transferring tokens, with the owner having exclusive rights to mint new tokens.

**Key Features:**

* **Minting & Burning:**
  * `mint(address to, uint256 amount)`: Owner-only function to increase supply.
  * `burn(uint256 amount)`: Users can burn their own tokens to reduce supply.
* **Standard ERC-20 Interface:**\
  Fully compatible with wallets, exchanges, and DeFi protocols that support ERC-20.

**Security & Access Control:**

* Inherits from OpenZeppelin’s `Ownable` for secure access control.
* Owner is set at deployment but can be transferred if needed.

### Staking

**Purpose:**

* Allows users to stake PEO tokens for a specified lock period and earn rewards over time.
* Calculates rewards based on APY (Annual Percentage Yield) and potentially tier multipliers.

**Key Features:**

* **Staking & Unstaking:**
  * `stake(uint256 amount)`: Locks user’s tokens until the lock period ends.
  * `unstake()`: Releases principal + rewards after the lock period.
* **Reward Calculation:**\
  `calculateReward(address user)` determines earned interest based on staked duration, amount, and configured APY.
* **Lock Periods & Tiers:** Ensures users must commit their tokens for a minimum time to earn rewards. Tiers (e.g., Bronze, Silver, Gold) could provide different multipliers if implemented.

### Governance

**Purpose:**

* Empowers PEO holders to create proposals and vote on them.
* Uses Dynamic Contribution Scores (DCS) to weight votes, encouraging meaningful participation over pure token holding.

**Key Features:**

* **Proposal Lifecycle:**
  * `createProposal(string description)`: Anyone holding PEO can propose changes.
  * `vote(uint256 proposalId, bool support)`: PEO holders cast votes weighted by their DCS score.
  * `executeProposal(uint256 proposalId)`: After voting ends, if quorum and majority are met, the proposal is executed.
* **Configurable Parameters:**
  * `votingPeriod`, `quorum`, and `majorityPercentage` can be updated by the owner to adjust governance dynamics.

### DCS (Dynamic Contribution Scoring)

**Purpose:**

* Assigns a contribution score to each user based on their token balances, staking activity, governance participation (or other integrated metrics).
* Influences governance voting power and can affect staking rewards or other benefits.

**Key Features:**

* **Score Calculation:**\
  `getScore(address user)` returns a numeric score factoring in:
  * Token balances (`tokenWeight`)
  * Staked amounts and durations (`stakeWeight`, `timeWeight`)
* **Updatable Weights:**\
  `updateWeights(uint256 tokenWeight, uint256 stakeWeight, uint256 timeWeight)` allows the owner to adjust scoring factors, adapting the system as it evolves.

**Integration Points:**

* Governance contract calls DCS to determine voter weights.
* Future integrations might use DCS for tiered staking rewards or reputation systems.

### Conversion (Crypto-to-Mobile)

**Purpose:**

* Bridges the gap between crypto (PEO) and mobile money systems.
* Allows users to request a conversion of PEO into off-chain mobile money, and a trusted backend service confirms the transaction.

**Key Features:**

* **Request & Confirm:**
  * `requestConversion(uint256 amount, string memory mobileNumber, string memory currency)`: User requests conversion.
  * `confirmConversion(address user, uint256 amount, string memory mobileNumber)`: Backend service authorizes the completed off-chain transfer.
* **Events & Logging:**
  * `ConversionRequested` and `ConversionConfirmed` events facilitate transparency and off-chain automation.

**Security & Authorization:**

* Only the designated `backendService` can confirm conversions, preventing unauthorized confirmations.
* Requires users to approve token transfers to the Conversion contract before requesting conversions.

### Mocks (MockStaking)

**Purpose:**

* Mock contracts, like `MockStaking`, simulate certain behaviors for testing.
* Example: `MockStaking` always returns a positive stake, allowing DCS or Governance tests to run without complex staking setups.

**When to Use Mocks:**

* Simplify integration tests, property-based testing (Echidna), and scenario checks that require controlled contract states.
* Not for production usage—these are test-only contracts.

### Common Patterns & Integrations

* **OpenZeppelin Libraries:**\
  Reuse of well-audited libraries for ERC-20, Ownable, and other patterns ensures security and standardization.
* **Time & Lock Mechanisms:**\
  Staking and Governance rely on block timestamps for voting periods, lock durations, and APY calculations.
* **Role & Access Control:**\
  Owner-only functions (in PeoCoin, Governance, DCS) allow controlled updates to weights, parameters, and supply.

### Next Steps

* **Getting Started:**\
  If you haven’t set up your environment yet, head back to Getting Started.
* **Deployment & Configuration:**\
  Learn how to deploy these contracts to various networks in Deployment & Configuration.
* **Testing & QA:**\
  Dive into test scenarios, coverage, and QA processes in Testing & QA.

***

This overview provides a conceptual map of how each contract fits into the PeoPay ecosystem. For detailed function signatures, events, and logic, refer to the source code and inline comments, or explore the [PeoPay Documentation](https://docs.peopay.io/) for more in-depth technical references.
