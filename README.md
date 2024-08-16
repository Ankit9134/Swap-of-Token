# TokenSwap

Token swap smart contract that swaps two ERC20 tokens and takes a fee

[![](https://img.shields.io/badge/Donate-yellow?style=for-the-badge)](https://www.patreon.com/free_college)

# 
![TokenSwap](https://user-images.githubusercontent.com/24751547/140658739-c6c999c0-e3c8-4250-a34c-d755ea9801f9.png)
Here’s a detailed explanation of how you can create a token swap smart contract that swaps two ERC20 tokens and takes a fee:

### Overview

A token swap smart contract allows users to exchange one ERC20 token for another. In this scenario, the contract will also take a fee from each transaction, which can be sent to a specific address (such as the contract owner or a designated fee recipient). This contract will involve the following key components:

1. **ERC20 Token Interface**: The contract will interact with two different ERC20 tokens.
2. **Fee Structure**: A fee is calculated as a percentage of the tokens being swapped.
3. **Swap Function**: The main function that handles the swapping of tokens between two parties and deducts the fee.
4. **Security**: Ensures safe handling of tokens and prevents common smart contract vulnerabilities.

### Contract Structure

1. **Imports and Setup**
   - Import the `IERC20` interface from OpenZeppelin to interact with ERC20 tokens.
   - Import `SafeERC20` for safe transfer operations.

2. **State Variables**
   - `token1` and `token2`: These will store the addresses of the ERC20 tokens involved in the swap.
   - `feeRecipient`: The address that will receive the fees.
   - `feePercentage`: The fee percentage in basis points (e.g., 30 for 0.3%).

3. **Constructor**
   - Initializes the contract with the addresses of `token1`, `token2`, the `feeRecipient`, and the `feePercentage`.

4. **Swap Function**
   - Takes the amount of `token1` from the user.
   - Calculates the fee and transfers it to the `feeRecipient`.
   - Calculates the amount of `token2` that the user should receive (considering the fee).
   - Transfers the equivalent amount of `token2` to the user.

5. **Helper Functions**
   - A function to calculate the equivalent amount of `token2` based on the swap logic (e.g., a 1:1 ratio for simplicity).
   - Other utility functions like `setFeePercentage` or `updateFeeRecipient` for contract management.


### Explanation:

1. **Fee Calculation**: 
   - The fee is calculated as a percentage of the tokens being swapped.
   - The fee is deducted from the user’s input amount and sent to the fee recipient.

2. **Token Transfer**:
   - The `SafeERC20` library ensures that token transfers are secure and revert if there are any issues.
   - The swap function first transfers the `token1` (after fee deduction) from the user to the contract.
   - Then, it transfers the equivalent amount of `token2` from the contract to the user.

3. **Customization**:
   - The contract allows the fee recipient and fee percentage to be updated through specific functions, ensuring flexibility.

4. **Security Considerations**:
   - This basic implementation assumes a 1:1 swap ratio. In a real-world scenario, you would need to incorporate more complex logic to handle different exchange rates.
   - Make sure to thoroughly test the contract and consider potential edge cases, like ensuring sufficient liquidity or handling reentrancy attacks.

### Use Cases:

- **Decentralized Exchanges (DEXs)**: This smart contract could be a core component in a DEX where users swap different ERC20 tokens.
- **Token Migration**: This could be used for migrating users from one token to another, with an optional fee.
- **Fee-Based Swaps**: Projects could use this model to offer token swap services and generate revenue through the fee.

This contract provides a foundational structure that can be expanded with additional features depending on the specific use case.

# Test

Open Ganache and run the following commands :

```
truffle migrate
truffle test
```

- in case you want to publish to the testnet dont Forget to add .secret file and put the seed of metamask account in it. for more informations : https://docs.binance.org/smart-chain/developer/deploy/truffle.html

# Run

you need to modify the Admin address in App.js to get the Admin panel and charge the TokenSwap Smart contract and then run the following comand

```
npm install
cd Client
yarn install
yarn start
```

- add the Admin account in your wallet, the TokenSwap will detect changes and redirect you to the Admin component
  you need to charge the smart Contract with Tokens XYZ and ABC and set the Ratio and the Fee
- make sure to configure Metamask to whichever network you migrated to when you ran the `truffle migarte ` command,this repository is already configured to connect to the testnet.
