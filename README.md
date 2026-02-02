Solana Anchor Programs Repository

A comprehensive collection of Solana smart contracts built with the Anchor framework. This repository serves as a learning resource and reference implementation for on-chain program development on Solana.

## Overview

This repository contains various Anchor programs ranging from beginner-friendly examples to advanced implementations. Each program is thoroughly documented with best practices, test suites, and deployment scripts.

## Prerequisites

Before you begin, ensure you have the following installed:

- **Rust** (latest stable version)
  ```bash
  curl --proto '=https' --tlsv1.2 -sSf https://sh.rustup.rs | sh
  ```

- **Solana CLI** (v1.18.0 or later)
  ```bash
  sh -c "$(curl -sSfL https://release.solana.com/stable/install)"
  ```

- **Anchor CLI** (v0.30.0 or later)
  ```bash
  cargo install --git https://github.com/coral-xyz/anchor avm --locked --force
  avm install latest
  avm use latest
  ```

- **Node.js** (v18 or later) and **Yarn**
  ```bash
  npm install -g yarn
  ```

## Repository Structure

```
.
├── programs/                 # Anchor program source code
│   ├── examples/            # Basic example programs
│   ├── intermediate/        # Intermediate level programs
│   └── advanced/            # Advanced implementations
├── tests/                   # Integration and unit tests
├── app/                     # Frontend integration examples
├── scripts/                 # Deployment and utility scripts
├── docs/                    # Additional documentation
└── target/                  # Build artifacts (gitignored)
```

## Getting Started

### 1. Clone the Repository

```bash
git clone <your-repo-url>
cd <repo-name>
```

### 2. Install Dependencies

```bash
yarn install
```

### 3. Configure Solana CLI

Set your Solana CLI to the desired network:

```bash
# For local development
solana config set --url localhost

# For devnet
solana config set --url devnet

# For mainnet-beta
solana config set --url mainnet-beta
```

Generate a new wallet (if needed):

```bash
solana-keygen new --outfile ~/.config/solana/id.json
```

### 4. Start Local Validator (for local testing)

```bash
solana-test-validator
```

### 5. Build Programs

```bash
anchor build
```

### 6. Run Tests

```bash
anchor test
```

## Program Categories

### Examples
Basic programs demonstrating fundamental Anchor concepts:
- **Hello World** - Basic program initialization and instructions
- **Counter** - State management and account initialization
- **Token Management** - Working with SPL tokens
- **PDA Examples** - Program Derived Addresses usage

### Intermediate
More complex implementations:
- **Escrow** - Peer-to-peer trading with SPL tokens
- **Voting System** - On-chain governance mechanisms
- **NFT Minting** - Creating and managing NFTs
- **Staking** - Token staking and rewards distribution

### Advanced
Production-ready patterns:
- **AMM (Automated Market Maker)** - Decentralized exchange mechanics
- **Lending Protocol** - Collateralized lending and borrowing
- **DAO Framework** - Complete decentralized organization structure
- **Oracle Integration** - External data feeds integration

## Development Workflow

### Creating a New Program

```bash
anchor init <program-name>
cd <program-name>
anchor build
anchor test
```

### Deploying to Devnet

```bash
# Ensure you have devnet SOL
solana airdrop 2 --url devnet

# Build and deploy
anchor build
anchor deploy --provider.cluster devnet
```

### Running Specific Tests

```bash
# Run all tests
anchor test

# Run tests for a specific program
anchor test --skip-local-validator -- --test-program <program-name>

# Run with detailed logs
RUST_LOG=debug anchor test
```

## Best Practices

### Code Organization
- Keep instruction handlers focused and single-purpose
- Use separate modules for different functionalities
- Implement proper error handling with custom errors
- Document all public functions and account structures

### Security Considerations
- Always validate account ownership and signers
- Implement proper access control checks
- Use account constraints to prevent unauthorized access
- Be mindful of arithmetic overflow/underflow
- Validate all user inputs

### Testing
- Write comprehensive unit tests for all instructions
- Include integration tests for multi-step workflows
- Test edge cases and error conditions
- Use fixtures for consistent test data

### Gas Optimization
- Minimize account data size where possible
- Use zero-copy deserialization for large accounts
- Batch operations when feasible
- Consider compute unit limits

## Common Commands

```bash
# Build all programs
anchor build

# Test all programs
anchor test

# Deploy to devnet
anchor deploy --provider.cluster devnet

# Get program ID
anchor keys list

# Clean build artifacts
anchor clean

# Upgrade a deployed program
anchor upgrade <program-id> --program-name <program-name>
```

## Environment Variables

Create a `.env` file in the root directory:

```env
ANCHOR_PROVIDER_URL=https://api.devnet.solana.com
ANCHOR_WALLET=~/.config/solana/id.json
PROGRAM_ID=<your-program-id>
```

## Debugging

### View Program Logs

```bash
solana logs <program-id>
```

### Check Account Data

```bash
solana account <account-address>
```

### Verify Program Deployment

```bash
solana program show <program-id>
```

## Resources

### Official Documentation
- [Solana Documentation](https://docs.solana.com/)
- [Anchor Framework Documentation](https://www.anchor-lang.com/)
- [Solana Cookbook](https://solanacookbook.com/)
- [Solana Program Library](https://spl.solana.com/)

### Community
- [Solana Stack Exchange](https://solana.stackexchange.com/)
- [Anchor Discord](https://discord.gg/anchor)
- [Solana Discord](https://discord.gg/solana)

### Learning Resources
- [Solana Bootcamp](https://www.soldev.app/)
- [Anchor by Example](https://examples.anchor-lang.com/)
- [Solana Bytes](https://www.youtube.com/@SolanaBytes)

## Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Code Standards
- Follow Rust naming conventions
- Run `cargo fmt` before committing
- Ensure all tests pass
- Add tests for new features
- Update documentation as needed

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments

- Solana Foundation for the amazing blockchain platform
- Coral (Backpack) team for the Anchor framework
- The Solana developer community

**Disclaimer**: This repository is for educational purposes. Always conduct thorough security audits before deploying to mainnet.
