# Add Generic Function for Withdraw From Sonic

## What is it?
We've claimed our sonic fees and they are now available for withdrawal. This will add a custom function for us to call the withdraw method on Sonic and receive our available tokens. Sneed = 8.56182307 ICP = 40.69574490. We will need to call the withdraw method twice - once for each token type.

## Background information
Full details of the overall approach to reclaiming our Sonic controlled tokens can be found in the XB0 section of the sneed_props github repo: https://github.com/XanderBrendon/sneed_props

## Generic Function details
Validator canister is the sneed_defi canister (ok64) previously upgraded to support the required validation methods. For withdraw: ok64y-uiaaa-aaaag-qdcbq-cai -> validate_withdraw_sonic_lp
Target canister is the Sonic sneed/icp canister: ni6i4-cqaaa-aaaak-qtsbq-cai -> withdraw