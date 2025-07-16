# Add Generic Function for Claim Sonic LP Fees

## What is it?
After adding our validation methods for claim and withdraw, we can now add Generic Functions to call the target methods. This proposal will add the method for claiming the fees from the sonic LP pools. After this function is added, a follow up proposal can be made to call the function and execute the claim call.

## Background information
Full details of the overall approach to reclaiming our Sonic controlled tokens can be found in the XB0 section of the sneed_props github repo: https://github.com/XanderBrendon/sneed_props

## Generic Function details
Validator canister is the sneed_defi canister (ok64) previously upgraded to support the required validation methods. For claim: ok64y-uiaaa-aaaag-qdcbq-cai -> validate_claim_fees_sonic_lp_position
Target canister is the Sonic sneed/icp canister: ni6i4-cqaaa-aaaak-qtsbq-cai -> claim