# stakr-edgeware-node

This repo houses the codebase for running stakr on edgeware node. Its forked from frontier branch of edgeware-node. 

### Quickstart
If your device is clean (such as a fresh cloud VM) you can use this
script for an automated setup:
```
./setup.sh
```

The script will automatically compile the edgeware node and install all dependencies. The script also pulls the submodules including both frontier branch from `parity` as well as stakr protocol contracts from the `dtrade-contracts`
 

To start up the Edgeware node in development mode:
```
./target/release/edgeware --dev
```

To deploy the dtrade contracts on the local edgeware chain first specify `DEPLOY_PRIVATE_KEY`  and `TESTNET_DEPLOY_PRIVATE_KEY` in .env with the private key of the account that you wish to use for deploying the contracts. Also update the REACT_APP_ADDRESS_RESOLVER_ADDRESS 

```
DEPLOY_PRIVATE_KEY=99B3C12287537E38C90A9219D4CB074A89A16E9CDB20BF85728EBD97C343E342
TESTNET_DEPLOY_PRIVATE_KEY=99B3C12287537E38C90A9219D4CB074A89A16E9CDB20BF85728EBD97C343E342
```

Update the `ProviderUrl` with the ip:port on which the edgeware-node is running. By default edgeware node runs on 9933 port so kindly set the variable to `http://127.0.0.1:9933` else you will receive the following error: `Error: Invalid JSON RPC response: ""`


Once everything is setup run:
```
cd vendor/dtrade-contracts
yarn install 
node scripts/deploy deploy -n local -d scripts/deploy/chain_config/local -g 8
```
