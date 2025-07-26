# Call Generic Function to withdraw ICP from Sonic canister

## What is it?
We've added the withdraw function and called claim. We have 4_069_574_490 (40.6) ICP available to withdraw. This call to withdraw will transfer the ICP back to the DAO's wallet.

## Background information
Full details of the overall approach to reclaiming our Sonic controlled tokens can be found in the XB0 section of the sneed_props github repo: https://github.com/XanderBrendon/sneed_props

## Parameter Details
Withdraw takes 3 parameters. For the ICP withdrawal the values will be:

- Fee (nat): 10_000 (ICP token fee)
- Token (text): ryjl3-tyaaa-aaaaa-aaaba-cai (ICP ledger)
- Amount (nat): 4_069_564_490 (total available ICP for withdrawal minus fee)