# About Blockchain

- In simple terms, blockchain are chain of blocks in which each block contains data and these blocks are chained togerther using secure cryptography.

- Blockchain can be seen as a distributed DB where copies of the data are spread across thousands of people's computers (called nodes).

- A wallet can be considered as a Bank Account where *wallet address corresponds to bank account number*. We can use the wallet to see the transaction history and the balance. **(NOTE: Wallet themselves store nothin)**

- A private key is used to send digital money from our account balance.

- Bitcoin is a digital money that just stores accounts and balances

- Ethereum, along with payments also has "Smart Contacts", which is a piece of code that runs on ethereum blockchain.

- A blockchain node is someone who has copy of all the data.

- State variables are permanently stored in contract storage. This means they're written to the Ethereum blockchain. Think of them like writing to a DB.

- All the reference types such as arrays, structs, mappings, and strings should be stored in memory. Example:
```
function eatBurgers(string memory _name) public {}
```


## Function Modifiers

- A view function is one which only views the data and not modifies it.
```
function sayHello() public view returns (string memory) {
    return "hello!";
}
```
The returns (string memory) denotes that the function returns stirng value.


- Events are a way for our contract to communicate that something happened on the blockchain to your app front-end.

- The Application Binary Interface (ABI) is a crucial component in the interaction between smart contracts and external applications, it serves as a communication protocol that defines how to interact with a smart contract.

- An address can be owned by a specific user or a smart contract.

- The msg.sender is a `global variable` available to all functions which refers to the address of the person (or smart contract) who called the current function.

- `require` (keyword) makes it so that the function will throw an error and stop executing if some condition is not true.

# Inheritance Exmaple

```
contract Doge {
  function catchphrase() public returns (string memory) {
    return "So Wow CryptoDoge";
  }
}

contract BabyDoge is Doge {
  function anotherCatchphrase() public returns (string memory) {
    return "Such Moon BabyDoge";
  }
}
```

- In Solidity, there are two locations you can store variables — in storage and in memory.

    `Storage` refers to variables stored permanently on the blockchain. `Memory` variables are temporary, and are erased between external function calls to your contract. Think of it like your computer's hard disk vs RAM.

    - Variables declared outside of functions are by default storage and written parmanently in blockchain, while variables declared inside functions are memory and will disappear when the function call ends.

- In addition to `public` & `private`, Solidity has 2 more visibility for functions: `internal` and `external`.

    `internal` is same as `private`, except that it's also accessible to child contracts.

    `external` is similar to `public`, except that these functions can ONLY be called outside the contract — they can't be called by other functions inside that contract.


- For our contract to talk to another contract on the blockchain that we don't own, **first we need to define an `interface`.**

- Contracts can be `Ownable`, meaning they have an owner who has special privileges.

- Modifiers are kind of half-functions that are used to modify other functions, usually to check some requirements prior to execution. (Something similar to middlewares)

- `View` functions don't cost any gas when they're called `externally` **(external view function)** by a user.

- `payable` function is a special type of function that can receive Ether. (Chapter-4)

- A `token` on Ethereum is basically just a smart contract that follows some common rules — namely it implements a standard set of functions that all other token contracts share, such as `transferFrom(address _from, address _to, uint256 _amount)` and `balanceOf(address _owner)`.

	OR: A token is just a contract that keeps track of who owns how much of that token, and some functions so those users can transfer their tokens to other addresses.

- Buring a token means assigning it's ownership to address 0 that no one has the private key of making it unrecoverable.

- A `library` is a special type of contract in Solidity. One of the things it is useful for is to attach functions to native data types.

  For example, with the SafeMath library, we'll have to use the syntax `using SafeMath for uint256`. 

- `assert` is similar to `require`, where it will throw an error if false. The difference between assert and require is that require will refund the user the rest of their gas when a function fails, whereas assert will not.

- `Web3 Provider` in `Web3.js` tells our code which node we should be talking to handle our reads and writes. It's kind of like setting the URL of the remote web server for your API calls in a traditional web app.

- Web3.js has two methods we will use to call functions on our contract: `call` and `send`.

- `call` is used for `view` and `pure` functions. It only runs on the local node, and won't create a transaction on the blockchain.

- `send` will create a transaction and change data on the blockchain.

-  In order to filter events and only listen for changes related to the current user, our Solidity contract would have to use the `indexed` keyword,