# Utilities

This contains useful scripts for maintaining a Cosmos SDK based node setup and comes from the [`cosmos-utils`](https://github.com/zenodeapp/cosmos-utils) repository.

This has been written by ZENODE and is licensed under the MIT-license (see [LICENSE](./LICENSE)).

## \_variables.sh

This holds all the repository-specific variables shared with most of the scripts. This makes it easier to adjust the chain-id, binary name or node directory without having to change it in a lot of different files.

## /backup

### [create.sh](./backup/create.sh)

This script creates a backup for the current node-setup, if one existed.

```
sh backup/create.sh [backup_dir_path]
```

> _[backup_dir_path]_ is optional (defaults: to a directory in the $HOME folder with a _unique_ name based on the system's current time).

## /fetch

### [peers.sh](./fetch/peers.sh)

This script fetches the (most recent) seeds and peers for the chain-id configured in the [\_variables.sh](./_variables.sh) file and adds it to the `seeds` and `persistent_peers` fields in the config.toml file residing in the node's directory.

```
sh fetch/peers.sh
```

### [state.sh](./fetch/state.sh)

This script fetches the (most recent) `genesis.json` file for the chain-id configured in the [\_variables.sh](./_variables.sh) file and places it inside of the /config-folder residing in the node's directory.

```
sh fetch/state.sh
```

## /info

### [my-peer.sh](./info/my-peer.sh)

This script will print out your peer-id: _node-id@ip-address:port_. This is useful for sharing your node with others so that they can add you as a persistent peer.

Bear in mind that the _port_ being echo'd is extracted from the _config.toml_-file. So if you start the node on a different port without explicitly stating this in the _config.toml_-file, then the outputted port may not represent the actual port this node uses.

```
sh info/my-peer.sh
```

> Add a --local flag to echo a local IP address, instead of your (public) external address.

## /key

### [create.sh](./key/create.sh)

This script creates a _new_ key (or prompts to overwrite one if the _alias_ already exists).

```
sh key/create.sh <key_alias>
```

### [import.sh](./key/import.sh)

This script imports an _existing_ key using the provided _private Ethereum key_.

```
sh key/import.sh <key_alias> <private_eth_key>
```

## /service

### [install.sh](./service/install.sh)

This script installs the daemon as a service, which will automatically start the node whenever the device reboots. See the `$SERVICE_DIR` and `$SERVICE_FILE` variables in [\_variables.sh](./_variables.sh) to see which service gets installed.

```
sh service/install.sh
```

### [uninstall.sh](./service/uninstall.sh)

This script uninstalls the daemon as a service. See the `$SERVICE_FILE` variable in [\_variables.sh](./_variables.sh) to see which service gets uninstalled.

```
sh service/uninstall.sh
```

## /tools

### [port-shifter.sh](./tools/port-shifter.sh)

This script is useful if you quickly want to replace the ports in the `client.toml`, `config.toml` and `app.toml` files. It uses the script(s) from the [`port-shifter`](https://github.com/zenodeapp/port-shifter/tree/v1.0.1) repository (`v1.0.1`). If in doubt whether this is safe, you could always check the repository to see how it works.

```
sh tools/port-shifter.sh <port_increment_value>
```

> <port_increment_value> is how much you would like to increment the value of the ports based on the default port values.

</br>

<p align="right">— ZEN</p>
<p align="right">Copyright (c) 2024 ZENODE</p>
