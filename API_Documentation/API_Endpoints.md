# **API Documentation**

This documentation provides a comprehensive guide to PeoPay’s APIs, enabling developers to integrate with the PeoPay ecosystem. The APIs allow seamless access to core features such as user management, P2P payments, staking, governance, and Dynamic Contribution Scoring (DCS).

---

## **1. Overview**

PeoPay APIs enable developers to:
- Authenticate users and manage accounts.
- Initiate and track transactions, including crypto-to-mobile money conversions.
- Access staking, rewards, and referral systems.
- Participate in governance through voting and proposal submission.
- Monitor user contributions and penalties via DCS.

### **Base URL**
- **Production Environment**: `https://api.peopay.com/v1`
- **Sandbox Environment**: `https://sandbox.api.peopay.com/v1`

---

## **2. Authentication**

### **Endpoint: Login**
Authenticate users and retrieve a session token for subsequent API requests.

- **Method**: `POST`
- **URL**: `/auth/login`

#### **Request**
```json
{
  "username": "user@example.com",
  "password": "securePassword123"
}
```

#### **Response**
```json
{
  "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9...",
  "expires_in": 3600
}
```

---

### **Endpoint: Register**
Create a new user account.

- **Method**: `POST`
- **URL**: `/auth/register`

#### **Request**
```json
{
  "username": "user@example.com",
  "password": "securePassword123",
  "mobile_number": "+1234567890"
}
```

#### **Response**
```json
{
  "message": "User registered successfully. Please verify your email."
}
```

---

## **3. User Management**

### **Endpoint: Get User Profile**
Retrieve user details, including DCS score and staking status.

- **Method**: `GET`
- **URL**: `/user/profile`
- **Headers**: `Authorization: Bearer <token>`

#### **Response**
```json
{
  "username": "user@example.com",
  "mobile_number": "+1234567890",
  "dcs_score": 1250,
  "staking_balance": 500,
  "referrals": 10
}
```

---

## **4. Transactions**

### **Endpoint: Send P2P Payment**
Send a peer-to-peer payment using PeoCoin.

- **Method**: `POST`
- **URL**: `/transactions/p2p`

#### **Request**
```json
{
  "recipient": "recipient@example.com",
  "amount": 50,
  "message": "Payment for services"
}
```

#### **Response**
```json
{
  "transaction_id": "abc123",
  "status": "success",
  "timestamp": "2024-01-01T12:00:00Z"
}
```

---

### **Endpoint: Crypto-to-Mobile Conversion**
Convert crypto to mobile money.

- **Method**: `POST`
- **URL**: `/transactions/convert`

#### **Request**
```json
{
  "amount": 100,
  "currency": "PEO",
  "mobile_number": "+1234567890"
}
```

#### **Response**
```json
{
  "conversion_id": "conv123",
  "status": "processing",
  "mobile_money_balance": 1000,
  "exchange_rate": 1.2
}
```

---

## **5. Staking**

### **Endpoint: Stake PeoCoin**
Stake PeoCoin to earn rewards.

- **Method**: `POST`
- **URL**: `/staking/stake`

#### **Request**
```json
{
  "amount": 200
}
```

#### **Response**
```json
{
  "staking_id": "stake123",
  "status": "success",
  "message": "You have successfully staked 200 PEO."
}
```

---

### **Endpoint: Get Staking Rewards**
Retrieve current staking rewards.

- **Method**: `GET`
- **URL**: `/staking/rewards`
- **Headers**: `Authorization: Bearer <token>`

#### **Response**
```json
{
  "total_rewards": 50,
  "next_payout": "2024-01-15T00:00:00Z"
}
```

---

## **6. Governance**

### **Endpoint: Submit Proposal**
Submit a governance proposal.

- **Method**: `POST`
- **URL**: `/governance/proposals`

#### **Request**
```json
{
  "title": "Proposal to Increase Staking Yields",
  "description": "This proposal suggests increasing staking yields by 5% to encourage participation.",
  "category": "Staking",
  "attachments": []
}
```

#### **Response**
```json
{
  "proposal_id": "prop123",
  "status": "submitted",
  "message": "Your proposal has been submitted for review."
}
```

---

### **Endpoint: Vote on Proposal**
Cast a vote on an active proposal.

- **Method**: `POST`
- **URL**: `/governance/vote`

#### **Request**
```json
{
  "proposal_id": "prop123",
  "vote": "yes"
}
```

#### **Response**
```json
{
  "status": "success",
  "message": "Your vote has been recorded."
}
```

---

## **7. Dynamic Contribution Scoring (DCS)**

### **Endpoint: Get DCS Score**
Retrieve the user’s DCS score.

- **Method**: `GET`
- **URL**: `/dcs/score`
- **Headers**: `Authorization: Bearer <token>`

#### **Response**
```json
{
  "dcs_score": 1350,
  "breakdown": {
    "transactions": 600,
    "staking": 500,
    "governance": 200,
    "referrals": 50,
    "penalties": -50
  }
}
```

---

## **8. Error Codes**

### **Common Errors**
| **Error Code** | **Message**                          | **Description**                              |
|----------------|--------------------------------------|----------------------------------------------|
| 400            | `Bad Request`                       | Invalid or malformed request data.           |
| 401            | `Unauthorized`                      | Missing or invalid authentication token.     |
| 403            | `Forbidden`                         | Insufficient permissions.                    |
| 404            | `Not Found`                         | Requested resource does not exist.           |
| 500            | `Internal Server Error`             | An unexpected error occurred.                |

---

## **9. Rate Limits**
- **Free Tier**: 100 requests per minute.
- **Pro Tier**: 500 requests per minute.

### **Headers**
- Rate limit status is returned in the headers:
  ```text
  X-RateLimit-Limit: 100
  X-RateLimit-Remaining: 80
  X-RateLimit-Reset: 1683721200
  ```

---

## **10. Examples**

### **Send a Payment (cURL)**
```bash
curl -X POST https://api.peopay.com/v1/transactions/p2p \
-H "Authorization: Bearer <token>" \
-H "Content-Type: application/json" \
-d '{
  "recipient": "recipient@example.com",
  "amount": 50,
  "message": "Payment for services"
}'
```

---

### **Next Steps**
1. Test API endpoints in the sandbox environment.
2. Follow our [Developer Guide](../Developer_Guide/Getting_Started.md) for integration tutorials.
3. Join our community forum for support.

