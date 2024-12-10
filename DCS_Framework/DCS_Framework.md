# Dynamic Contribution Scoring (DCS) Framework

## 1. Overview

Dynamic Contribution Scoring (DCS) is a core mechanism within the PeoPay ecosystem. It aligns user behavior with the platform’s goals by providing a transparent, adaptable system that rewards positive contributions and penalizes harmful actions. By incentivizing beneficial activities like staking, referrals, and governance participation—and discouraging spam, fraud, and malicious conduct—DCS ensures fairness, fosters growth, and promotes long-term sustainability.

## 2. Purpose

### 2.1 Key Objectives

1. **Encourage Ecosystem Growth**:  
   Reward users for staking, transacting, participating in governance, and referring new members.
   
2. **Discourage Misuse**:  
   Penalize fraudulent or harmful actions to maintain ecosystem integrity.
   
3. **Promote Long-Term Engagement**:  
   Gamified tiers and rewards inspire sustained user involvement.
   
4. **Optimize Resource Allocation**:  
   Dynamically adjust rewards to support growth priorities and stability.

## 3. Scoring Model

### 3.1 Formula

The DCS formula calculates a user’s contribution score based on weighted positive activities and penalties:

\[
\text{DCS}(t) = \alpha \cdot \text{Tx}(t) + \beta \cdot \text{Stake}(t) + \gamma \cdot \text{Gov}(t) + \delta \cdot \text{Referral}(t) - \epsilon \cdot \text{Penalty}(t)
\]

Where:  
- **Tx(t)**: Transaction volume and frequency  
- **Stake(t)**: Amount of PeoCoin staked over time  
- **Gov(t)**: Governance participation (e.g., voting)  
- **Referral(t)**: Successful user referrals  
- **Penalty(t)**: Deductions for harmful behavior (e.g., fraud, spam)  
- **Weights (α, β, γ, δ, ε)**: Dynamically adjusted based on evolving ecosystem priorities

### 3.2 Properties

- **Transparency**: Users can track their scores and understand how actions affect rewards.
- **Penalty Dominance**: Negative behaviors incur substantial penalties, outweighing potential gains.
- **Dynamic Adjustments**: Weight parameters evolve over time, reflecting current ecosystem goals.

## 4. Use Cases

### 4.1 Staking Rewards

DCS scores determine tier-based staking yields:

- **Bronze Tier**: Base staking rewards  
- **Silver Tier**: +10% bonus  
- **Gold Tier**: +20% bonus  
- **Platinum Tier**: +30% bonus

### 4.2 Governance Influence

Users with higher DCS scores have greater voting power, enhancing their influence in decision-making and policy formation.

### 4.3 Merchant Incentives

Merchants benefit from high DCS scores through:

- Reduced transaction fees  
- Access to premium promotional tools and features

### 4.4 Referral Bonuses

Referral rewards scale with DCS tiers, encouraging users to grow the ecosystem organically.

### 4.5 Penalty Enforcement

Malicious activities like fraudulent referrals or governance spamming result in score deductions, reducing rewards and feature access.

## 5. Gamification and Tiers

DCS employs a tiered system to motivate active participation and higher contributions:

| **DCS Tier** | **Score Range** | **Benefits**                             |
|--------------|-----------------|-------------------------------------------|
| Bronze       | 0–499           | Base staking rewards, standard fees       |
| Silver       | 500–999         | +10% rewards, 5% fee discounts            |
| Gold         | 1000–1999       | +20% rewards, 10% fee discounts           |
| Platinum     | 2000+           | +30% rewards, 20% fee discounts           |

## 6. Implementation

### 6.1 Data Collection

On-chain metrics (e.g., transaction volume, staking activity) and verified off-chain data (e.g., user referrals) feed into DCS calculations.

### 6.2 Smart Contracts

Automated smart contracts ensure transparent, efficient scoring and reward distribution.

### 6.3 Dynamic Adjustments

Weight parameters (α, β, γ, δ, ε) are periodically updated to address ecosystem needs. For example, during early growth phases, the referral weight might increase to incentivize user expansion.

## 7. Benefits

### 7.1 Fairness and Transparency

Users clearly see how their actions impact their DCS and associated rewards.

### 7.2 Ecosystem Alignment

DCS aligns individual incentives with the broader ecosystem’s health and growth.

### 7.3 Fraud Prevention

Penalties deter harmful behaviors, maintaining platform integrity.

### 7.4 Gamified Engagement

Tiered rewards and progression create an engaging, competitive user environment.

## 8. Pilot Testing

### 8.1 Objectives

- Validate DCS’s influence on user engagement and key ecosystem metrics  
- Adjust weights and tiers based on real-world user data

### 8.2 Metrics to Track

1. Staking participation and reward distribution  
2. Growth in user referrals and retention  
3. Reduction in spam and other harmful activities  
4. Correlation between DCS tiers and governance involvement

### 8.3 Pilot Regions

Initial tests to be conducted in Kenya, the Philippines, and Nigeria, integrating with local mobile money systems (e.g., M-Pesa, GCash).

## 9. Long-Term Vision

### 9.1 Adaptable Scoring

DCS parameters will evolve as the ecosystem matures, accommodating new use cases and governance structures.

### 9.2 NFT-Based Rewards

DCS tiers may be represented as NFTs, granting on-chain credentials and unlocking exclusive platform benefits.

### 9.3 Integration with DeFi

Future expansions into DeFi products (e.g., lending, borrowing) could leverage DCS scores for determining collateral requirements and interest rates.

## 10. Conclusion

DCS is integral to PeoPay’s vision of a transparent, user-driven financial ecosystem. By aligning incentives with collective goals, DCS fosters trust, engagement, and sustainable growth—ensuring the platform’s long-term success.

---

### Next Steps

- [White Paper](../WhitePaper/PeoPay_White_Paper.md): Overview of PeoPay’s vision and features  
- [Strategic Plan](../Strategic_Plan/Strategic_Plan.md): Implementation and testing details  
- [Tokenomics Model](../Tokenomics_Model/Tokenomics_Model.md): Understanding DCS’s role in token dynamics

