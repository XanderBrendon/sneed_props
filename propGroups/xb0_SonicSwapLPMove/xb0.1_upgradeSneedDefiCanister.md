# Upgrade proposal to push new code to the Sneed Defi (ok64) canister

## What is it?
In order to manage Sonic liquidity positions, our Sneed Defi canister needs to be able to talk to the Sonic canister. In order to trigger calls from our canister, we need a way to validate the inputs to the methods we're calling. This code change adds the validation methods that will enable us to create the generic functions we need to call to manage our Sonic positions.

## Background information
Full details of the overall approach to reclaiming our Sonic controlled tokens can be found in the XB0 section of the sneed_props github repo: https://github.com/XanderBrendon/sneed_props

## How to verify
1. Ensure you have installed and can use dfx
2. Clone the sneed_defi canister code from github: https://github.com/icsneed/sneed_defi
3. run ```dfx build --ic``` to build the project for the ic network
4. Find the produced wasm file (generally at .dfx\ic\canisters\sneed_defi\sneed_defi.wasm)
5. Create a SHA256 hash of the file using your preferred tooling (e.g. in Powershell ```Get-FileHash -Path sneed_defi.wasm -Algorithm SHA256```)
6. Compare against the one listed in the proposal
