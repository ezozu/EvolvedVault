# EvolvedVault: Decentralized NFT Marketplace

A secure and powerful platform for trading, fractionalizing, and managing NFTs with on-chain royalties.

## Detailed Description

EvolvedVault is a decentralized NFT marketplace built to provide a comprehensive and secure ecosystem for creators and collectors. The platform leverages the power of smart contracts to facilitate atomic swaps, enabling trustless peer-to-peer NFT trading. Beyond simple trading, EvolvedVault introduces the concept of fractional ownership, allowing NFTs to be divided into smaller, more accessible units, opening up investment opportunities to a broader audience. Critically, the platform ensures transparent and immutable on-chain royalty payments to creators, fostering a sustainable and equitable NFT economy.

This project prioritizes security through rigorous smart contract audits and best-practice development methodologies. EvolvedVault is designed to be highly modular and extensible, allowing for seamless integration of new features and functionalities in the future. The use of TypeScript ensures type safety and maintainability, making it easier for developers to contribute to the project. The platform's design emphasizes gas efficiency, reducing transaction costs and making it more accessible to users.

EvolvedVault aims to address several limitations of existing NFT marketplaces. By implementing atomic swaps, it eliminates the need for intermediaries and reduces the risk of fraud. Fractional ownership allows for greater liquidity and democratizes access to high-value NFTs. And perhaps most importantly, the platform's on-chain royalty mechanism guarantees that creators receive fair compensation for their work, directly supporting the NFT ecosystem. The architecture is designed with future scalability in mind, enabling the platform to adapt to the evolving needs of the NFT market.

## Key Features

*   **Atomic Swaps:** Facilitates trustless peer-to-peer NFT trading through secure smart contract orchestration. The swap logic ensures that both the NFT and the agreed-upon payment are exchanged simultaneously, eliminating counterparty risk. (Implemented via Solidity contract `AtomicSwap.sol`).
*   **Fractional Ownership:** Allows NFTs to be divided into fungible ERC-20 tokens, enabling shared ownership and increased liquidity. The fractionalization process involves locking the original NFT in a smart contract and minting corresponding ERC-20 tokens. (Implemented via Solidity contract `FractionalNFT.sol`).
*   **On-Chain Royalties:** Enforces transparent and immutable royalty payments to creators directly within the smart contract logic. Royalties are automatically distributed to the creator upon each sale or transfer of the NFT. (Implemented using ERC-2981 standard in Solidity).
*   **Decentralized Governance (Future Implementation):** Planned implementation of a DAO (Decentralized Autonomous Organization) allowing token holders to vote on key platform parameters and governance decisions.
*   **Gas Optimization:** Smart contracts are optimized for gas efficiency to minimize transaction costs for users. This includes using efficient data structures and minimizing storage operations. (Utilizes best practices in Solidity development).
*   **Secure Smart Contracts:** All smart contracts are rigorously audited and tested to ensure security and prevent vulnerabilities. This includes formal verification and penetration testing. (Audited by a third-party security firm).
*   **TypeScript Frontend:** The user interface is built with TypeScript for type safety and improved developer experience. This ensures a robust and maintainable codebase.

## Technology Stack

*   **TypeScript:** Primary language for the frontend and backend components, providing type safety and improved code maintainability.
*   **React:** Used for building the user interface, providing a component-based architecture and efficient rendering.
*   **Solidity:** Smart contract language used for implementing the core marketplace logic on the blockchain (Ethereum or compatible chains).
*   **Hardhat:** Development environment for compiling, testing, and deploying Solidity smart contracts.
*   **Ethers.js/Web3.js:** JavaScript libraries for interacting with the Ethereum blockchain and smart contracts.
*   **Node.js:** Backend runtime environment for handling API requests and interacting with the blockchain.
*   **IPFS (InterPlanetary File System):** Decentralized storage system for storing NFT metadata and assets.

## Installation

1.  Clone the repository:

    git clone https://github.com/ezozu/EvolvedVault.git

2.  Navigate to the project directory:

    cd EvolvedVault

3.  Install dependencies:

    npm install

4.  Install Hardhat globally:

    npm install --global hardhat

## Configuration

1.  Create a `.env` file in the project root directory.
2.  Add the following environment variables:

    PRIVATE_KEY=<Your Ethereum private key>
    INFURA_API_KEY=<Your Infura API key>
    ALCHEMY_API_KEY=<Your Alchemy API key>
    NETWORK=goerli (or other supported network)

3.  Configure Hardhat in `hardhat.config.ts` to use the specified network and private key.

    Example `hardhat.config.ts` snippet:

    module.exports = {
      solidity: "0.8.4",
      networks: {
        goerli: {
          url: `https://goerli.infura.io/v3/${process.env.INFURA_API_KEY}`,
          accounts: [process.env.PRIVATE_KEY],
        },
      },
    };

## Usage

1.  Compile smart contracts:

    npx hardhat compile

2.  Deploy smart contracts to the specified network:

    npx hardhat run scripts/deploy.ts --network goerli

3.  Interact with the smart contracts using Ethers.js or Web3.js in the frontend.

    Example JavaScript code snippet (using Ethers.js):

    import { ethers } from "ethers";
    const provider = new ethers.providers.JsonRpcProvider(process.env.INFURA_API_KEY);
    const signer = new ethers.Wallet(process.env.PRIVATE_KEY, provider);
    const contractAddress = "<Deployed Contract Address>";
    const contract = new ethers.Contract(contractAddress, <ABI>, signer);
    async function mintNFT(tokenURI) {
      const transaction = await contract.mint(tokenURI);
      await transaction.wait();
      console.log("NFT minted!");
    }

## Contributing

We welcome contributions to EvolvedVault! Please follow these guidelines:

1.  Fork the repository.
2.  Create a new branch for your feature or bug fix.
3.  Write clear and concise commit messages.
4.  Submit a pull request with a detailed description of your changes.
5.  Ensure that your code adheres to the project's coding standards and passes all tests.

## License

This project is licensed under the MIT License. See the [LICENSE](https://github.com/ezozu/EvolvedVault/blob/main/LICENSE) file for details.

## Acknowledgements

We would like to acknowledge the following open-source projects and libraries that were used in the development of EvolvedVault:

*   OpenZeppelin Contracts
*   Ethers.js
*   React
*   Hardhat