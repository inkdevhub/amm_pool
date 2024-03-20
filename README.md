# AMM Pool - Smart Contract for Automated Market Making

This repository contains the smart contract code for an Automated Market Making (AMM) pool. The AMM pool facilitates decentralized token exchange between supported tokens.

The smart contract relies on [PSP22 implementation](https://github.com/Cardinal-Cryptography/PSP22).

This contract is based on Balancer multi asset LP design and all formulas are taken from the [Balancer's whitepaper](https://balancer.fi/whitepaper.pdf)

## Features:

- Swap functionality to exchange tokens within the pool.
- Liquidity provisioning for users to contribute to the pool and earn rewards. (Can be added later)
- Fee collection on swaps to incentivize liquidity providers. (Can be added later)
- Permissioned withdrawal for authorized accounts to remove liquidity.

## Getting Started

### Prerequisites
    - Rust programming language with tools installed ([Rust compiler, Cargo package manager](https://doc.rust-lang.org/cargo/getting-started/installation.html))
    - Cargo contract (https://github.com/paritytech/cargo-contract)
    - Familiarity with smart contract development principles

### Clone the Repository

```Bash
git clone https://https://github.com/inkdevhub/amm_pool.git
```
### Build

```Bash
cd amm_pool
cargo contract build -release
```

### Test

```Bash
cargo test
```

## Usage

### Swapping Tokens:

Use the `swap(token_in, token_out, amount_token_in, min_amount_token_out)` function to exchange tokens within the pool, where:
- `token_in`: The token type being provided for the swap (PSP22 token address).
- `token_out`: The token type desired in return for the swap (PSP22 token address).
- `amount_token_in`: The amount of token_in the user is willing to spend (U128 integer representing the amount).
- `min_amount_token_out`: The minimum amount of `token_out` the user expects to receive (U128 integer representing the amount).

### Liquidity Management (For Authorized Accounts):

Currently, the provided code doesn't include functionality for liquidity provisioning. However, you can implement features like:
- A function to deposit tokens into the pool to become a liquidity provider.
- A function for liquidity providers to withdraw their share of the pool's reserves.
- Permissions and Configuration (For Authorized Accounts):

The `is_authorized(account)` function can be used internally to verify if an account has permission to perform specific actions (like withdrawals).
The `set_swap_fee_percentage(swap_fee_percentage)` function allows authorized accounts to adjust the swap fee percentage (if implemented).

Important Notes:
- Ensure the calling account has granted sufficient allowance to the AMM contract to transfer the specified amount_token_in before calling the swap function.
- Only authorized accounts (typically the contract owner) can perform actions like withdrawals and fee adjustments.

### Disclaimer:
This code example is for educational purposes only and should not be used in production environments without proper testing, security audits, and legal considerations.