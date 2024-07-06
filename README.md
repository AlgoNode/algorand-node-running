# Algorand Node Running

Community driven set of guides, benchmarks and best practices for Algorand node running.

## Official docs

## Quick Start

There are multiple ways to run an Algorand node. Here are the most common use-case focused guides that allows you to quickly setup a non-archival node in ~1hr and optionally become a validator or start incentivized staking*

<!-- TODO
proper guides instead of external links
 -->
### Mouse friendly one-click nodes

#### Windows
* [Aust One Click Node](https://github.com/AustP/austs-one-click-node)

#### Linux/MacOS

Pixelnode provide a simple install script to get your node up and running as quickly and easily as possible.
```sudo curl -L http://get.pixelnode.org | sudo bash```

Once the installation is complete, you should be able to access the Pixelnode web interface on port 8000 of your server's IP address (e.g., http://<your_server_ip>:8000).
Follow the on-screen instructions to configure your Pixelnode Agent.  This might involve specifying the network type (Mainnet, Testnet, etc.) and potentially setting your stake amount (for participation nodes).

The Pixelnode web interface will display the status of your Algorand node. You can see if it's running, syncing with the network (catching up), and other details.

* [Pixelnode](https://www.pixelnode.org/)

### Terminal managed

* [Official one-click-node](https://github.com/algorandfoundation/algorun), docker based
* Linux node on Ubuntu on Windows WSL
* Linux node on Ubuntu

### UI / Web interface add-ons

Algorand provide a Node UI that shows realtime node status, fast-catchup progress and realtime block data (such as proposers).
This UI is accessed via the terminal directly.
On Linux you can download the binary under the Github releases section, and if you run the binary on your local node, just point it to your data directory.

For example:
```
wget https://github.com/algorand/node-ui/releases/download/v0.2.0/nodeui_Linux_x86_64.tar.gz
tar -xzf nodeui_Linux_x86_64.tar.gz
ALGORAND_DATA=/var/lib/algorand ./nodeui
```
* [Official terminal UI](https://github.com/algorand/node-ui)

Another option is Allo'Ctrl, this is a node manager that is accessed via a web browser.
Once the dependancies have been installed, simply create the directory
```
mkdir ~/algorand-dashboard
cd ~/algorand-dashboard
```
And run the NPX command to install it.
```
npx alloctrl
    Need to install the following packages:
        alloctrl@0.1.4
    Ok to proceed? (y) 
```
The installer will ask you a few questions to setup the environment file.

* [Allo'Ctrl](https://github.com/AlgoNode/alloctrl) , local node manager

## Node types

### Relay Node

Relay nodes receive and broadcast information (blocks, transactions) between other relay nodes.
They help the network run smoothly and efficiently by distributing messages as quickly and directly as possible across the globe.
It's important to note that these *DO NOT* play any role in the consensus mechanism _(Block Proposal/Transaction Validation/Block Voting)_.

### Participation Node

Participation Nodes are the core of consensus, by securing the network in a decentralised way.
These nodes are responsible for proposing blocks, valdating transactions, and voting on blocks proposed by other nodes.
Requirements are a lot lower as the VRF they run is light on resources, and they only need to keep a record of the last 1000 blocks.
These nodes host the participation keys for an account that has Algo staked.

### Archival Node

Archive nodes store the entire history of the blockchain (all transactions ever made) for anyone who needs it.
This acts as a backup for the network and allows users to see past activity.

### Indexer

Indexers take the massive amount of blockchain data (stored by archival nodes) and organise it for easier searching (such as a Postgres database).
This allows applications (eg: Blockchain explorers such as [allo.info](https://allo.info)) to query the database, and present it to you in a readable / human friendly format.

## Installing

### Home node

### Cloud node

### K8S

### Docker/Docker-compose

## Running

### Boostrapping

Bootstrapping involves getting your node to synchronise with the current state of the network.
Relay and Participation Nodes use a built-in bootstrap mechanism to connect to the network and synchronize with other nodes.

Participation Nodes only require the last 1000 blocks as previously mentioned, so they can use the "catchup" snapshot to get synced faster.
Relay / Archival Nodes require the full history of the chain so they must sync all blocks from other nodes already present on the network which can take a number of days / weeks as a catchup snapshot isn't possible.
Third party snapshots can be used for Archival nodes if you trust that they haven't modified the data.

### Start/Stop/Auto


### Updating

### Monitoring

Monitoring your node is cruicial to ensuring the node is operating as expected and protecting the network.
Provided are two ways you can monitor your node using Netdata or Telegraf. 
[Monitoring](monitoring/monitoring.md)

### Troubleshooting

## Config tweaking

## Staking

## FAQ

## Developer resources

### Switching networks
