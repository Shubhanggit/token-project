# token-project
This Solidity smart contract, MyToken, is a simple implementation of an ERC-20-like token on the Ethereum blockchain.
The token is named "HELLO" with the abbreviation "HE". The contract provides basic functionality for minting and burning tokens, which directly affects the total supply and balances of the token.
Creating and Deploying the MyToken Contract
1. Write the Contract
Open Remix IDE: Visit Remix IDE.

Create a New File:

Click the "+" icon in the left sidebar to create a new file.
Name the file MyToken.sol and save it.
Paste the Following Code:

solidity
Copy code
// SPDX-License-Identifier: MIT
pragma solidity ^0.8.18;

contract MyToken {
    string public tokenName = "HELLO";
    string public tokenAbbrv = "HE";
    uint256 public totalSupply;

    mapping(address => uint256) public balances;

    function mint(address _to, uint256 _value) public {
        require(_to != address(0), "Cannot mint to the zero address");
        totalSupply += _value;
        balances[_to] += _value;
    }

    function burn(address _from, uint256 _value) public {
        require(_from != address(0), "Cannot burn from the zero address");
        require(balances[_from] >= _value, "Insufficient balance to burn");
        totalSupply -= _value;
        balances[_from] -= _value;
    }
}
2. Compile the Contract
Select the Solidity Compiler Tab:

Click on the "Solidity Compiler" tab in the left sidebar.
Choose the Compiler Version:

Ensure the "Compiler" option is set to "0.8.18" or another compatible version.
Compile the Contract:

Click "Compile MyToken.sol".
3. Deploy the Contract
Go to Deploy & Run Transactions:

Navigate to the "Deploy & Run Transactions" tab in the left sidebar.
Deploy the Contract:

Make sure "MyToken" is selected from the contract dropdown menu.
Click "Deploy" to deploy the contract.
4. Interact with the Contract
Mint Tokens:

In the deployed contract section, find the mint function.
Enter an address and a value for minting tokens.
Click "transact" to execute the minting.
Burn Tokens:

Similarly, find the burn function in the deployed contract section.
Enter the address and value for burning tokens.
Click "transact" to execute the burning.
Check Total Supply and Balances:

To view the total supply of tokens, click on the totalSupply function.
To check the balance of a specific address, enter the address in the balances mapping field and click "call".
