# Delegate Call In Solidity

```.delegatecall()``` is a method in Solidity used to call a function in a target contract from an original contract. However, unlike other methods, when the function is executed in the target contract using .delegatecall(), the context is passed from the original contract i.e. the code executes in the target contract, but variables get modified in the original contract.

DelegateCall, as the name implies, is calling mechanism of how caller contract calls target contract function but when target contract executed its logic, the context is not on the user who execute caller contract but on caller contract.

![image](https://user-images.githubusercontent.com/102557215/187830372-8c5c7fa2-f078-4565-a7b1-d5ef44dd1111.png)


![image](https://user-images.githubusercontent.com/102557215/187830398-f07feb2f-bd43-4915-9823-5ae43e8c9608.png)


Then when contract delegatecall to target, how the state of storage would be changed?

Because when delegatecall to target, the context is on Caller contract, all state change logics reflect on Caller’s storage.

For example, let’s there’s Proxy contract and Business contract. Proxy contract delegatecall to Business contract function. If the user calls Proxy contract, Proxy contract will delegatecall to Business contract and function would be executed. But all state changes will be reflected Proxy contract storage, not a Business contract.
