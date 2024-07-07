# Bootstapping
Bootstrapping involves getting your node to synchronise with the current state of the network.
Relay and Participation Nodes use a built-in bootstrap mechanism to connect to the network and synchronise with other nodes.

Participation Nodes only require the last 1000 blocks, they can use a "catch-up" snapshot to get up to date much faster.

Relay / Archival Nodes require the full history of the chain so they must sync all blocks from other nodes already present on the network which can take a number of days / weeks as a catchup snapshot isn't possible.

That said however, third parties can provide snapshots of their archival nodes for you to use, however there is some risk in this approach as you must trust the third party to ensure they haven't modified the blockchain data that is being supplied.
