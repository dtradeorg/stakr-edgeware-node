![Frame 362](https://user-images.githubusercontent.com/74007432/101769771-e8ff0d00-3b00-11eb-8e46-339eec3095ff.png)

<p align="center"

<!---[![GitHub Workflow Status](https://img.shields.io/github/workflow/status/AcalaNetwork/Acala/Test?label=Actions&logo=github)](https://github.com/dtradeorg/stakr-edgeware-node/actions/new)
[![GitHub tag (latest by date)](https://img.shields.io/github/v/tag/AcalaNetwork/Acala)](https://github.com/AcalaNetwork/Acala/tags)
[![Substrate version](https://img.shields.io/badge/Substrate-2.0.0-brightgreen?logo=Parity%20Substrate)](https://substrate.dev/)
[![GitHub license](https://img.shields.io/github/license/dtradeorg/stakr-edgeware-node?color=gree)](https://github.com/dtradeorg/stakr-edgeware-node/blob/edgeware-frontier/LICENSE) --->
[![Twitter URL](https://img.shields.io/twitter/url?style=social&url=https%3A%2F%2Ftwitter.com%2FAcalaNetwork)](https://twitter.com/dtradeorg)
[![Discord](https://img.shields.io/badge/Discord-gray?logo=discord)](https://discord.com/invite/KwCFQz3zTp)
[![Medium](https://img.shields.io/badge/Medium-gray?logo=medium)](https://medium.com/dtrade)

</p>

# Contracts-deployment-edgeware-node

This repo houses the codebase for running the multi-collateral staking platform & synthetic asset exchange on the edgeware node.

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


Once everything is setup run the following to deploy stakr contracts on local chain:
```
cd vendor/dtrade-contracts
yarn install 
node scripts/deploy deploy -n local -d scripts/deploy/chain_config/local -g 8
```
