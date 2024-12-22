# Testing and QA

This page outlines the testing philosophy, available test commands, coverage analysis, and quality assurance processes for PeoPay-Core. By understanding these steps, contributors and auditors can ensure that changes maintain or improve the reliability and security of the codebase.

### Philosophy

* **Comprehensive Coverage:**\
  Aim to test all critical logic, including ERC-20 functionality, staking calculations, governance proposals, DCS scoring, and conversion operations.
* **Edge Cases & Invariants:**\
  Incorporate scenarios where users stake zero tokens, proposals fail quorum, or DCS weight factors are updated. Property-based testing (e.g., via Echidna) helps ensure invariants hold under random conditions.
* **Continuous Improvement:**\
  As the code evolves, maintain and update tests to cover new features. Avoid regressions by adding tests for previously uncovered branches or lines.

### Running Tests

Use Hardhat’s test runner to execute all tests:

```bash
npx hardhat test
```

* **Location of Tests:**\
  All test files are in the `test/` directory, named after the corresponding contracts (e.g., `peocoin.test.js`, `staking.test.js`).
* **Verbose Output:**\
  Use `npx hardhat test --verbose` for more detailed logs if needed.

When tests pass, you’ll see green checkmarks and a summary of tested scenarios. If any fail, review the error output to identify the cause.

### Test Coverage

Generate a coverage report to measure how thoroughly the tests exercise the code:

```bash
npx hardhat coverage
```

* **Coverage Report:**\
  After running, open `coverage/index.html` in your browser to view a color-coded report.
* **Goals:**\
  Aim for near 100% coverage of statements and functions. If coverage dips, add or update tests to cover missed lines or branches.

### Property-Based Testing (Echidna)

For advanced QA, consider Echidna (if integrated):

* **Echidna Setup:**\
  Place Echidna test contracts in `test/echidna/`.
*   **Run Echidna Tests:**\
    Instructions vary based on your setup, but typically something like:

    ```bash
    echidna-test . --config echidna_config.yaml
    ```
* **Properties & Invariants:**\
  Define invariants that must always hold (e.g., total supply consistency, no unauthorized minting) and let Echidna generate random inputs to confirm these invariants remain unbroken.

### Static Analysis & Linting

Beyond tests, use static analysis tools to catch potential issues early:

* **Slither:**\
  Run `slither .` to detect common vulnerabilities and logic issues.
* **Mythril:**\
  Use `myth analyze` for symbolic execution-based vulnerability detection.
* **Linting and Formatting:**\
  Consider a tool like Prettier or ESLint (for JavaScript) to maintain code style consistency.

### Continuous Integration (CI)

Integrating tests into CI ensures every pull request undergoes automated testing:

* **GitHub Actions:**\
  Set up a workflow to run `npx hardhat test` on every push or PR.
* **Code Quality Gates:**\
  Configure CI to require all tests to pass and coverage thresholds to meet or exceed a set level before merging changes.

### Troubleshooting Test Failures

* **Common Errors:**
  * Reverts due to insufficient approvals or attempts to unstake before lock period ends.
  * Incorrect addresses, missing environment variables, or lack of testnet funds can cause deployment-related issues in integration tests.
* **Debugging Tips:**
  * Add console logs in test files or use `--verbose` mode.
  * Check the Hardhat network logs (`npx hardhat node`) when running against a local node.
  * Review recent commits and PR changes if a previously passing test starts failing.

### Updating & Maintaining Tests

* **After Feature Additions:**\
  Add new tests to cover all new code paths introduced.
* **After Refactoring:**\
  Re-run tests and coverage to ensure no regressions.
* **Code Reviews:**\
  During PR review, check if the contributor added or updated tests for their changes.

### Next Steps

* **Deployment & Configuration:**\
  Once tests pass locally, consider deploying to a testnet. See Deployment & Configuration.
* **Security & Audits:**\
  Combine passing tests with static analysis and future external audits for comprehensive security. See Security & Audits.
