The below code is designated to be used in remix.zama.ai

You would be able to create multiple transactions by interacting with the contract created 

simply copy and use responsibly

```

import "fhevm/lib/TFHE.sol";

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.0;

contract Counter {
    uint256 public count;

    constructor() {
        count = 0;
    }

    function getCount() public view returns (uint256) {
        return count;
    }

    function increment() public {
        count += 1;
    }

    function decrement() public {
        require(count > 0, "Count cannot be negative");
        count -= 1;
    }
}

```

