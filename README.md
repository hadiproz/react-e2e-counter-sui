# React E2E Counter - Sui dApp

A full-stack decentralized application (dApp) built on the Sui blockchain featuring a simple counter smart contract with React frontend integration.

## 🚀 Features

- **Smart Contract**: Counter module written in Move language
- **React Frontend**: Modern UI built with React, TypeScript, and Vite
- **Sui Integration**: Seamless blockchain interaction using @mysten/dapp-kit
- **Wallet Connection**: Connect with Sui wallets
- **Counter Operations**:
  - Create new counter instances
  - Increment counter values
  - Set counter values (owner only)
  - View counter state in real-time

## 📁 Project Structure

```
react-e2e-counter-sui/
├── move/counter/              # Smart contract
│   ├── sources/
│   │   └── counter.move      # Counter module
│   ├── Move.toml             # Move package manifest
│   └── build/                # Compiled bytecode
│
└── my-first-sui-dapp/        # React frontend
    ├── src/
    │   ├── App.tsx           # Main app component
    │   ├── Counter.tsx       # Counter display component
    │   ├── CreateCounter.tsx # Counter creation component
    │   ├── constants.ts      # Package ID & config
    │   └── networkConfig.ts  # Sui network configuration
    ├── move/counter/         # Local Move module reference
    ├── package.json
    └── vite.config.mts
```

## 🛠️ Prerequisites

- [Node.js](https://nodejs.org/) (v18 or higher)
- [pnpm](https://pnpm.io/) package manager
- [Sui CLI](https://docs.sui.io/build/install) installed and configured
- A Sui wallet (e.g., Sui Wallet browser extension)

## 📦 Installation

### 1. Clone the repository

```bash
git clone https://github.com/hadiproz/react-e2e-counter-sui.git
cd react-e2e-counter-sui
```

### 2. Install frontend dependencies

```bash
cd my-first-sui-dapp
pnpm install
```

## 🏗️ Build & Deploy Smart Contract

### 1. Build the Move package

```bash
cd move/counter
sui move build
```

### 2. Deploy to Sui network

```bash
# For testnet
sui client publish --gas-budget 100000000

# Save the Package ID from the output
```

### 3. Update Package ID

Copy the Package ID from deployment output and update in `my-first-sui-dapp/src/constants.ts`:

```typescript
export const COUNTER_PACKAGE_ID = "YOUR_PACKAGE_ID_HERE";
```

## 🚀 Running the dApp

### Start the development server

```bash
cd my-first-sui-dapp
pnpm dev
```

The app will be available at `http://localhost:5173`

### Build for production

```bash
pnpm build
pnpm preview
```

## 💡 How to Use

1. **Connect Wallet**: Click "Connect Wallet" and select your Sui wallet
2. **Create Counter**: Click "Create Counter" to deploy a new counter instance
3. **Increment**: Click the increment button to increase the counter
4. **Set Value**: As the owner, you can set a custom value
5. **Share**: Share the URL with the counter ID in the hash to let others view/interact

## 📜 Smart Contract Functions

### `create(ctx: &mut TxContext)`
Creates a new shared Counter object with initial value 0

### `increment(counter: &mut Counter)`
Increments the counter value by 1 (anyone can call)

### `set_value(counter: &mut Counter, value: u64, ctx: &TxContext)`
Sets a custom value (only owner can call)

## 🔧 Tech Stack

### Frontend
- **React 18** - UI library
- **TypeScript** - Type safety
- **Vite** - Build tool
- **@mysten/dapp-kit** - Sui wallet integration
- **@mysten/sui** - Sui SDK
- **@radix-ui/themes** - UI components
- **@tanstack/react-query** - Data fetching

### Smart Contract
- **Move** - Sui smart contract language
- **Sui Framework** - Standard library

## 🌐 Network Configuration

The dApp is configured to work with Sui networks. Update `networkConfig.ts` to switch networks:

```typescript
import { getFullnodeUrl } from "@mysten/sui/client";
import { createNetworkConfig } from "@mysten/dapp-kit";

const { networkConfig, useNetworkVariable, useNetworkVariables } =
  createNetworkConfig({
    testnet: { url: getFullnodeUrl("testnet") },
    mainnet: { url: getFullnodeUrl("mainnet") },
  });

export { networkConfig, useNetworkVariable, useNetworkVariables };
```

## 📝 License

This project is open source and available under the MIT License.

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

## 📧 Contact

- GitHub: [@hadiproz](https://github.com/hadiproz)
- Repository: [react-e2e-counter-sui](https://github.com/hadiproz/react-e2e-counter-sui)

## 🙏 Acknowledgments

- [Sui Documentation](https://docs.sui.io/)
- [Mysten Labs](https://mystenlabs.com/)
- Sui developer community

---

**Built with ❤️ on Sui blockchain**
