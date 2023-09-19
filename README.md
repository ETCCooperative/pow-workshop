# Workshop: PoW Mining on a Private Network with core-geth

## Introduction
- Welcome participants and provide an overview of the workshop's goals.
- Briefly introduce Ethereum Classic and core-geth.

## Setting Up a Private Network

In this section, we will guide you through setting up a private Ethereum Classic network using the core-geth client. We have prepared a GitHub repository with all the necessary files to make this process easy for you. Follow the steps below:

**1. Download Workshop Materials**
- Visit our GitHub repository: [https://github.com/ETCCooperative/pow-workshop](https://github.com/ETCCooperative/pow-workshop)

**2. Clone the Repository**
- If you have Git installed, open your terminal and run the following command to clone the repository to your local machine:
  ```bash
  git clone https://github.com/ETCCooperative/pow-workshop.git
  ```

- Alternatively, you can download the repository as a ZIP file by clicking the "Code" button on the GitHub page and selecting "Download ZIP." Extract the ZIP file to a location of your choice.

**3. Download core-geth**
- Download the latest core-geth release for your operating system from the [core-geth releases page](https://github.com/etclabscore/core-geth/releases/tag/v1.12.13).

Place the `geth` binary into the `pow-workshop` directory where you downloaded the repository.

**3. Locate the Genesis Configuration File**
- Inside the downloaded repository folder, you will find a file named `genesis.json`. This file contains the configuration for the initial block of your private network. You can customize this file based on your preferences.

**4. Initialize Your Private Network**
- Open your terminal and navigate to the `pow-workshop` directory where you downloaded the repository.

- Initialize a new private network using the core-geth client and the `genesis.json` file. Replace  with the path where you want to store your blockchain data.
  ```bash
  ./geth --datadir workshop_datadir --networkid 8932763451 init genesis.json
  ```

On command succeed you must see the following output:
```bash
INFO [09-19|15:18:31.854] Successfully wrote genesis state         database=lightchaindata hash=edd47b..83806d
```

> NOTE: on MacOS, you may need to trust the geth binary before running it. To do so, run the following command:
>  ```bash
>    xattr -d com.apple.quarantine geth
>  ```
> Or go to system settings -> security & privacy -> general -> allow geth to run.

**5. Start Your Private Node**
- After initializing the private network, you can start your core-geth private node with the following command:
  ```bash
  ./geth --datadir workshop_datadir --networkid 8932763451 --http --http.corsdomain "*" --bootnodes enode://4d191f544f993eddf3d0ef7c996d33643822c59995cf72aa1fdcb980f11018d53ffd3c9b66bef42ff5737692fe6600284310e48a0804c010a0f3d9c94c646463@127.0.0.1:30303
  ```

- Replace datadir, if needed, with the same path used in the initialization step.

**6. You're Ready to Go!**
- Your private PoW network is now up and running. You can use this private network for mining and development purposes during this workshop.

## Mining
**Show participants how to enable mining on their nodes:**
- Create a wallet so as to use its address as the etherbase.
- Run geth with the `--mine` flag to enable mining.
  ```bash
  ./geth --datadir workshop_datadir --networkid 8932763451 --http --http.corsdomain "*" --bootnodes enode://4d191f544f993eddf3d0ef7c996d33643822c59995cf72aa1fdcb980f11018d53ffd3c9b66bef42ff5737692fe6600284310e48a0804c010a0f3d9c94c646463@2.87.118.100:30303 --miner.etherbase "<SET_YOUR_ETHERBASE>" --miner.threads 2 --mine
  ```

> IMPORTANT: On a mining node, never expose the HTTP or WS APIs. Doing so will allow anyone to control your node and steal your funds.
> Here we are exposing the HTTP API for demonstration purposes only to see your balance changes in Metamask.

## Connecting Metamask
**Guide participants on connecting Metamask to your private network:**
- From your browser download the Metamask extension.
- Open Metamask and click on the network dropdown.
- Select "Add network."
- Select "Add network manually."
- Provide the following info:
  - Network Name: `PoW Workshop`
  - New RPC URL: `http://127.0.0.1:8545`
  - Chain ID: `8932763451`
  - Currency Symbol: `ETCW`
  - Block Explorer URL: leave blank
- Import an account or create a new one using Metamask.

## Sending Transfers
**Demonstrate how participants can send transactions using Metamask:**
- Send a simple transaction between two Metamask accounts on your private network.

## Q&A and Conclusion
- Open the floor for questions.
- Provide additional resources and documentation for further learning.
- Thank participants for attending and encourage them to explore Ethereum Classic and core-geth further.