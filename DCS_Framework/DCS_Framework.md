## **Dynamic Contribution Scoring (DCS) Framework**

---

### **1. Overview**
Dynamic Contribution Scoring (DCS) is a core mechanism within the PeoPay ecosystem. It aligns user behavior with ecosystem goals by providing a transparent and dynamic system for rewarding positive contributions and penalizing harmful actions. DCS ensures fairness and sustainability by incentivizing activities like staking, referrals, and governance participation while discouraging spam, fraud, and malicious actions.

---

### **2. Purpose**

#### **2.1 Key Objectives**
1. **Encourage Ecosystem Growth**:
   - Reward users for staking, transactions, governance, and referrals.
2. **Discourage Misuse**:
   - Penalize fraudulent or harmful actions, maintaining ecosystem integrity.
3. **Promote Long-Term Engagement**:
   - Gamified tiers and rewards motivate sustained user activity.
4. **Optimize Resource Allocation**:
   - Adjust rewards dynamically to support growth areas and ecosystem stability.

---

### **3. Scoring Model**

#### **3.1 Formula**
The DCS formula calculates a user’s contribution score based on positive activities and penalties:

$$
\text{DCS}(t) = \alpha \cdot \text{Tx}(t) + \beta \cdot \text{Stake}(t) + \gamma \cdot \text{Gov}(t) + \delta \cdot \text{Referral}(t) - \epsilon \cdot \text{Penalty}(t)
$$

- **$\text{Tx}(t)$**: Volume and frequency of transactions.
- **$\text{Stake}(t)$**: Amount of PeoCoin staked over time.
- **$\text{Gov}(t)$**: Participation in governance, such as voting.
- **$\text{Referral}(t)$**: Successful referrals of new users.
- **$\text{Penalty}(t)$**: Deductions for harmful behavior (e.g., fraud, spam).
- **Weights ($\alpha, \beta, \gamma, \delta, \epsilon$)**: Dynamically adjusted based on ecosystem priorities.

#### **3.2 Properties**
- **Transparency**: Users can track their scores and understand how actions affect rewards.
- **Penalty Dominance**: DCS ensures that penalties outweigh rewards for malicious behavior.
- **Dynamic Adjustments**: Weight parameters evolve to reflect ecosystem needs.

---

### **4. Use Cases**

#### **4.1 Staking Rewards**
- Higher DCS scores result in increased staking yield:
  - **Bronze Tier**: Base staking rewards.
  - **Silver Tier**: +10% bonus.
  - **Gold Tier**: +20% bonus.
  - **Platinum Tier**: +30% bonus.

#### **4.2 Governance Influence**
- Voting power is tied to DCS scores, rewarding active contributors with greater decision-making influence.

#### **4.3 Merchant Incentives**
- Merchants with high DCS scores enjoy:
  - Lower transaction fees.
  - Access to exclusive features, such as premium promotions.

#### **4.4 Referral Bonuses**
- Users earn referral bonuses that scale with their DCS tier, promoting organic ecosystem growth.

#### **4.5 Penalty Enforcement**
- Actions like fraudulent referrals or governance spamming result in score deductions and reduced rewards.

---

### **5. Gamification and Tiers**

DCS introduces a tiered system to gamify engagement and reward high-performing users:

| **DCS Tier**   | **Score Range** | **Benefits**                         |
|----------------|-----------------|---------------------------------------|
| **Bronze**     | 0–499           | Base staking rewards, standard fees. |
| **Silver**     | 500–999         | 10% bonus rewards, 5% fee discounts. |
| **Gold**       | 1000–1999       | 20% bonus rewards, 10% fee discounts.|
| **Platinum**   | 2000+           | 30% bonus rewards, 20% fee discounts.|

---

### **6. Implementation**

#### **6.1 Data Collection**
- On-chain metrics (e.g., transaction volume, staking activity) and verified off-chain data (e.g., user referrals) are aggregated to compute scores.

#### **6.2 Smart Contracts**
- Automated smart contracts execute DCS calculations and reward distributions, ensuring transparency and efficiency.

#### **6.3 Dynamic Adjustments**
- Weight parameters ($\alpha, \beta, \gamma, \delta, \epsilon$) are periodically updated based on ecosystem priorities:
  - Example: Increase referral weight during early adoption phases.

---

### **7. Benefits**

#### **7.1 Fairness and Transparency**
- Users can track contributions and understand how scores affect rewards.

#### **7.2 Ecosystem Alignment**
- Aligns individual incentives with ecosystem goals, driving sustainable growth.

#### **7.3 Fraud Prevention**
- Penalizes harmful behavior, protecting the ecosystem from abuse.

#### **7.4 Gamified Engagement**
- Tiered rewards create a competitive and engaging user experience.

---

### **8. Pilot Testing**

#### **8.1 Objectives**
- Validate DCS’s impact on user engagement and ecosystem metrics.
- Refine weights and scoring tiers based on real-world data.

#### **8.2 Metrics to Track**
1. Staking participation and reward distribution.
2. Growth in user referrals and retention rates.
3. Reduction in harmful behaviors (e.g., spam).
4. Correlation between DCS tiers and governance participation.

#### **8.3 Pilot Regions**
- Kenya, Philippines, and Nigeria, integrated with mobile money systems (e.g., M-Pesa, GCash).

---

### **9. Long-Term Vision**

#### **9.1 Adaptable Scoring**
- Evolve DCS parameters to reflect changing ecosystem dynamics, such as new use cases or governance structures.

#### **9.2 NFT-Based Rewards**
- Introduce NFT badges that represent on-chain credentials tied to user DCS tiers, unlocking additional benefits.

#### **9.3 Integration with DeFi**
- Expand DCS into future DeFi products like lending and borrowing, where scores influence collateral requirements and interest rates.

---

### **10. Conclusion**

Dynamic Contribution Scoring is essential to PeoPay’s vision of a transparent, user-driven financial ecosystem. By aligning individual incentives with collective goals, DCS fosters trust, engagement, and sustainability, ensuring the long-term success of the platform.

---

### **Next Steps**
- [White Paper](../WhitePaper/PeoPay_White_Paper.md): For an overview of PeoPay’s vision and features.
- [Strategic Plan](../Strategic_Plan/Strategic_Plan.md): For implementation and testing details.
- [Tokenomics Model](../Tokenomics_Model/Tokenomics_Model.md): For the role of DCS in token rewards and deflationary mechanisms.

