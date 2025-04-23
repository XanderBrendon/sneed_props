# Researching and learning about the sonic swap containers and Sneed's LP positions

- [2024-02-10, 1:07:27 PM UTC - 220 Sneed Deposited](https://dashboard.internetcomputer.org/sns/fp274-iaaaa-aaaaq-aacha-cai/transaction/5788) into the old Sonic swap canister [3xwpq-ziaaa-aaaah-qcn4a-cai](https://dashboard.internetcomputer.org/canister/3xwpq-ziaaa-aaaah-qcn4a-cai)
- [2024-12-06, 10:07:17 AM UTC - 375 Sneed Transfer](https://dashboard.internetcomputer.org/sns/fp274-iaaaa-aaaaq-aacha-cai/transaction/51548) from the old swap canister to the new swap canister [ni6i4-cqaaa-aaaak-qtsbq-cai](https://dashboard.internetcomputer.org/canister/ni6i4-cqaaa-aaaak-qtsbq-cai) for sonic's migration. New canister is still active and can be inspected and interacted with via the candid interface on the icp dashboard linked. (https://dashboard.internetcomputer.org/canister/ni6i4-cqaaa-aaaak-qtsbq-cai)
- Sneed transactions for the swap canister show active bot trading activity. (https://dashboard.internetcomputer.org/sns/fp274-iaaaa-aaaaq-aacha-cai/account/ni6i4-cqaaa-aaaak-qtsbq-cai)
- One can verify the canister ID in sonic's UI when trying to swap ICP and Sneed

![Image highlighting canister ID: ni6i4-cqaaa-aaaak-qtsbq-cai in sonic UI](images/sonicUIShowsCanisterID.png)

## Calls on the New Swap Canister
> Note: I couldn't find sonic documentation but their current swap canister seems to mirror ICPSwap's. [ICPSwap-Labs documentation](https://github.com/ICPSwap-Labs/docs/tree/main/02.SwapPool) has been helpful in understanding some of these canister calls.

Using the icp dashboard interface to interact with the [swap canister](https://dashboard.internetcomputer.org/canister/ni6i4-cqaaa-aaaak-qtsbq-cai), you can verify the following information:

1) The canister is the swap canister for ICP/Sneed
   - Call ```getTokenMeta``` (no parameters required)

        ```
        (
            record {
                token0 = vec {
                record { "name"; variant { Text = "Sneed DAO" } };
                record { "symbol"; variant { Text = "SNEED" } };
                record { "decimals"; variant { Nat = 8 : nat } };
                record { "fee"; variant { Nat = 1_000 : nat } };
                };
                token1 = vec {
                record { "name"; variant { Text = "Internet Computer" } };
                record { "symbol"; variant { Text = "ICP" } };
                record { "decimals"; variant { Nat = 8 : nat } };
                record { "fee"; variant { Nat = 10_000 : nat } };
                };
            },
        )
        ```
    - We see token0 is Sneed and token1 is ICP
2) The canister has two positions in the pool - one of which belongs to Sneed DAO
    - Call ```getUserPositionIds``` (no parameters required)
    
        ```
        (
            variant {
                ok = vec {
                record { "3cf95c2475cc3b972af1dbfa614f9c9697634fffd290b71c6035e7ffdf2e2bb5"; vec { 1 : nat } };
                record { "580deb37eb3583e5854516481bd52c2618ca73ef6ee1c2df2b556bf85c0ce5a9"; vec { 2 : nat } };
                }
            },
        )
        ```
    - We see position with id 2 is pointing to Sneed DAO's ICP Treasury account. To verify you can navigate to https://dashboard.internetcomputer.org/sns/fp274-iaaaa-aaaaq-aacha-cai to view the Sneed SNS ICP Dashboard page and click on "ICP Treasury" and check the address of the linked account and verify that it matches the response from the Sonic canister position 2.
3) The position is under control of the [Sneed Governance Container](https://dashboard.internetcomputer.org/canister/fi3zi-fyaaa-aaaaq-aachq-cai)
   - From the Sneed SNS ICP Dashboard page, scroll down to the Sneed Canisters table. The table lists a canister with the governance type and ID ```fi3zi-fyaaa-aaaaq-aachq-cai```
   - In the Sonic swap canister call ```checkOwnerOfUserPosition``` This requires two parameters, one is principal (the governance canister ID fi3...cai), the other is the position number (2). 
    
        ```
        (variant { ok = true })
        ```
    - This confirms that the Sneed governance canister owns the position and should be able to make calls on it.
4) There are 2.9 Sneed and 35 ICP in liquidity fees that position 2 has earned
    - Call ```getUserPosition(2)``` 
    
        ```
        (
            variant {
                ok = record {
                tickUpper = 26_520 : int;
                tokensOwed0 = 292_041_024 : nat;
                tokensOwed1 = 3_500_693_344 : nat;
                feeGrowthInside1LastX128 = 0 : nat;
                liquidity = 339_138_795_889 : nat;
                feeGrowthInside0LastX128 = 0 : nat;
                tickLower = 12_660 : int;
                }
            },
        )
        ```
    - From the ICPSwap-Labs documentation mentioned above, we are told:
      - liquidity is the amount of liquidity, it can be computed to the amounts of token0 and token1.
      - tickUpper is the upper tick of this position, it can be computed to the upper price of the position.
      - tickLower is the lower tick of this position, it can be computed to the lower price of the position.
      - tokensOwed0 is the token0 fee earned by the position owner.
      - tokensOwed1 is the token1 fee earned by the position owner.
    - We can expect a call to claim the fees for this position to result in 2.92041024 Sneed and 35.00693344 (at time of writing. values may adjust slightly as position is still active)
5) The Sneed controlled Sonic position contains __ Sneed and ___ ICP that we might be able to move back into more accessible forms of liquidity. Unfortunately finding those values has proved challenging and might point towards problems in Sonic's systems. 
    - Tried to again pull some information from icpswap-labs: https://github.com/ICPSwap-Labs/docs/blob/main/02.SwapPool/Liquidity/05.Getting_Amounts_For_Liquidity.md
    - Call ```metadata```
    
        ```
        (
            variant {
                ok = record {
                fee = 3_000 : nat;
                key = "hvgxa-wqaaa-aaaaq-aacia-cai_ryjl3-tyaaa-aaaaa-aaaba-cai_3000";
                sqrtPriceX96 = 298_341_050_750_672_022_733_592_503_956 : nat;
                tick = 26_519 : int;
                liquidity = 339_139_161_241 : nat;
                token0 = record { address = "hvgxa-wqaaa-aaaaq-aacia-cai"; standard = "ICRC2" };
                token1 = record { address = "ryjl3-tyaaa-aaaaa-aaaba-cai"; standard = "ICRC2" };
                maxLiquidityPerTick = 11_505_743_598_341_114_571_880_798_222_544_994 : nat;
                nextPositionId = 3 : nat;
                }
            },
        )
        ```
    - The ICPSwap-Labs doc has us gather the following information.
    - The sqrtPriceX96 value is ```298_341_050_750_672_022_733_592_503_956```
    - Our position has tickLower: ```12_660```, tickUpper: ```26_520```, liquidity: ```339_138_795_889```
    - The final step in the ICPSwap-Labs documentation was to utilize a canister to perform price calculations, but it's unclear what to pass to parameters and nothing I've tried has given reasonable results. The canister is located at https://dashboard.internetcomputer.org/canister/phr2m-oyaaa-aaaag-qjuoq-cai and the method in question is getTokenAmountByLiquidity.
    - Note that the tick value in the metadata call is only 1 away from the tickUpper on the position. It's possible there is a Sonic technical problem lurking here that may get in our way moving forward. I welcome input or ideas from the community on what I might be missing. 