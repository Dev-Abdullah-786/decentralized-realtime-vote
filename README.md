Here's a revised version of your README with reworded sections to make it distinct from the original while keeping all the technical details intact:

---

# DeVote - Decentralized Voting App

A sleek, on-chain voting platform powered by **Ethereum** (Sepolia testnet) featuring a neon-inspired interface. Connect your wallet, cast your vote, and watch results update live on the blockchain.

---

## 🎯 Key Features

- **MetaMask Wallet Support** – Securely link your crypto wallet
- **Real-Time Vote Tracking** – Monitor results as they happen on-chain
- **One Vote Per Wallet** – Smart contract prevents duplicate voting
- **Cyberpunk Aesthetic** – Dark theme with glowing neon highlights
- **Zero-Gas Reads** – Viewing data costs nothing
- **Mobile-Friendly** – Looks great on any screen size

---

## 🛠️ Built With

- **Frontend:** HTML, CSS, JavaScript (ES6+)
- **Smart Contract:** Solidity (Voting.sol)
- **Blockchain Library:** Ethers.js v6
- **Network:** Ethereum Sepolia Testnet
- **Wallet Provider:** MetaMask

---

## 📋 What You'll Need

1. **MetaMask Wallet** – [Download here](https://metamask.io)
2. **Sepolia Test ETH** – Grab some free from:
   - https://sepoliafaucet.com
   - https://www.infura.io/faucet/sepolia
3. **Remix IDE** – Deploy contracts at https://remix.ethereum.org

---

## 🚀 Getting Started

### Step 1: Deploy the Contract

1. Open [Remix IDE](https://remix.ethereum.org)
2. Create a new file named `Voting.sol`
3. Paste the contents from the `Voting.sol` file in this repo
4. **Compile:** Go to Solidity Compiler tab → hit Compile
5. **Deploy:**
   - Set Environment to "Injected Provider - MetaMask"
   - Confirm MetaMask is connected to **Sepolia testnet**
   - Enter candidates as constructor input: `["Alice", "Bob", "Charlie"]`
   - Hit **Deploy**
   - Save the contract address that appears

### Step 2: Update Frontend Config

1. Open `app.js` (around line 5)
2. Swap the placeholder with your contract address:
   ```javascript
   const CONTRACT_ADDRESS = "0xYOUR_DEPLOYED_ADDRESS";
   ```

### Step 3: Launch the App

1. Open `index.html` in your browser
2. **Hit "Connect Wallet"**
3. **Confirm** the MetaMask prompt
4. Browse candidates and **submit your vote!**

---

## 📂 Folder Layout

```
Decentralized voting app/
├── index.html          # Main page markup
├── app.js             # Frontend logic (Ethers.js, Web3)
├── style.css          # Neon-themed styles
├── Voting.sol         # Solidity smart contract
└── README.md          # Documentation
```

---

## 🔧 What Each File Does

### **Voting.sol** (Smart Contract)

- `constructor(string[] memory candidateNames)` – Sets up the candidate list
- `vote(uint candidateIndex)` – Records a vote (limited to one per wallet)
- `getCandidates()` – Returns all candidates and their vote totals
- `checkIfVoted(address voter)` – Verifies if an address has already voted
- Uses a `hasVoted` mapping to block repeat voting

### **app.js** (Frontend Logic)

- `connectWallet()` – Links MetaMask and checks for Sepolia network
- `loadCandidates()` – Pulls candidate data from the blockchain
- `renderCandidates()` – Builds the candidate card display
- `castVote(index)` – Sends the vote transaction to the contract
- Helpers: `truncateAddress()`, `escapeHtml()`, `showStatus()`

### **index.html** (Page Structure)

- Header with wallet connection button
- Hero section explaining the app
- Status bar for transaction updates
- Candidate grid (filled by app.js)
- Footer showing contract details

### **style.css** (Styling)

- CSS variables for colors and typography
- Neon dark theme (cyan, purple, green highlights)
- Responsive grid layout
- Animated elements (spinner, pulse, fade effects)

---

## 🔐 Network Settings

**Default Network:** Sepolia Testnet

- Chain ID: `11155111`
- RPC: https://sepolia.infura.io/v3/YOUR_KEY (or use MetaMask's default)

**Switching networks:**

1. Open MetaMask
2. Click the network selector at the top
3. Toggle "Show test networks" if hidden
4. Pick "Sepolia"

---

## 💡 How It Works

### Voting Process

1. **Wallet connects** → MetaMask popup appears
2. **App checks network** → Shows warning if not on Sepolia
3. **Candidates load** → Calls `getCandidates()` (free read)
4. **User clicks Vote** → MetaMask asks for confirmation
5. **Transaction sends** → Blockchain processes it (gas required)
6. **Results refresh** → Frontend pulls updated data
7. **Display updates** → Shows vote percentages and counts

### Contract Behavior

- Each wallet can vote only **once** (tracked via `hasVoted` mapping)
- Voting is **transparent** – anyone can view results
- Votes are **permanent** – no undo on-chain
- **Fully auditable** – all logic is in the Solidity source

---

## 🐛 Common Issues

### "Please switch to Sepolia testnet"

- MetaMask is on the wrong network
- Fix: Open network dropdown → Select Sepolia

### "Contract address not set"

- The contract address in app.js is still the placeholder
- Fix: Deploy on Remix, copy the address into app.js line 5

### "Failed to load candidates"

- Invalid address or contract doesn't exist on Sepolia
- Fix: Redeploy contract and update the address

### "You have already voted"

- This wallet already voted for this contract instance
- Note: Each wallet gets one vote per contract deployment

### "Insufficient Sepolia ETH for gas"

- Wallet needs test ETH for transaction fees
- Fix: Claim free Sepolia ETH from [sepoliafaucet.com](https://sepoliafaucet.com)

---

## 🌐 Pre-Flight Checklist

- [ ] MetaMask installed and set to Sepolia
- [ ] Sepolia test ETH in wallet
- [ ] Contract deployed (address saved)
- [ ] Contract address updated in app.js
- [ ] Page loads without console errors (F12)
- [ ] Connect Wallet button responds
- [ ] Candidates appear after connecting
- [ ] Vote button is clickable
- [ ] Vote transaction confirms successfully
- [ ] Vote count updates on refresh

---

## 📝 Sample Candidates

Try these when deploying:

```
["Bitcoin", "Ethereum", "Solana", "Cardano"]
```

Or customize for your needs:

```
["Option A", "Option B", "Option C", "Option D", "Option E"]
```

---

## 🔗 Helpful Links

- **Remix IDE:** https://remix.ethereum.org
- **Sepolia Faucet:** https://sepoliafaucet.com
- **Etherscan (Sepolia):** https://sepolia.etherscan.io
- **Ethers.js Docs:** https://docs.ethers.org/v6/
- **MetaMask Support:** https://support.metamask.io

---

## ⚖️ License

MIT – Free to use and modify

---

## 🎓 What You'll Learn

This project covers:

- Writing smart contracts in Solidity
- Connecting Web3 with Ethers.js
- Integrating MetaMask wallets
- Reading and writing blockchain data
- Handling real-time updates
- Gas-efficient patterns (view functions)

---

**Built with ❤️ for decentralized voting.**
