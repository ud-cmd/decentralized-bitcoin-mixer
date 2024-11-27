# Decentralized Bitcoin Mixer Smart Contract

## Overview

This Clarity smart contract provides a decentralized Bitcoin mixing service designed to enhance transaction privacy on the Stacks blockchain. The mixer allows users to deposit, withdraw, and participate in mixing pools, with robust security and privacy features.

## Features

### Key Functionalities

- **Deposit**: Securely deposit Bitcoin into the mixer
- **Withdrawal**: Withdraw funds from the mixer
- **Mixer Pools**: Create and join mixer pools for enhanced privacy
- **Transaction Limits**: Daily transaction limits to prevent abuse
- **Emergency Pause**: Contract owner can pause operations in critical situations

### Security Mechanisms

- User balance tracking
- Daily transaction limits
- Maximum transaction amount constraints
- Pool participant limits
- Emergency contract pause functionality

## Contract Constants

### Transaction Limits

- **Maximum Daily Limit**: 100 BTC (100,000,000,000 satoshis)
- **Maximum Pool Participants**: 10
- **Maximum Transaction Amount**: 10,000 BTC (10,000,000,000,000 satoshis)
- **Minimum Pool Contribution**: 0.001 BTC (100,000 satoshis)
- **Mixing Fee**: 1% (100 basis points)

## Error Handling

The contract includes comprehensive error handling with specific error codes:

- `ERR-NOT-AUTHORIZED` (u1000): Unauthorized access attempt
- `ERR-INVALID-AMOUNT` (u1001): Invalid transaction amount
- `ERR-INSUFFICIENT-BALANCE` (u1002): Insufficient user balance
- `ERR-CONTRACT-NOT-INITIALIZED` (u1003): Contract not initialized
- `ERR-ALREADY-INITIALIZED` (u1004): Contract already initialized
- `ERR-POOL-FULL` (u1005): Mixer pool has reached maximum participants
- `ERR-DAILY-LIMIT-EXCEEDED` (u1006): Daily transaction limit exceeded
- `ERR-INVALID-POOL` (u1007): Invalid mixer pool
- `ERR-DUPLICATE-PARTICIPANT` (u1008): Duplicate pool participant

## Public Functions

### Initialization

- `initialize()`: Initialize the contract

### User Actions

- `deposit(amount)`: Deposit funds into the mixer
- `withdraw(amount)`: Withdraw funds from the mixer
- `create-mixer-pool(pool-id, initial-amount)`: Create a new mixer pool
- `join-mixer-pool(pool-id, amount)`: Join an existing mixer pool

### Contract Management

- `toggle-contract-pause()`: Pause or unpause the contract (owner only)

## Read-Only Functions

- `get-balance(user)`: Check user's current balance
- `get-daily-limit-remaining(user)`: Check remaining daily transaction limit
- `get-contract-status()`: Get current contract initialization and pause status

## Usage Example

```clarity
;; Initialize the contract
(initialize)

;; Deposit funds
(deposit u1000000) ;; 0.01 BTC

;; Create a mixer pool
(create-mixer-pool u1 u500000) ;; Pool ID 1, initial amount 0.005 BTC

;; Join a mixer pool
(join-mixer-pool u1 u250000) ;; Join pool 1 with 0.0025 BTC
```

## Security Considerations

- Only the contract owner can pause/unpause the contract
- Daily transaction limits prevent potential abuse
- Pools have participant and amount limits
- Validates all inputs before processing transactions

## Deployment Requirements

- Stacks blockchain
- Clarity smart contract support
- Minimum Stacks wallet balance for transaction fees
