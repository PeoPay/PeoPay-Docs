# Governance and DCS Parameters

PeoPay-Core’s Governance and DCS (Dynamic Contribution Scoring) systems are designed to be flexible. Authorized parties (such as the owner) can update parameters like voting periods, quorums, APY tiers, and DCS weight factors, allowing the ecosystem to adapt over time.

### Governance Parameters

**Affected Contracts:**

* **Governance.sol:** Manages proposals, voting, execution, and acceptance criteria.

**Key Parameters:**

* **votingPeriod:**\
  The length of time (in seconds) that proposals remain open for voting. Longer voting periods give more participants a chance to vote, but also slow decision-making.
* **quorum:**\
  The minimum total number of weighted votes required for a proposal to be considered valid. Increasing quorum ensures broad participation, but may make proposals harder to pass.
* **majorityPercentage:**\
  The percentage of votes that must be “yes” votes for the proposal to pass. A higher majority threshold ensures stronger consensus but may slow down decision-making.

**Updating Governance Parameters:**

* **Function:** `updateParameters(uint256 _votingPeriod, uint256 _quorum, uint256 _majorityPercentage)`
* **Access Control:** Owner-only function.\
  Ensure the caller is the contract owner or the address authorized to make these changes.

**Considerations:**

* **Impact on Voting Dynamics:**\
  Increasing quorum or majorityPercentage can prevent low-participation proposals from passing easily. Decreasing them can make governance more agile but potentially less stable.
* **Community Consultation:**\
  Consider announcing parameter changes in advance or holding a governance vote to agree on updates, even if the owner has the authority, to maintain community trust.

### DCS Parameters

**Affected Contracts:**

* **DCS.sol:** Calculates user scores based on token holdings, staking amounts/durations, and possibly governance participation.

**Key Parameters:**

* **tokenWeight:**\
  How much the user’s token balance contributes to their DCS score.
* **stakeWeight:**\
  How much the user’s staked amount influences their DCS score.
* **timeWeight:**\
  How much time staked contributes to the DCS calculation (e.g., rewarding longer commitments).

**Updating DCS Parameters:**

* **Function:** `updateWeights(uint256 _tokenWeight, uint256 _stakeWeight, uint256 _timeWeight)`
* **Access Control:** Owner-only function.\
  Ensure that the address calling this function is the owner or authorized to update scoring factors.

**Considerations:**

* **Impact on User Behavior:**\
  Increasing `timeWeight` rewards long-term stakers, while increasing `tokenWeight` places more emphasis on simply holding PEO. Adjust these factors to encourage desired ecosystem behavior.
* **Stability & Predictability:**\
  Frequent changes to DCS weights can confuse participants. Aim for incremental adjustments rather than drastic shifts.

### Best Practices for Parameter Changes

1. **Incremental Adjustments:**\
   Avoid large, sudden changes that could destabilize governance or DCS scoring. Make small tweaks and observe the impact over time.
2. **Transparency & Communication:** Announce proposed parameter changes well in advance through community channels, governance proposals, or documentation updates. Seek feedback from token holders, stakers, and other stakeholders.
3. **Monitor Metrics Post-Change:** After adjusting parameters, monitor governance participation rates, staking behaviors, DCS score distributions, and proposal pass/fail patterns to determine if the changes produced the intended results.
4. **Backup & Rollback Plan:** Have a strategy to revert parameter changes if they negatively impact the ecosystem. Since these are owner-only functions, retaining the authority to restore previous values or more balanced settings is essential.

### Integration Points

* **Governance & DCS Relationship:** DCS scores directly influence voting power in governance. Adjusting DCS weights changes who wields influence. For example, increasing `stakeWeight` might empower long-term stakers in governance decisions.
* **Staking & DCS:** Adjusting `timeWeight` or `stakeWeight` will alter the incentives for users to stake longer or in greater amounts.
* **Conversion & Other Features:** While conversion logic may not be directly affected by these parameters, changes in DCS and governance can indirectly influence user trust, participation, and ecosystem health, which can impact how users engage with conversion features.

### Next Steps

* **Testing & QA:** Before applying parameter changes to a live environment, test them on a local or testnet deployment. See Testing & QA for instructions.
* **Deployment & Configuration:** After deciding on new parameters, refer to Deployment & Configuration to apply changes in a controlled and verified manner.

***

By carefully managing governance and DCS parameters, you can maintain a balanced, fair, and adaptive ecosystem. Transparency, incremental changes, and ongoing monitoring are key to successful parameter management in PeoPay-Core.
