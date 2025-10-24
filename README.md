# 🎮 Base Stack - Web3 Social Puzzle Game

**Base Batches 002: Builder Track Submission**

Base Stack is a revolutionary Web3 social puzzle game that seamlessly bridges traditional gaming with blockchain technology. Built specifically for Farcaster's social ecosystem, players enjoy classic match-3 puzzle mechanics while their achievements are permanently recorded on the Base blockchain, creating verifiable, tamper-proof leaderboards.

## 📱 Screenshots

| Game Interface 1 | Game Interface 2 |
|------------------|------------------|
| <img width="300" alt="Game Interface 1" src="https://github.com/user-attachments/assets/3a6153c2-bb18-42ef-acb4-baa26bf16193" /> | <img width="300" alt="Game Interface 2" src="https://github.com/user-attachments/assets/24a7b6dd-c107-47f0-8c91-bc60019135c9" /> |

## 🚀 Live Demo

- **Farcaster Mini App**: [Play on Farcaster](https://farcaster.xyz/miniapps/eXi6Yi5K2MIp/base-stack)
- **Direct Access**: [Base Stack Game](https://farcaster-base-cardgame-gilt.vercel.app/)
- **Contract**: [0xEc632126Ea270D792b71379f223fbEE1C496f6DE](https://basescan.org/address/0xEc632126Ea270D792b71379f223fbEE1C496f6DE)

## ✨ Key Features

### 🎯 **Progressive Web3 Onboarding**
- **Invisible Blockchain**: Users learn Web3 concepts through gameplay, not tutorials
- **Seamless Wallet Integration**: Connect with MetaMask, Coinbase Wallet, or Farcaster
- **Low-Cost Transactions**: Optimized for Base network's minimal gas fees

### 🏆 **Permanent On-Chain Achievements**
- **Tamper-Proof Leaderboards**: All scores recorded on Base blockchain
- **Cumulative Scoring**: Player progress accumulates across multiple sessions
- **Verifiable Records**: Achievements can't be manipulated or lost

### 📱 **Farcaster-Native Social Experience**
- **Automatic Profile Integration**: Uses Farcaster user data seamlessly
- **One-Click Sharing**: Share achievements as Farcaster casts
- **Viral Growth Mechanics**: Built-in social features drive organic growth

### 🎮 **Classic Puzzle Gameplay**
- **Match-3 Mechanics**: Familiar and engaging puzzle gameplay
- **Power-Ups**: Clock (freeze time) and Key (auto-match) abilities
- **Progressive Difficulty**: 3 lives system with increasing challenge

## 🛠️ Technology Stack

### **Frontend**
- **Next.js 14.2.6** - React framework
- **TypeScript** - Type-safe development
- **Tailwind CSS** - Utility-first styling
- **Styled Components** - Dynamic styling

### **Blockchain & Web3**
- **Base Network** - Layer 2 blockchain
- **Wagmi 2.17.5** - React hooks for Ethereum
- **Viem 2.22.22** - TypeScript Ethereum interface
- **Reown AppKit** - Multi-wallet connection

### **Farcaster Integration**
- **@farcaster/miniapp-sdk** - Social platform integration
- **@farcaster/miniapp-wagmi-connector** - Wallet integration
- **Farcaster Context** - User profile and social data

### **Smart Contract**
- **Contract Address**: `0xEc632126Ea270D792b71379f223fbEE1C496f6DE`
- **Network**: Base Mainnet
- **Functions**: `setScore`, `addScore`, `getAllScoresDescending`

## 🏗️ Smart Contract Architecture

### **Core Functions**
```solidity
// Create new user profile and set initial score
function setScore(uint256 _score, string _username, uint256 _fid, string _pfp)

// Add score for existing users
function addScore(uint256 _score)

// Get leaderboard data
function getAllScoresDescending() returns (UserProfile[])

// Check if user exists
function hasProfile(address _user) returns (bool)
```

### **User Profile Structure**
```solidity
struct UserProfile {
    string username;
    uint256 fid;        // Farcaster ID
    string pfp;         // Profile picture URL
    uint256 score;      // Cumulative score
    bool exists;
}
```

## 🚀 Quick Start

### **Prerequisites**
- Node.js 18+
- pnpm package manager
- Base network wallet

### **Installation**

1. **Clone the repository**
```bash
git clone https://github.com/Rahul-Roy-Hub/base-stack.git
cd base-stack
```

2. **Install dependencies**
```bash
pnpm install
```

3. **Set up environment variables**
```bash
cp .env.example .env.local
```

4. **Configure environment**
```bash
# .env.local
NEXT_PUBLIC_URL=your-deployed-url
REOWN_PROJECT_ID=your-reown-project-id
```

5. **Run development server**
```bash
pnpm dev
```

### **Farcaster Mini App Testing**

1. **Install Cloudflared**
```bash
brew install cloudflared
```

2. **Expose localhost**
```bash
cloudflared tunnel --url http://localhost:3000
```

3. **Test in Farcaster Embed Tool**
- Use the provided URL in [Warpcast Embed tool](https://warpcast.com/~/developers/mini-apps/embed)

## 🎯 Game Mechanics

### **How to Play**
- 🎯 **Match 3 same cards** to clear them
- 📱 **Tap cards on top** (not blocked by others)
- ⏰ **Beat the timer** before running out of moves
- ❤️ **3 lives system** - lose them all = game over

### **Power-Ups**
- 🕐 **Clock**: Freeze time once per game
- 🔑 **Key**: Auto-match best trio once per game

### **Scoring System**
- **Base Score**: Points for matched cards
- **Time Bonus**: Faster completion = higher score
- **Cumulative**: Scores accumulate across sessions
- **On-Chain**: All scores permanently recorded

## 📊 Smart Contract Integration

### **Score Submission Flow**
1. **Check User Status**: Determine if new or existing user
2. **Profile Creation**: New users get profile with `setScore`
3. **Score Addition**: Existing users get `addScore`
4. **Leaderboard Update**: Scores appear on live leaderboard

### **Contract Interaction**
```typescript
// New user flow
await writeContract({
  functionName: 'setScore',
  args: [BigInt(score), username, BigInt(fid), pfp]
})

// Existing user flow
await writeContract({
  functionName: 'addScore',
  args: [BigInt(score)]
})
```

## 🌐 Deployment

### **Base Network Deployment**
- **Contract**: Deployed on Base Mainnet
- **Address**: `0xEc632126Ea270D792b71379f223fbEE1C496f6DE`
- **Verification**: [View on BaseScan](https://basescan.org/address/0xEc632126Ea270D792b71379f223fbEE1C496f6DE)

### **Frontend Deployment**
- **Platform**: Vercel (recommended)
- **Domain**: Configure custom domain
- **Environment**: Set production environment variables

## 🔧 Development

### **Project Structure**
```
base-stack/
├── app/                    # Next.js app directory
├── components/            # React components
│   ├── Home/              # Game components
│   ├── Leaderboard/       # Leaderboard UI
│   └── sharing/           # Social sharing
├── hooks/                 # Custom React hooks
├── lib/                   # Utilities and config
├── smartcontracthooks/    # Contract integration
└── types/                 # TypeScript types
```

### **Key Components**
- **GameBoard**: Main game logic and UI
- **ScoreSubmission**: On-chain score submission
- **GameLeaderboard**: Live leaderboard display
- **ScoreShare**: Farcaster social sharing
- **WalletConnect**: Multi-wallet integration

## 📈 Future Roadmap

### **Phase 1: Core Features** ✅
- [x] Basic puzzle gameplay
- [x] On-chain scoring
- [x] Farcaster integration
- [x] Social sharing

### **Phase 2: Enhanced Features**
- [ ] NFT achievements
- [ ] Tournament system
- [ ] Team competitions
- [ ] Advanced power-ups


## 🤝 Contributing

We welcome contributions! Please see our [Contributing Guide](CONTRIBUTING.md) for details.

### **Development Setup**
1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Test thoroughly
5. Submit a pull request

## 📄 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 🙏 Acknowledgments

- **Base Network** - For the amazing L2 infrastructure
- **Farcaster** - For the social platform integration
- **Reown** - For wallet connection solutions
- **Base Community** - For support and feedback

---

**Built with ❤️ for Base Batches 002: Builder Track**

*Base Stack - Where Web3 meets social gaming*