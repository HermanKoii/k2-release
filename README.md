# K2 Validator Setup Guide for Koii Network

## Project Overview

This repository provides a comprehensive guide and installation scripts for setting up a validator node on the Koii Network's K2 blockchain. The project is designed to help blockchain enthusiasts, developers, and network participants establish and maintain a Koii validator with detailed, step-by-step instructions.

🔗 **Network**: Koii Mainnet
🌐 **Blockchain**: K2 (Koii's Layer 1 Blockchain)

### Key Objectives
- Provide a complete walkthrough for K2 validator setup
- Offer installation scripts for different versions
- Guide users through technical requirements and configuration steps

## Features / Capabilities

- Detailed validator setup instructions
- Scripts for different K2 release versions
- Comprehensive network and system configuration guidance
- Step-by-step validator initialization process
- Instructions for:
  - System preparation
  - Keypair generation
  - Vote account creation
  - Stake delegation
  - Validator configuration

## Technologies Used

- **Operating System**: Ubuntu 22.04 (recommended)
- **Languages/Tools**: 
  - Shell Scripting
  - Koii CLI
- **Blockchain**: Koii K2 Network
- **Key Components**:
  - Systemd
  - UFW (Uncomplicated Firewall)

## System Requirements

### Minimum Hardware Specifications
- **Memory**: 
  - 256GB for consensus validator nodes
  - 512GB for RPC nodes
- **Compute**:
  - 12 cores / 24 threads @ 2.8GHz (consensus validator)
  - 16 cores / 32 threads (RPC nodes)
- **Storage**:
  - PCIe Gen3 x4 NVME SSD
  - Accounts: 500GB high TBW
  - Ledger: 2TB high TBW

### Network Requirements
- 1 Gbps symmetrical uplink/downlink
- Unshaped and unmetered connection

## Getting Started

### Prerequisites
1. Ubuntu 22.04 server
2. Basic Linux administration skills
3. KOII tokens for staking

### Quick Installation
```bash
# Update system
sudo apt update && sudo apt upgrade

# Install Koii CLI
sh -c "$(curl -sSfL https://raw.githubusercontent.com/koii-network/k2-release/master/k2-install-init_v1.16.6.sh)"

# Configure Koii CLI
koii config set --url https://mainnet.koii.network
```

## Usage Examples

### Generate Validator Keypairs
```bash
# On a secure computer
koii-keygen new --outfile ~/validator-keypair.json
koii-keygen new --outfile ~/vote-account-keypair.json
```

### Create Vote Account
```bash
# After funding your validator identity
koii create-vote-account ~/vote-account-keypair.json ~/validator-keypair.json ~/authorized-withdrawer-keypair.json
```

### Stake KOII Tokens
```bash
# Delegate stake to your validator
koii delegate-stake ~/stake-account-keypair.json ~/vote-account-keypair.json
```

## Versioning

This repository includes multiple installation scripts for different K2 releases:
- v1.14.19
- v1.14.20
- v1.14.21
- v1.15.0
- v1.16.0 to v1.16.6

Always use the latest version recommended by the Koii Network.

## Security Considerations

⚠️ **Important Security Notes**:
- Keep validator and withdrawer keypairs secure
- Never share private keys
- Use a separate secure computer for key generation
- Implement proper firewall and network security

## Troubleshooting

- Check systemd service status: `sudo systemctl status koii-validator`
- Verify Koii CLI configuration: `koii config get`
- Review logs at `/home/koii/koii-rpc.log`

## Contributing

Contributions are welcome! Please:
- Report issues on the GitHub repository
- Submit pull requests with improvements
- Follow Koii Network's contribution guidelines

## License

This project is open-source. Please refer to the LICENSE file for detailed information.

## Support

For additional support:
- Koii Network Documentation: [https://docs.koii.network](https://docs.koii.network)
- Community Discord: [Koii Network Discord](https://discord.gg/koii)

---

*Disclaimer: Running a validator involves technical complexity and financial risks. Always do thorough research and understand the responsibilities.*