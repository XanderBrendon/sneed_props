# Call Generic Function to withdraw Sneed from Sonic canister

## What is it?
We've added the withdraw function and called claim. We have 856_182_307 (8.5) Sneed available to withdraw. This call to withdraw will transfer the Sneed back to the DAO's wallet.

## Background information
Full details of the overall approach to reclaiming our Sonic controlled tokens can be found in the XB0 section of the sneed_props github repo: https://github.com/XanderBrendon/sneed_props

## Parameter Details
Withdraw takes 3 parameters. For the Sneed withdrawal the values will be:

- Fee (nat): 1_000 (Sneed token fee)
- Token (text): hvgxa-wqaaa-aaaaq-aacia-cai (Sneed ledger)
- Amount (nat): 856_181_307 (total available sneed for withdrawal minus fee)