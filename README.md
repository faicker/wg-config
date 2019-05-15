This is a simple wireguard VPN user management script using on VPN server.
Client config file and qrcode are generated.

### dependency

* wireguard
* qrencode

### config
The wireguard default config directory is /etc/wireguard.

The script config file is wg.def, create and edit it according to wg.def.sample.

You can generate the public key and private key with command `wg genkey | tee prikey | wg pubkey > pubkey`.

### usage

Running as root.

#### init wireguard server

```bash
./user.sh -i
```

#### add a user

```bash
./user.sh -a alice
```

This will generate a client conf and qrcode in users directory which name is alice
and add alice to the wg server config.

client will route all traffic to server.

```bash
./user.sh -a alice -r
```

This will disable default route change. Route traffic Manually.

#### delete a user

```bash
./user.sh -d alice
```
This will delete the alice directory and delete alice from the wg server config.

#### clear all

```bash
./user.sh -c
```
