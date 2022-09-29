## Setting up Local Development Environment for NEAR smart contracts

Welcome on your journey on smart contract development on NEAR blockchain protocol. It would be fun and challenging — wishing you lots of AHA 💡 moments. 

This article aims to help you setup your local system for smartcontract development on NEAR protocol. It includes guides on installing WSL for Windows users, and steps for installing the necessary programs and libraries.

NEAR is a simple, scalable and fast layer 1 blockchain protocol used for building decentralised applications. NEAR runs smartcontracts compiled to WebAssembly (wasm).  Currently there are Rust and AssemblyScript (a dialect of Typescript) official SDKs.

*NOTE: You do not have to do this to start developing on NEAR — You can get started in seconds by opening [existing contracts on Gitpod](https://examples.near.org/) online IDE.*

## **Setting up Windows Subsystem for Linux (WSL).**

   *Non-windows users should [skip this step](#install-lib)

This is an essential step in your smart contract development process as Windows OS user — most SDKs, Docs, tutorials and developer tools assume you are on a Linux/GNU environment. This step makes you develop contracts seamlessly.

[WSL](https://docs.microsoft.com/en-us/windows/wsl/about)  removes the need for virtual machine and let’s you seamlessly run a GNU/Linux environment “including most command-line tools, utilities, and applications -- directly on Windows”. 

### **Setting up your WSL dev environment(Git, VS Code and Windows Terminal).**

Install WSL2 using this straight to the point [official doc by Microsoft](https://docs.microsoft.com/en-us/windows/wsl/setup/environment). Ubuntu, the default Linux distribution that WSL now comes with suits our purpose — you can use any distribution, of course. 

The guide includes instructions on setting up your code editor, I recommend you use Visual studio code. You can ignore the instructions on how to setup Docker, Databases etc., but make sure you read the part about Basic WSL commands and Git setup for WSL.

If you prefer a video instruction on setting up WSL [this is an awesome resource](https://www.youtube.com/watch?v=2TKh3aokgec).

Remember, for Windows 10 and 11 WSL now comes with Ubuntu distro by default, and you do not have to install Docker.

## **Installing essential program and libraries (Linux, MacOs and WSL).** <span id="install-lib"><span>

*If you are on Windows ensure you’re running the following commands in WSL. There is also an Apple M1 specific workarounds mentioned in this post.*

### Essential Programs

- **Node**
Follow the instructions here  [Microsoft official docs](https://learn.microsoft.com/en-us/windows/dev-environment/javascript/nodejs-on-wsl#install-nvm-nodejs-and-npm) to install nvm and nodejs on your wsl linux distro.

   On WSL ensure you [change the npm default directory](https://docs.npmjs.com/resolving-eacces-permissions-errors-when-installing-packages-globally#manually-change-npms-default-directory), to avoid permission issues with WSL.

- **Yarn**
Using node package manager, that comes with Node.js (already installed in the previous step. Run `npm install --global yarn` on the command line to install yarn globally.

- **Rust**
Install rust using Rustup by running the following command.

 `curl --proto '=https' --tlsv1.2 -sSf [https://sh.rustup.rs](https://sh.rustup.rs/) | sh` 

   Add wasm target to your RUST toolchain by running this  `rustup target add wasm32-unknown-unknown` command.

   I mentioned earlier that  NEAR currently has SDKs for Rust and AssemblyScript. The preferred programming language for writing smart contracts on NEAR. If you do not have prior experience writing Rust, I’d recommend you start with AS then subsequently learn RUST.

- **AssemblyScript**
To install AS globally run `npm install --global  assemblyscript` . 

### NEAR CLI and Libraries

These are the library for easy writing Smart contracts on NEAR.  Apple M1 users should [read this guide](https://docs.near.org/docs/faq/developer-faq#4-building-smart-contracts-on-apple-m1-arm64) for workarounds to using Near SDKs.
 
- **Installing **NEAR Command Line Interface** **
You will use NEAR CLI to interact with the NEAR blockchain. To install, run `npm i -g near-cli`

- **Rust SDK**
You will have to add this in your cargo.toml file each time when creating a new Rust smart contract project. There are various ways of starting a Rust this, and more instructions can be [found here](https://www.near-sdk.io/).

- **AssemblyScript SDK**
To use near-as-sdk run `yarn add -D near-sdk-as` 

- **NEAR-API-JS**
Run `npm i -g near-api-js` to install the JS library that would connect your applications to the NEAR blockchain.

### Creating your NEAR Account.

You need a NEAR account to interact with the blockchain, you will also use accounts when deploying smartcontracts.
You can [create account in the mainnet](https://wallet.near.org/) (you can think of this as the live network of near protocol) and for development purposes you need to create account on [the testnet](https://wallet.testnet.near.org/). This is an easy process, ensure you keep your passphrase safe.

You may check these [step-by-step](https://docs.near.org/docs/develop/basics/create-account) instructions on creating accounts.

Congratulations! You can now start developing smart contracts on NEAR. 

### What's next?

Check out these official guides to get started.

**AssemblyScript** SmartContracts [AssemblyScript | NEAR Documentation](https://docs.near.org/docs/develop/contracts/as/intro)

**Rust**:  [Building a Smart Contract in Rust | NEAR Documentation](https://docs.near.org/docs/develop/contracts/rust/intro) and [https://www.near-sdk.io/](https://www.near-sdk.io/)