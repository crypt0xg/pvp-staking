<h1 align="center">PVP Staking: A Contract for Unlocked and Locked Staking</h1>

<p align="center">
  <img src="https://img.shields.io/badge/-Solana-000000?style=flat-square&logo=solana&logoColor=06AFF2">
  <img src="https://img.shields.io/badge/-Rust-000000?style=flat-square&logo=rust&logoColor=white">
  <img src="https://img.shields.io/badge/-Typescript-F7DF1E?style=flat-square&logo=typescript&logoColor=black">
  <img src="https://img.shields.io/badge/-VSCode-007ACC?style=flat-square&logo=visual-studio-code&logoColor=white">
</p>

## Overview
`pvp_staking` utilizes the Anchor framework to facilitate staking operations on the Solana network, offering both standard and locked staking options with reward enhancements through multipliers.

## Modules

- `context`: Defines the context data structures for transaction instructions.
- `error`: Custom error codes for handling exceptions in contract operations.
- `state`: Manages stateful components of the staking pools and user stakes.
- `utils`: Utility functions to support various operations like state updates and calculations.


## Functions
List of all the functions used to interact with the program

### Admin Operations

- `initialize`: Sets up a new staking pool with required parameters like reward rate and initializes time tracking.
- `initialize_locked`: Configures locked staking pools with specified serving periods and associated multipliers.
- `update_admin`: Allows updating the administrator of the staking pool.
- `update_reward_rate`: Changes the reward rate per second for the pool.
- `add_multiplier`: Adds multiplier settings to a specified locked pool period.

### User Operations

- `deposit`: Allows users to deposit tokens into the staking pool and updates the internal accounting to reflect the new state.
- `deposit_locked`: Similar to deposit, but for locked pools with specified multipliers affecting the staked amount.
- `withdraw`: Withdraw tokens from the staking pool, adjusting the internal state accordingly.
- `withdraw_locked`: Withdraw tokens from a locked pool assuming the locking period has passed.
- `claim_reward`: Allows users to claim their accumulated rewards based on their staked tokens.

## Error Codes
The contract uses custom error codes defined in the error::ErrorCodes module to manage exceptions related to invalid operations and authorization issues.

## State Management
The contract maintains the state of the staking pools and user stakes using the following structs

- `Pool`: Tracks the main staking pool details.
- `PoolLocked`: Manages settings for locked pools with multipliers.
- `StakeAccount`: Records individual user stakes in the flexible pool.
- `StakeLocked`: Manages individual locked stakes for users.

## Setup
Note - It is assumed that you have solana/rust/anchor installed already, otherwise <a href="https://www.anchor-lang.com/docs/installation">Install Anchor</a>
- `Change wallet`: Change the `username` in the `Anchor.toml's wallet field` to your username.
- `Configure the cluster`: Change the cluster in the `Anchor.toml` to `Mainnet`, `Testnet`, `Devnet` or `Localnet`.

## Run on local
1. `Anchor localnet` - Start the localnet.
2. `Anchor build` - Build the program
3. `Anchor keys list` - Get the program address after build, then change the address in `Anchor.toml` and `declare_id!` of `lib.rs`.
4. `Anchor build` - Rebuild the program with updated program id.
5. `Anchor deploy` - Deploy the program.
6. `Anchor run test` - Test the testing scripts with the updated program.
