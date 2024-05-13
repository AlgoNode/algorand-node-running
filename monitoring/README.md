# Keeping Your Algorand Node Healthy

Participation Nodes play a crucial role in verifying transactions and securing the network. By running a node, you actively participate in the consensus process, ensuring the network remains decentralized and resistant to manipulation.

A larger and more geographically diverse network of nodes makes it harder for any single entity to gain control. Your contribution helps maintain a robust and secure network.


## System Monitoring

System Monitoring ensures the operating system and underlying hardware of your node is working as intended. This includes system metrics such as CPU, memory, disk and network utilisation.
 

## Node Monitoring

Node Monitoring ensures your node daemon is online, synced with the network, and participating in consensus correctly.


# Monitoring Setup

There are two examples listed in this guide for monitoring your node.

- First option is using `Netdata Cloud`, this method is quicker and easier to get up and running for quick visualisation of your system and node metrics. No additional servers are required to implement this. Thanks to SilentRhetoric for this guide.

- Second option is using `InfluxDB` as a time series database, `Telefraf` as a polling engine and `Grafana` as the graphing front end. There is a lot more involved in setting this up compared to Netdata, however you can build out custom dashboards to suite your requirements. An additional server is required for this option as we do not recommend running it on the same server as your node.

Both options require you to <strong>`Enable Node Metrics`</strong>.


### Enable node metrics

See https://developer.algorand.org/docs/run-a-node/reference/config/

In your node's data directory, use the `config.json.example` file to create a config file (if you don't have one already)
> cp config.json.example config.json.

Enable node metrics
>diagcfg metric enable.

Verify status
> diagcfg metric status.

### Select Monitoring Option

The following guides use Ubuntu 22.04 LTS Server for the OS, and assumes you already have a participation node operational.

[Option 1: Netdata Cloud](netdata.md)

[Option 2: InfluxDB, Telegraf, Grafana](influx.md)


# Alerting Setup

Once you have monitoring setup, it is highly recommended you look at configuring alerting rules.

This ensures you are made aware of any issues as soon as possible. In these examples, this can be done using Netdata or Influx/Grafana depending on your choice.

Another option is to use Allo Alerts, you don't need a server or any monitoring setup.
You can provide the address you want to monitor, and preferred contact method, they'll handle the rest.

[Alerting Guides](alerting.md)
