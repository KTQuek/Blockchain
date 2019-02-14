# Decentralized StarNotary Project

This is project 5 for the Udacity Blockchain Nano Degree program. 
The project involve modifying the StarNotary version 2 contract to achieve the following:

(1) Adding a name and a symbol for the starNotary token.
(2) Adding a function called "lookUptokenIdToStarInfo" for looking up the stars using the Token ID, and then returning the name of the star.
(3) Adding a function called "exchangeStars" so that 2 users can exchange their star tokens.
(4) Adding a function for transferring a Star from the address of the caller. This function accepts 2 arguments, the address to transfer the star to and the token ID of the star.
(5) Adding unit tests for checking:
    (i)   The token name and token symbol could be added properly.
    (ii)  Two users can exchange their stars.
    (iii) Star Tokens can be transferred from one address to another.
(6) Deploying the contract to the Rinkeby test network.
(7) Modifying the front end of the DAPP to support the looking up of a star by using its ID.

# Key details

(1) Truffle version:      Truffle v5.0.3
(2) ERC-721 Token Name:   Star Token
(3) ERC-721 Token Symbol: STK
(4) Token Address on the Rinkeby Test Network:   '0x19eB8340b655E1bd4A2dbfF0b9b152f12983E654'
(5) Transaction Hash for creating the contract on Rinkeby Test Network: '0x98888dd71a374651ec8396cb72a021ea2f54d2ddd9694215709f3a6fe92f26b6'
(6) Etherscan: https://rinkeby.etherscan.io/tx/0x98888dd71a374651ec8396cb72a021ea2f54d2ddd9694215709f3a6fe92f26b6


# Deploying this DAPP locally

(1) Navigate to the project folder.
(2) Run truffle develop or sudo truffle develop
(3) Run compile
(4) Run migrate --reset
(5) Open a second terminal window
(6) Run cd app
(7) Run npm run dev
(8) Open http://localhost:8080

# Deploying the contract on the Rinkeby Test Network

(1) Run truffle migrate --reset --network rinkeby


# truffle-config.js

Before deploying on the Rinkeby Test Network you will need to modify the truffle-config.js to include the following:

const HDWalletProvider = require('truffle-hdwallet-provider');
const infuraKey = "<Infura PROJECT ID>";
//
// const fs = require('fs');
const mnemonic = "<METAMASK SEED>";

module.exports = {

  networks: {
    development: {
      host: "127.0.0.1",     // Localhost (default: none)
      port: 9545,            // Standard Ethereum port (default: none)
      network_id: "*",       // Any network (default: none)
     },
    // Useful for deploying to a public network.
    // NB: It's important to wrap the provider as a function.
    rinkeby: {
      provider: () => new HDWalletProvider(mnemonic, `https://rinkeby.infura.io/v3/${infuraKey}`),
        network_id: 4,       // rinkeby's id
        gas: 4500000,        // rinkeby has a lower block limit than mainnet
        gasPrice: 10000000000
    },
  },

  // Set default mocha options here, use special reporters etc.
  mocha: {
    // timeout: 100000
  },

  // Configure your compilers
  compilers: {
    solc: {
      // version: "0.5.1",    // Fetch exact version from solc-bin (default: truffle's version)
      // docker: true,        // Use "0.5.1" you've installed locally with docker (default: false)
      // settings: {          // See the solidity docs for advice about optimization and evmVersion
      //  optimizer: {
      //    enabled: false,
      //    runs: 200
      //  },
      //  evmVersion: "byzantium"
      // }
    }
  }
}

