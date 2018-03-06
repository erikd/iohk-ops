[![Build status](https://badge.buildkite.com/5645abfe1411086f06a4d8cee1e3bbbbba9fb9318738f1fdb1.svg)](https://buildkite.com/input-output-hk/iohk-ops?theme=solarized)

Collection of tooling and automation to deploy IOHK infrastructure.

### Structure

- `deployments` - includes all NixOps deployments controlled via `.hs` scripts
- `modules` - NixOS modules
- `lib.nix` - wraps upstream `<nixpkgs/lib.nix>` with our common functions
- `scripts` - has bash scripts not converted to Haskell/Turtle into Cardano.hs yet
- `default.nix` - is a collection of Haskell packages
- `static` includes files using in deployments
- `jobsets` is used by Hydra CI


### Usage

   $(nix-build -A iohk-ops)/bin/iohk-ops --help


### Getting SSH access

1. Append https://github.com/input-output-hk/iohk-ops/blob/master/lib.nix#L83 and submit a PR.
2. Wait until the DevOps team deploys the infrastructure cluster.

### edge nodes - watch log
# 10 nodes "edgenode-1", each has 10 wallets "cardano-node-[1-10]"
export NIXOPS_DEPLOYMENT=edgenodes-cluster
nixops ssh edgenode-1

journalctl -f -u cardano-node-1

