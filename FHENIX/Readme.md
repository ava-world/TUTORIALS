## NETWORK CONFIGURATION FOR DEVNET


Network Name: FHENIX DEVNET

Symbol: FHE

chain ID: 5432

RPC URL : https://fhenode.fhenix.io/new/evm

Block Exolorer : https://demoexplorer.fhenix.io/



## FAUCET LINK

<a href="https://fhenix-demo.pages.dev/">Faucet link</a>




## SAMPLE CODE

```

// SPDX-License-Identifier: MIT
pragma solidity ^0.8.17;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "fhevm/lib/TFHE.sol";

contract WrappingERC20 is ERC20 {

    // A mapping from address to an encrypted balance.
    mapping(address => euint32) internal _encBalances;

    constructor(string memory name, string memory symbol) ERC20(name, symbol) {
        _mint(msg.sender, 100 * 10 ** uint(decimals()));
    }

    function wrap(uint32 amount) public {
        require(balanceOf(msg.sender) >= amount);
        _burn(msg.sender, amount);

        _encBalances[msg.sender] = TFHE.add(_encBalances[msg.sender], amount);
    }

    function unwrap(uint32 amount) public {
        TFHE.req(TFHE.gt(_encBalances[msg.sender], amount));

        _encBalances[msg.sender] = TFHE.sub(_encBalances[msg.sender], amount);

        _mint(msg.sender, amount);
    }

    function transferEncrypted(address to, bytes calldata encryptedAmount) public {
        _transferEncrypted(to, TFHE.asEuint32(encryptedAmount));
    }

    // Transfers an amount from the message sender address to the `to` address.
    function _transferEncrypted(address to, euint32 amount) internal {
        _transferImpl(msg.sender, to, amount);
    }

        // Transfers an encrypted amount.
    function _transferImpl(address from, address to, euint32 amount) internal {
        // Make sure the sender has enough tokens.
        TFHE.req(TFHE.le(amount, _encBalances[from]));

        // Add to the balance of `to` and subract from the balance of `from`.
        _encBalances[to] = TFHE.add(_encBalances[to], amount);
        _encBalances[from] = TFHE.sub(_encBalances[from], amount);
    }

    function balanceOfEncrypted(address sender, bytes32 publicKey) 
    public 
    view 
    returns (bytes memory)
    {
        return TFHE.reencrypt(_encBalances[sender], publicKey);
    }
}


```
