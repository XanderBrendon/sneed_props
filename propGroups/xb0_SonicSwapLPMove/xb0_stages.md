# Stages
Each Task box is a Sneed DAO proposal that will need to be passed. Some later stages may need to be broken into additional individual proposals.

## Stage 0
- Initial research on interacting with Sonic canisters and the state of the Sonic swap canister holding Sneed/ICP
  - Status: Complete
  - Results under research and learning - [sonic canisters](/propGroups/xb0_SonicSwapLPMove/research_and_learning/sonic_canisters.md)
- [X] Submit Motion Proposal to begin XB0 with Plan of Action for Sneed DAO Consideration
  - [Proposal Details (xb0.0_motionToStart.md)](xb0.0_motionToStart.md)
  - Status: [Executed](https://nns.ic0.app/proposal/?u=fp274-iaaaa-aaaaq-aacha-cai&proposal=266)

> Useful reading for understanding this process https://internetcomputer.org/docs/building-apps/governing-apps/managing/making-proposals#generic-proposals

## Stage 1

Goal: Claim and gain DAO access to Sonic LP fees as test of capability of access to funds.

- Attempt to claim LP fees from Sonic into the pool to verify pool interaction.
  - [X] Update Sneed defi canister with new code to validate claim parameters (preperatory step for adding generic function)
    - [Proposal Details (xb0.1_upgradeSneedDefiCanister.md)](xb0.1_upgradeSneedDefiCanister.md)
    - Status: [Executed](https://nns.ic0.app/proposal/?u=fp274-iaaaa-aaaaq-aacha-cai&proposal=275)
  - [X] Add claim as a callable generic function
    - [Proposal Details (xb0.2_addClaimSonicFeeGenericFunction.md)](xb0.2_addClaimSonicFeeGenericFunction.md)
    - Status: [Executed](https://nns.ic0.app/proposal/?u=fp274-iaaaa-aaaaq-aacha-cai&proposal=301)
  - [X] Call claim function
    - [Proposal Details (xb0.3_callClaimSonicFeeGenericFunction.md)](xb0.3_callClaimSonicFeeGenericFunction.md)
    - Status: [Executed](https://nns.ic0.app/proposal/?u=fp274-iaaaa-aaaaq-aacha-cai&proposal=302)
  - [X] Verify Results
    - Sonic canister has increased unused balance for the principal and decreased claimable tokens for the position, indicating success.
- Withdraw funds for claimed fees to verify token access after withdrawal
  - [X] Update Sneed defi canister with new code to validate withdraw parameters
  - [ ] Add withdraw as a callable generic function
    - [Proposal Details (xb0.4_addWithdrawFromSonicGenericFunction.md)](xb0.4_addWithdrawFromSonicGenericFunction.md)
    - Status: [Open for voting](https://nns.ic0.app/proposal/?u=fp274-iaaaa-aaaaq-aacha-cai&proposal=303)
  - [ ] Call withdraw for Sneed
    - [Proposal Details (xb0.5_callWithdrawSneedFromSonic.md)](xb0.5_callWithdrawSneedFromSonic.md)
    - Status: [Waiting on 303](https://nns.ic0.app/proposal/?u=fp274-iaaaa-aaaaq-aacha-cai&proposal=303)
  - [ ] Call withdraw for ICP
    - [Proposal Details (xb0.6_callWithdrawICPFromSonic.md)](xb0.6_callWithdrawICPFromSonic.md)
    - Status: [Waiting on 303](https://nns.ic0.app/proposal/?u=fp274-iaaaa-aaaaq-aacha-cai&proposal=303)

> Note: Some of these stages could be done in tandem (e.g. updating defi canister with validate for both claim and withdraw), but steps are broken up to ensure any mistakes are only made once and with small impact. 

## Stage 2
Revised plan:
  - In order to simplify the completion of the sonic reclamation process, this proposal group will no longer seek to utilize most of the funds reclaimed and instead will focus on being able to withdraw those funds to the DAO treasury.
  - Fees generated from the sonic positions will be distributed via the RLL mechanism as this is revenue the DAO has generated.
  
Original plan (no longer part of this proposal group):
>  Goal: Plan remaining required proposals to pull full liquidity position from Sonic and move to an ICPSwap position. Explore swap position options.
> 
> - Discuss planned ICPSwap position parameters
> - [ ] Submit Motion Proposal to continue the process with additional details for next steps

*Subsequent stages have also been updated to reduce scope of defined goals*

## Stage 3
Goal: Withdraw and gain DAO access to tokens in Sonic LP pool.

- Withdraw full LP position from Sonic
  - [ ] Add validation method for decrease liquidity
  - [ ] Deploy ok64 canister with new validation method
  - [ ] Add generic function to call decrease lp
  - [ ] Call decrease lp function
  - [ ] Call withdraw function for Sneed
  - [ ] Call withdraw function for ICP
