# Confidex – Confidential Trading, Uncompromised Privacy

**Confidex** is a fully confidential, MEV-resistant decentralized exchange that integrates secure computing, confidential ERC20, and blockchain-based attestation logic to deliver a seamless and private trading experience. Built using Inco’s Fully Homomorphic Encryption (FHE) stack and deployed on Base Sepolia, Confidex enables fair and tamper-proof swaps without revealing user balances or trading intents.

We have 3 submodules:

- `confidex-contract`: Smart contracts using Inco FHE on Base Sepolia.
- `confidex-next`: Frontend built with Next.js, Wagmi, and integrated with @inco/js.
- `confidex-tee`: NestJS-based backend running inside a Marlin Trusted Execution Environment (TEE).

## 🔑 Key Features

- 🫣 Confidential Trading - Supported by Inco's FHE capabalities
- 🕵️‍♂️ Confidential ERC20 Support – Encrypted tokens using @inco/lightning standard.
- 🔐 End-to-End Encrypted Intents – All trades are FHE-encrypted before submission.
- 🛡️ No MEV or Frontrunning – Mempool obfuscation via encrypted off-chain intent matching.
- ⚡ Low On-chain Footprint – Merkle trees compress state updates.

## 🛠️ How Confidex Is Built

Confidex extends SoloPatty by introducing confidential token support and encrypted matching logic for fully private trading.

### 🧠 Secure Execution & Order Matching

- **Marlin TEE + NestJS** – The backend listens to encrypted deposit events, decrypts using @inco/js within a TEE, matches trades, and signs off-chain updates.
  - Job ID: `0x0000000000000000000000000000000000000000000000000000000000000bca`
  - IP Address: `43.204.7.162`

### 🔗 Smart Contracts

- **Solidity on Base Sepolia**  
  - Built using `@inco/lightning` and Inco’s `ConfidentialERC20` standard  
  - Manages encrypted token deposits, off-chain balance sync, and attested withdrawals

- **OpenZeppelin** – Leveraged ERC20, ECDSA, and MessageHashUtils

### 🖥️ Frontend

- **Next.js + Wagmi + Viem + ShadCN + TailwindCSS**
- Uses `@inco/js` to:
  - Encrypt amounts before deposit
  - Decrypt balances client-side for rendering
  - Handle encrypted withdrawal payloads

## 📜 Contracts Deployed

### 🔐 cUSDC Token
- Address: `0x1bc80bcc4fbb107fcf65d09e84d4c6ff5e0b9e7b`
- BaseScan: https://sepolia.basescan.org/address/0x1bc80bcc4fbb107fcf65d09e84d4c6ff5e0b9e7b#code
- Description: ERC20 token with encrypted balances powered by Inco FHE

### 🔐 cCMF Token
- Address: `0x144481927c78798b5c38890c2e8e777de27dfc97`
- BaseScan: https://sepolia.basescan.org/address/0x144481927c78798b5c38890c2e8e777de27dfc97#code
- Description: ERC20 token with encrypted balances powered by Inco FHE

### 🔄 Confidex Contract
- Address: `0x571f608851abf768f332233a43b6d54240cda01e`
- BaseScan: https://sepolia.basescan.org/address/0x571f608851abf768f332233a43b6d54240cda01e#code
- Description: Orchestrates encrypted deposits, state attestations, and secure withdrawals with FHE

## ⚙️ How Confidex Works

1. User encrypts deposit amount via `@inco/js` and sends to smart contract  
2. TEE decrypts using `@inco/js`, updates Merkle balance state  
3. Users submit FHE-encrypted trade intents  
4. TEE batch decrypts intents → matches via CoW algorithm → signs state root  
5. User withdraws → encrypted withdrawal amount signed by TEE → contract verifies and releases tokens

## 🚫 Preventing MEV & Frontrunning

- 🔐 Encrypted Intents – No visibility to bots or external observers
- 🧠 TEE Matching – Private, deterministic, and tamper-resistant execution
- ✅ Attested Withdrawals – Enforces correctness with cryptographic proof

## 🧪 Hacky & Cool Innovations

- 🧬 First use of Inco’s ConfidentialERC20 in a working DEX
- 🔄 FHE Decryption/Encryption inside TEE using `@inco/js`
- 🌲 Merkle Tree compression of balance states
- 🔒 True full-stack encrypted DeFi system: UI → TEE → Chain



## 🚀 Getting Started

See individual submodule READMEs for setup and deployment instructions.

## 🤝 Contributing

We welcome contributions! Check out [CONTRIBUTING.md](CONTRIBUTING.md) for details.

## 📄 License

MIT – See [LICENSE](LICENSE)

---

> This project is under active development. Expect updates, enhancements, and cool new privacy features!




