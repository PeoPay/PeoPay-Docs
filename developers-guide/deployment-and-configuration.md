# Deployment and Configuration

This page explains how to configure your environment for deploying PeoPay-Core contracts to different networks (local, testnet, mainnet) and how to run deployment scripts. By following these steps, you can quickly set up your environment and deploy the PeoPay ecosystem’s core components (PeoCoin, Staking, Governance, DCS, and Conversion).

### Prerequisites

* **Node.js & npm:** Installed and set up (see Getting Started).
* **Hardhat:** Already installed via `npm install`.
* **`.env` file:** Contains RPC URLs, private keys, and API keys.
* **Test Network Funds:** If deploying to a testnet (e.g., Polygon’s Mumbai), ensure you have test MATIC in your deployer account.

### Environment Variables

Your `.env` file provides the sensitive credentials and configuration needed for deployments. For example:

```bash
PRIVATE_KEY=0xyourprivatekeyhere
INFURA_API_KEY=your_infura_project_id
ALCHEMY_KEY=your_alchemy_api_key
```

If deploying to Polygon or Mumbai:

```bash
RPC_URL_MUMBAI=https://polygon-amoy.infura.io/v3/${INFURA_API_KEY}
```

Adjust these variables based on the provider and network you choose.

### Hardhat Configuration

Check `hardhat.config.js` to see predefined network settings. For example:

```javascript
networks: {
  hardhat: {
    // Local network for testing and development
  },
  mumbai: {
    url: process.env.RPC_URL_MUMBAI,
    accounts: [process.env.PRIVATE_KEY]
  },
  polygon: {
    url: "https://polygon-mainnet.infura.io/v3/" + process.env.INFURA_API_KEY,
    accounts: [process.env.PRIVATE_KEY]
  }
}
```

Customize these entries for the networks you want to target. Make sure `process.env.PRIVATE_KEY` and relevant RPC URLs are properly set in `.env`.

### Local Deployment

To deploy contracts to the local Hardhat network (e.g., for testing):

1.  Start a local node (optional):

    ```bash
    npx hardhat node
    ```
2.  Deploy contracts:

    ```bash
    npx hardhat run scripts/deploy_peocoin.js
    ```

By default, running without `--network` uses the `hardhat` network. This is ideal for quick testing and development.

### Testnet Deployment (e.g., Mumbai)

To deploy to Polygon’s Amoy testnet:

1. Ensure `.env` includes `RPC_URL_AMOY` and `PRIVATE_KEY`.
2.  Run:

    ```bash
    npx hardhat run scripts/deploy_peocoin.js --network amoy
    ```

Repeat for other scripts (like `deploy_staking.js`, `deploy_governance.js`) as needed. Once deployed, you can verify contracts on Polygonscan if desired.

### Mainnet Deployment (Polygon)

For production deployments:

1. Ensure you have a funded deployer account with MATIC on Polygon mainnet.
2. Set `INFURA_API_KEY` or `ALCHEMY_KEY` for a Polygon mainnet RPC URL.
3.  Run:

    ```bash
    npx hardhat run scripts/deploy_peocoin.js --network polygon
    ```

Use caution when deploying to mainnet. Double-check addresses, contracts, and parameters before execution.

### Verifying Contracts

After deployment, you can verify contracts on Polygonscan (or Etherscan if using Ethereum):

```bash
npx hardhat verify --network amoy <contract_address> <constructor_args...>
```

This step requires `ETHERSCAN_API_KEY` or `POLYGONSCAN_API_KEY` in `.env`. The verification helps third parties inspect source code and builds trust in your contracts.

### Common Issues & Tips

* **Insufficient Gas / Funds:**\
  Make sure the deployer account has enough test or mainnet tokens (e.g., MATIC) to cover gas costs.
* **Incorrect RPC URLs:**\
  If deployments fail, verify that the RPC endpoints in `.env` and `hardhat.config.js` are correct and active.
* **Contract Dependencies:**\
  Some scripts assume prior deployment of certain contracts. Deploy them in logical order (e.g., PeoCoin first, then Staking, then Governance).
* **Wait for Confirmations:**\
  On testnets or mainnet, consider waiting for multiple confirmations or verifying block explorers to ensure contracts are properly deployed.

### Next Steps

* **Interacting with Deployed Contracts:**\
  See Contracts Overview and Interacting with Contracts (if available) for guidance.
* **Testing & QA:**\
  Re-run tests against a locally deployed environment to ensure no regressions.
* **Governance & DCS Parameters:**\
  After deployment, consider updating governance parameters or DCS weights if needed. See Governance & DCS Parameters.

***

By following these guidelines, you can seamlessly configure your environment and deploy PeoPay-Core contracts to various networks. Always review your setup and scripts before deploying to mainnet to maintain security and stability in the PeoPay ecosystem.
