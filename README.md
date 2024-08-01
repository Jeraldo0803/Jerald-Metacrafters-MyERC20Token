# Jerald-Metacrafters-MyERC20Token

## Getting Started

### Description
The code for JeraldToken is taken from Openzeppelin's contract as it has all of the standards of proper implementation of ERC20 tokens.
You can visit the definition here: https://www.openzeppelin.com/contracts

### Executing / Running the Program
- You can use the online Solidity IDE named Remix, you can find it here: https://remix.ethereum.org/
- Make a new file and copy paste the content of the `JeraldToken.sol`.

- Compile the code, on the left side of the screen, with the icon named `Solidity Compiler`. Compile and then run.
- After that, go to `Deploy & Run Transactions`.
- To Deploy, you will need to provide the address of the `initialOwner`, you can copy & paste the address at the top of the left pane, just under *Accounts*.
- From there, scroll down and go to `Deployed Contracts`.

Here is the code snippet of the contract under `CrowdfundingContract.sol`.
```
// SPDX-License-Identifier: MIT
// Compatible with OpenZeppelin Contracts ^5.0.0
pragma solidity ^0.8.20;

import "@openzeppelin/contracts/token/ERC20/ERC20.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Burnable.sol";
import "@openzeppelin/contracts/access/Ownable.sol";
import "@openzeppelin/contracts/token/ERC20/extensions/ERC20Permit.sol";

contract JeraldToken is ERC20, ERC20Burnable, Ownable, ERC20Permit {
    constructor(address initialOwner)
        ERC20("JeraldToken", "JTK")
        Ownable(initialOwner)
        ERC20Permit("JeraldToken")
    {
        _mint(msg.sender, 100 * 10 ** decimals());
    }

    function mint(address to, uint256 amount) public onlyOwner {
        _mint(to, amount);
    }
}
```
- You can mint values as long as your current Account is the same as the `initialOwner`. Only owners can mint tokens, this is defined by `Ownable(initialOwner)1`.
- Any account can transfer `JTK` or `JeraldToken` as long as they have currency.
- Any account can burn `JTK` or `JeraldToken` as long as the value is not 0 or less than 0. 

## Author
Jeraldo0803
