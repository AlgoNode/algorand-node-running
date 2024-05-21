# Updating your Algorand node

One click nodes have their own upgrade instructions, please follow them to get your node up to date.

## Ubuntu/Debian official installation upgrade

The following set of commands refreshes your system package list and tries to upgrade only the Algorand node.

```bash
sudo apt update && sudo apt install --only-upgrade algorand
```

* node will restart automatically but you can force it with `systemctl restart algorand`
* same command works on for all AVM networks/chains and node types
* sometimes node requires database migration during restart and it will appear dead to several minutes

## Troubleshooting the upgrade

### Node is syncing

When `goal node status` shows `Sync Time` greater then `0.0s`, eg :

```bash
sudo goal node status
# Last committed block: 39035771
# Time since last block: 0.0s
# Sync Time: 2.5s
```
 
Your node is catchichg up to the tip of the blockchain - give it some time.
You can watch the progress with updates every second using:
```bash
sudo goal node status -w 1000
```

Press Ctrl+C to stop the watch. 

### Node is stuck at unsupported protocol

TBD

### Node is not there

When `goal node status` shows responds with `Cannot contact Algorand node: open /var/lib/algorand/algod.net: no such file or directory`

Check if node process is running, it might just be doing database migration before it becomes fully available:
```bash
ps -U algorand
#  PID TTY          TIME CMD
#13884 ?        03:35:59 algod
```

If the list does not show algod process it means that node has not started and you need to consult the troubleshooting guide.

Othewise wait for the node to do its stuff. You can monitor the progress with this command:

```bash
sudo journalctl -fu algorand
```
