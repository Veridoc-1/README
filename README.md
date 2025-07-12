# Veridoc

Veridoc is a decentralized system for storing, verifying, and managing legal documents on the blockchain. Leveraging IPFS for distributed file storage and Ethereum smart contracts (currently deployed on Sepolia testnet), Veridoc ensures that legal documents are tamper-proof, easily accessible, and cryptographically verifiable.

---

## 🚀 Overview

- **Purpose:** Securely store legal documents on-chain with metadata and hash references, ensuring authenticity and integrity.
- **Storage:** Document files are stored on IPFS; only their hashes and metadata are stored on the blockchain.
- **Verification:** Anyone can verify the existence and integrity of a document via its IPFS hash and on-chain record.
- **Network:** Deployed on Sepolia Ethereum testnet.

---

## 🏗️ Contract Structure & Logic

### Main Contract: `DocumentRegistry.sol`

- **Structs:**
  - `Document`: Contains document ID, owner address, IPFS hash, timestamp, and metadata.
- **Mappings:**
  - `documents`: Maps document IDs to `Document` structs.
  - `ownerToDocs`: Maps owner addresses to arrays of their document IDs.
- **Key Functions:**
  - `registerDocument(string calldata ipfsHash, string calldata metadata)`: Registers a new document, storing its IPFS hash and metadata.
  - `getDocument(uint256 docId)`: Retrieves document details by ID.
  - `verifyDocument(uint256 docId, string calldata ipfsHash)`: Validates the document’s hash against the stored value.
  - `getDocumentsByOwner(address owner)`: Lists all documents owned by a specific address.
- **Access Control:**
  - Only the document owner can register or modify their documents.
  - Public read access for verification and retrieval.

---

## ✨ Key Highlights

- **Decentralized Storage:** Uses IPFS for off-chain storage, reducing on-chain costs while maintaining data availability.
- **Tamper-Proof:** Document hashes are immutable once registered, ensuring authenticity.
- **Ownership Tracking:** Each document is linked to an Ethereum address.
- **Open Verification:** Anyone can verify a document’s existence and integrity.
- **Scalable & Modular:** Easy to extend for additional features like document expiry, multi-signature, or access control.

---

## 🧑‍💻 Developer Environment

### Prerequisites

- Node.js (v16+ recommended)
- npm or yarn
- Hardhat (for smart contract development)
- MetaMask or similar wallet for interacting with Sepolia
- IPFS CLI or API access

### Setup

1. **Clone the repository:**
   ```bash
   git clone https://github.com/yourusername/veridoc-contracts.git
   cd veridoc-contracts
   ```

2. **Install dependencies:**
   ```bash
   npm install
   # or
   yarn install
   ```

3. **Compile contracts:**
   ```bash
   npx hardhat compile
   ```

4. **Deploy to Sepolia:**
   - Configure your `.env` with Sepolia RPC URL and private key.
   - Run:
     ```bash
     npx hardhat run scripts/deploy.js --network sepolia
     ```

5. **Testing:**
   ```bash
   npx hardhat test
   ```

---

## 📝 Example Usage

```solidity
// Register a document
registerDocument("QmHash...", "Title: Contract Agreement; Parties: Alice, Bob; Date: 2025-07-13");

// Verify a document
verifyDocument(1, "QmHash...");
```

---

## 📦 Contract ABI & Address

- **Contract Address (Sepolia):** `0xf9225ef9648d273db99a71A2F11255329C31832a`
- **ABI:** See `artifacts/contracts/DocumentRegistry.json`

---

## 🛡️ Security & Considerations

- Never store sensitive document content on-chain.
- IPFS hashes must be pinned for persistent availability.
- Always verify contract addresses and ABIs before interacting on mainnet.

---

## 🤝 Contributing

1. Fork the repo
2. Create your feature branch (`git checkout -b feature/YourFeature`)
3. Commit your changes
4. Push to the branch
5. Open a Pull Request

---

## 📄 License

MIT License. See `LICENSE` file for details.

---

## 📬 Contact

For questions or support, open an issue.
