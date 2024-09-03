# Bootstapping
Bootstrapping involves getting your node to synchronise with the current state of the network.
Relay and Participation Nodes use a built-in bootstrap mechanism to connect to the network and synchronise with other nodes.

Participation Nodes only require the last 1000 blocks, they can use a "catch-up" snapshot to get up to date much faster.
Relay / Archival Nodes require the full history of the chain so they must sync all blocks from other nodes already present on the network which can take a number of days / weeks as a catchup snapshot isn't possible.
That said however, third parties can provide snapshots of their archival nodes for you to use, however there is some risk in this approach as you must trust the third party to ensure they haven't modified the blockchain data that is being supplied.

You can check the status by running goal node status and specifying the directory.

```
goal node status -d /var/lib/algorand/
```

Once the sync time reaches 0.0s, and your last commited block matches the current block on the network (Blockchain Explorers show this value such as allo.info) your node is in sync and ready.

```
node:~$ goal node status -d /var/lib/algorand/
Last committed block: 40707939
Time since last block: 2.8s
Sync Time: 0.0s
Last consensus protocol: https://github.com/algorandfoundation/specs/tree/925a46433742afb0b51bb939354bd907fa88bf95
Next consensus protocol: https://github.com/algorandfoundation/specs/tree/925a46433742afb0b51bb939354bd907fa88bf95
Round for next consensus protocol: 40707940
Next consensus protocol supported: true
Last Catchpoint: 
Genesis ID: mainnet-v1.0
Genesis hash: wGHE2Pwdvd7S12BL5FaOP20EGYesN73ktiC1qzkkit8=
```
