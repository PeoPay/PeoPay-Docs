# Getting Started

Hey there! Welcome to the PeoPay-Core codebase! This guide is here to help you get your environment up and running, install all the necessary dependencies, and run tests. You'll be ready to contribute, experiment, or integrate with our ecosystem in no time. Happy coding!

### Prerequisites

* **Node.js & npm**:\
  Install the latest LTS version of [Node.js](https://nodejs.org/en/download/) and ensure `npm` is available.
* **Git**:\
  Ensure you have [Git](https://git-scm.com/downloads) installed to clone the repository.
* **Hardhat**:\
  This project uses [Hardhat](https://hardhat.org/) as the development environment for compiling contracts, running tests, and deploying. Hardhat is installed as a dev dependency within the project.
* **A Test Network (Optional)**:\
  If you plan to deploy to a testnet (e.g., Polygon’s Amoy), you’ll need an RPC endpoint and testnet funds for gas. Services like [Alchemy](https://www.alchemy.com/) or [Infura](https://infura.io/) can provide RPC URLs.

### Cloning the Repository

1. **Fork (Optional)**:\
   If you plan to contribute, fork the repository on GitHub before cloning.
2.  **Clone the Repository**:

    ```bash
    git clone https://github.com/PeoPay/PeoPay-Core.git
    cd PeoPay-Core
    ```

### Installing Dependencies

Install all required npm packages:

```bash
npm install
```

This will install Hardhat, OpenZeppelin contracts, and other dependencies specified in `package.json`.

### Environment Variables

Create a `.env` file (based on `.env.example`) to store sensitive info like private keys, RPC URLs, and API keys:

```bash
cp .env.example .env
```

Then open `.env` and fill in:

* `PRIVATE_KEY` for deployment (if needed).
* `INFURA_API_KEY` or `ALCHEMY_KEY` if you deploy to a testnet/mainnet.
* Other variables as needed.

### Compiling Contracts

Compile the Solidity contracts:

```bash
npx hardhat compile
```

If successful, you’ll see a “Compiled successfully” message and generated artifacts in the `artifacts/` directory.

### Running Tests

The test suite ensures the integrity and functionality of the PeoPay-Core contracts. Run:

```bash
npx hardhat test
```

* All tests are located in the `test/` directory.
* If tests pass, you should see green checkmarks and details of each test scenario.

For additional testing guidance, see the Testing & QA page.

### Coverage

To measure test coverage:

```bash
npx hardhat coverage
```

Open the generated coverage report in `coverage/` to review which lines and branches are tested. Aim for high coverage before contributing new features or refactoring code.

### Deployment

To deploy contracts to a local Hardhat network:

```bash
npx hardhat run scripts/deploy_peocoin.js
```

Adjust the script and network:

```bash
npx hardhat run scripts/deploy_peocoin.js --network mumbai
```

For more details on deploying to various networks, consult the Deployment & Configuration page.

### Code Quality and Security

Before submitting changes:

* Review code style and adhere to the project’s formatting and commenting guidelines.
* Run tests and coverage to ensure no regressions.
* Consider running static analysis tools like `slither` for additional checks.

See the [CONTRIBUTING.md](https://github.com/PeoPay/PeoPay-Core/blob/main/CONTRIBUTING.md) file for detailed contribution guidelines.

### Next Steps

* **Contracts Overview:** Dive deeper into the Contracts Overview page to understand each contract’s role and logic.
* **Governance & DCS Parameters:** Learn how to modify governance settings or DCS weights in the Governance & DCS Parameters page.
* **FAQ:** Check the FAQ if you encounter common issues or need clarification on typical scenarios.

***

By following these steps, you’ll have a functional development environment, an understanding of how to test the code, and a foundation to start exploring, contributing, and integrating with the PeoPay ecosystem. If you have any questions or run into issues, open a GitHub Issue or join our community channels for support.
