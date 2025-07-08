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
    - Status: Preparing
  - [ ] Add claim as a callable generic function
  - [ ] Call claim function
  - Verify Results
- Withdraw funds for claimed fees to verify token access after withdrawal
  - [X] Update Sneed defi canister with new code to validate withdraw parameters
  - [ ] Add withdraw as a callable generic function
  - [ ] Call withdraw

> Note: Some of these stages could be done in tandem (e.g. updating defi canister with validate for both claim and withdraw), but steps are broken up to ensure any mistakes are only made once and with small impact. 

## Stage 2
Goal: Plan remaining required proposals to pull full liquidity position from Sonic and move to an ICPSwap position. Explore swap position options.

- Discuss planned ICPSwap position parameters
- [ ] Submit Motion Proposal to continue the process with additional details for next steps

## Stage 3
Goal: Withdraw and gain DAO access to tokens in Sonic LP pool. Make final preparations for ICPSwap position changes.

- Withdraw full LP position from Sonic
  - [ ] PlaceHolder for Additional proposals for Stage 3 Work (To be replaced before Stage 2 passes)
- Prepare for ICPSwap LP addition (code changes and such required to happen before Stage 4)
  - [ ] PlaceHolder for Additional proposals for Stage 3 Work (To be replaced before Stage 2 passes)
- Define finalized ICPSwap position parameters
  - [ ] Depending on stage 2 work might or might not need additional motion proposal for community approval.

## Stage 4
Goal: Complete XB0 goal of moving tokens out of Sonic pool and into ICPSwap pool
- [ ] Create ICPSwap position or increase existing position depending on Stage 3 feedback/results