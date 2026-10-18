# Built for Pharos Season of AI

# Wallet Risk Checker

A pre-transaction checker that reviews on-chain signals and explains potential wallet or contract risks before a user interacts.

Video Walkthrough for getting started

## https://youtu.be/f_aUJqjsih4

## Overview

Wallet Risk Checker evaluates a wallet or contract using available on-chain evidence, assigns a low, medium, or high risk level, and explains each detected flag in plain language. It is a decision-support tool, not a guarantee that an address is safe or malicious.

## Signals

The implementation should evaluate at least four signals where the data is available:

- **Contract age:** How long the contract has existed or when it was first observed.
- **Verified source code:** Whether source code is verified by the relevant explorer.
- **Flagged-address interactions:** Known interactions with addresses on a defined risk list.
- **Approval patterns:** Unusual or broad token approvals, where approval data is available.
- **Fresh funding:** Whether a wallet was funded shortly before the current interaction.

A signal should be marked unknown when the data source cannot verify it; missing evidence must not be treated as proof of safety.

## Output

Each assessment should include:

- Checked wallet or contract address.
- Network and assessment timestamp or block, where available.
- Overall risk level: `low`, `medium`, or `high`.
- Individual signals and their status.
- Plain-language reasons for each warning.
- Evidence links, where available.
- Important limitations or unavailable data.

## Example Output

```text
Wallet Risk Assessment
Address: 0x...
Network: Pharos

Risk level: MEDIUM

Signals:
- Contract age: Unknown — deployment information was unavailable.
- Source verification: Flag — source code was not verified by the checked explorer.
- Flagged-address interactions: Clear in the checked data source.
- Approval pattern: Warning — a broad token approval was detected.

Why this matters:
An unverified contract is harder to inspect independently. A broad approval can allow a spender to move eligible tokens up to the approved limit.

This result is an assessment of available evidence, not a guarantee of safety.
```

This example is illustrative, not a real address assessment.

## Setup

Clone the repository:

```bash
git clone <YOUR_REPOSITORY_URL>
cd <REPOSITORY_DIRECTORY>
```

Install dependencies according to the repository's package manager. Configure any RPC, MCP, explorer, or risk-list data sources required by the implementation. Keep credentials out of source control.

Run the application using the command documented by the project.

## Validation

Test at least:

- One clean or low-risk example.
- One risky example with known, explainable flags.
- An address with incomplete data.
- A contract with verified and unverified source-code cases, if supported.
- A case where the tool cannot access a data source.

For each test, record the address, network, expected signal, actual result, and supporting evidence.

## Risk Scoring

Document the actual scoring logic here, including signal weights and thresholds. Do not imply that the score is based on a formal security audit unless it is. Prefer explainable rules and show the specific evidence behind each flag.

## Security and Limitations

- A low-risk result does not guarantee that a transaction is safe.
- A high-risk result should explain the evidence rather than make unsupported accusations.
- Risk lists and explorer data can be incomplete or outdated.
- Token approvals and contract behavior may require additional transaction simulation or security analysis.
- Never ask users to provide seed phrases or private keys.

## Roadmap

- [ ] Add configurable signal weights
- [ ] Improve evidence links
- [ ] Add test fixtures for clean and risky examples
- [ ] Track data-source freshness

## License

Not approved yet !



