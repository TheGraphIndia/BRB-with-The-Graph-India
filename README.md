# Push Protocol's BRB with The Graph Protocol

gm gm gm!!!

This repo is your starting point to work on The Graph Protocol during BRB.

This repo contains step-by-step instruction on building a subgraph and using it's endpoint to showcase the data. 

So, LFG🚀

---

## Deploy your Subgraph

### Description

Deploy a simple smart contract on the Polygon Mumbai testnet and deploy a subgraph for it.

### BUIDLing!!!

- Open [Remix IDE](https://remix.ethereum.org/). Create a Solidity file `Graphathon.sol` and paste the following code.

    ```solidity
    //SPDX-License-Identifier: MIT
    pragma solidity ^0.8.7;

    contract BRBwithGraph {

    event ChangeNameEvent (string name);
    event ChangeTwitterNameEvent (string name);
    event TransferEvent(address from, address to, uint amount);

    string public name = "The Graph";
    string public twitterName = "graphprotocol";

    function changeName(string calldata _name) public {
        name = _name;
        emit ChangeNameEvent(_name);
    }

    function changeTwitterName(string calldata _twitterName) public {
        twitterName = _twitterName;
        emit ChangeTwitterNameEvent(_twitterName);
    }

    function transfer(address payable to) public payable {
        to.transfer(msg.value);
        emit TransferEvent(msg.sender, to, msg.value);
    }
    }
    ```
- Compile the contract and deploy it to Mumbai testnet using `Injected Provider` as the environment. Note down the contract address.
- Verify and publish your smart contract (Don't know how? See [this](https://medium.com/etherscan-blog/verifying-contracts-on-etherscan-f995ab772327))
- Go to the [Subgraph studio](https://thegraph.com/studio/) and connect your wallet.
- Click on `Create a Subgraph`. Name your subgraph and select 'Polygon Mumbai' as the blockchain network. Your subgraph is created 🤩.
- You need to install The Graph protocol CLI to work with the subgraph.
    ```
    npm install -g @graphprotocol/graph-cli
    ```
    OR
    ```
    yarn global add @graphprotocol/graph-cli
    ```
- Create an empty folder and open it in your code editor (I love VSCode ❤️). Change the directory to that folder and fire up your terminal pointing to that folder.
- Now we will initialize the subgraph using the following command
    ```
    graph init --studio SUBGRAPH_NAME
    ```
- Select `ethereum` as Protocol
- Press Enter for `subgraph slug` and `Directory to create subgraph in`.
- Select `mumbai` as our network.
- Enter the contract address of your deployed contract from above. It will automatically fetch the ABI as we have verified our contract.
- Enter the block number in which the contract is created.
- Enter `BRBwithGraph` as the contract name.
- Press Enter for `Index contract events as entities`.
- You have successfully created your first Subgraph. (YOU ARE AWESOMEEE! 🙇🏻‍♂️)
-------

- You need to authenticate your subgraph. Refer dashboard for the key.
     ```
    graph auth --studio 5a6288af6001705f65d514e5423b018d
    ```
- Change the directory to your deployed subgraph folder
    ```
    cd BRBwithGraph
    ```
- Now we build our subgraph using the following command
  ```
  graph codegen && graph build
  ```
- Final Step - Deploy your subgraph. 🥳🥳🥳
  ```
  graph deploy --studio BRBwithGraph
  ```
- You can give the version as `v0.1`

- Play around with your contract. Transfer some ETH / MATIC or change your name or Twitter username using the Remix IDE.
