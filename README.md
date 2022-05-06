# Loyal Networks

This repository contains network information for the various Loyal networks.

In general, there will be three networks available at any given time:

| Network            | Status             | Version     | Description                             |
| ------------------ | ------------------ | ----------- | --------------------------------------- |
| [mainnet](mainnet) | :heavy_check_mark: | v0.16.3     | Loyal Network mainnet network.          |
| [testnet](testnet) | :construction:     | v0.14.1     | Testnet of the current mainnet version. |

Each network has a corresponding directory (linked to above) containing network information.
Each directory includes, at a minimum:

| File             | Description                                                                           |
| ---------------- | ------------------------------------------------------------------------------------- |
| `version.txt`    | The [Loyal](//github.com/LoyalLabs/loyal) version used to participate in the network. |
| `chain-id.txt`   | The "chain-id" of the network.                                                        |
| `genesis.json`   | The genesis file for the network                                                      |
| `seed-nodes.txt` | A list of seed node addresses for the network.                                        |

The following files may also be present:

| File             | Description                                         |
| ---------------- | --------------------------------------------------- |
| `peer-nodes.txt` | A list of peer node addresses for the network.      |
| `rpc-nodes.txt`  | A list of RPC node addresses for the network.       |
| `api-nodes.txt`  | A list of API (LCD) node addresses for the network. |
| `faucet-url.txt` | The url of a faucet server for the network.         |

## Usage

The information in this repo may be used to automate tasks when deploying or configuring
[loyal](//github.com/LoyalLabs/loyal) software.

The format is standardized across the networks so that you can use the same method
to fetch the information for all of them - just change the base URL

```sh
LOYAL_NET_BASE=https://raw.githubusercontent.com/LoyalLabs/net/master

##
#  Use _one_ of the following:
##

# mainnet
LOYAL_NET="$LOYAL_NET_BASE/mainnet"

# testnet
LOYAL_NET="$LOYAL_NET_BASE/testnet"

# edgenet
LOYAL_NET="$LOYAL_NET_BASE/edgenet"
```

## Fetching Information

### Version

```sh
LOYAL_VERSION="$(curl -s "$LOYAL_NET/version.txt")"
```

### Chain ID

```sh
LOYAL_CHAIN_ID="$(curl -s "$LOYAL_NET/chain-id.txt")"
```

### Genesis

```sh
curl -s "$LOYAL_NET/genesis.json" > genesis.json
```

### Seed Nodes

```sh
curl -s "$LOYAL_NET/seed-nodes.txt" | paste -d, -s
```

### Peer Nodes

```sh
curl -s "$LOYAL_NET/peer-nodes.txt" | paste -d, -s
```

### RPC Node

Print a random RPC endpoint

```sh
curl -s "$LOYAL_NET/rpc-nodes.txt" | shuf -n 1
```

### API Node

Print a random API endpoint

```sh
curl -s "$LOYAL_NET/api-nodes.txt" | shuf -n 1
```
