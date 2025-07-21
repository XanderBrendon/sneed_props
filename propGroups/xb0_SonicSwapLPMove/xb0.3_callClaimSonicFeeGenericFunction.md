# Call Generic Function for Claim Sonic LP Fees

## What is it?
After adding the custom function to call the sonic claim method, we now need to execute it to make our tokens avialable for withdrawing. The next step will be to add a withdraw custom function and call it to extract the tokens.

## Background information
Full details of the overall approach to reclaiming our Sonic controlled tokens can be found in the XB0 section of the sneed_props github repo: https://github.com/XanderBrendon/sneed_props

## Parameter Details
Position 2 belongs to the DAO as can be confirmed by calling checkOwnerOfUserPosition on the swap canister https://dashboard.internetcomputer.org/canister/ni6i4-cqaaa-aaaak-qtsbq-cai