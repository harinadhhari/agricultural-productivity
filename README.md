# Agricultural Productivity 
## Overview

This Solidity smart contract, named AgriculturalProductivity, is designed to manage and track the harvest of agricultural products on the Ethereum blockchain. It includes functions to record harvest amounts for individual farmers and process payouts based on the total harvested quantity.

## Features

### Harvest Recording

Farmers can report their harvest by calling the `recordHarvest` function. The function ensures the validity of the reported amount, rejecting values exceeding the maximum limit of 1000. Harvested amounts are associated with the farmer's address and aggregated to calculate the total harvest across all farmers.

```solidity
function recordHarvest(address farmer, uint256 amount) public {
    require(amount <= 1000, "Harvest amount exceeds the maximum allowed limit");

    harvestedAmounts[farmer] += amount;
    totalHarvest += amount;
}
```

### Payout Processing

The `processPayout` function is responsible for handling payouts to farmers. It employs the `assert` statement to ensure that the payout can only be processed twice. Additionally, a check is performed to ensure that the total harvest quantity is sufficient for a payout (in this case, at least 100 units).

```solidity
function processPayout() public {
    assert(payoutCount < 2);

    if (totalHarvest < 100) {
        revert("Insufficient total harvest quantity for payout");
    }

    payoutCount++;
}
```

## License

This smart contract is released under the MIT License. See the SPDX-License-Identifier in the source code for more details.

```solidity
// SPDX-License-Identifier: MIT
```

## Usage

Deploy this smart contract on the Ethereum blockchain to enable farmers to record their harvest and trigger payout processing. Interact with the contract using Ethereum wallet applications or scripts.

## Contact

harinadhhari15@gmail.com
