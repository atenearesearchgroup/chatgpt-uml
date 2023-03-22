# The Banks

## Context

Suppose the financial system of a country is composed of banks. 

* Each bank has branches, which may be spread throughout the country, but there may not be more than three branches of the same bank in the same city. 
* The structure of a bank's branches is hierarchical, so that a branch may have subordinate branches (of the same bank), either in the same city or in other cities. 
* The customers of a branch can be either the individuals or companies that have an account at the branch. Each customer may have one or more accounts in any of the branches of a bank. Each account can have only one account holder, the customer who opens the account. 
* Each branch owns an account, in which it stores its assets. 
* Each account has a balance, which must be positive, unless it is a "credit" account. 
* Credit accounts allow their balance to be negative, with a limit that is established when the account is opened. 
* A customer may request a change in this limit from the branch where the account is held, and the branch must request authorization from the branch directly responsible for it (except the head office, at the root of the hierarchy, which can make decisions directly). Changes in the credit limit will be authorized as long as the new limit is lower than the previous one, or if it is only 10% higher than the one the account already had, and the current balance exceeds the new limit (e.g., if the credit limit is 1,000 Euros and you request to increase it to 1,005 Euros with a balance of 1,100 euros on the account, the branch will authorize the change).
* Customer can perform transactions with their accounts (request balance, deposit or withdraw money, and transfer money to another account). hey can also open accounts at any branch. When opening an account, the initial balance is 0. If the account is a credit account, the initial limit is 10 euros. 
* The accounts have a maintenance fee of 1% per year. This means that, once a year (on January 1), each branch deducts 1% from the current balance of all its accounts. If the balance is 0 and the account is not a credit account, no money is deducted. In case of credit accounts, if the resulting balance is negative the branch will deduct 1% of the account's credit limit instead. The deducted money from the becomes the property of the branch and is stored in your account.
* All customers can transfer money from any of the accounts the own, to any other account -- no matter who the owner is, or the bank the destination account belongs to. Transfers between accounts of different banks have a 2% commission, i.e., if you transfer 1,000 euros, then 980 euros are deposited in the destination account. That 2% of the money becomes the property of the origin and destination branches (1% for each). Transfers between accounts of the same bank are free of charge. 
* Companies with a balance of more than 1 million euros in one of their accounts are considered VIP by that bank and have a number of advantages. Firstly, in a transfer between banks, the part corresponding to the account of origin or destination that is of that bank is not taxed with the corresponding 1%. Secondly, these accounts do not pay an annual maintenance fee. Only companies, and not individuals, can be considered VIP.
* Finally, accounts whose holders are bank branches pay neither annual fee nor transfer commission in any bank.


## Questions

1. Develop the conceptual model of the structure of such a system in UML, including the appropriate OCL constraints that describe the system invariants. 

2. Specify the behavior of the operations described above. Include the appropriate pre- and post-conditions, and the body of operations if using a UML tool that supports an action language (such as SOIL).

3. Specify a system with 2 banks, each with two branches, and each branch with 3 accounts, one of which must be a credit account. There must be at least two customers with multiple accounts at different banks, and one VIP customer. 

4. If using an action language, make transfers between the accounts over 3 years, so as to cover all possible cases of collection and waiver of maintenance and transfer fees, and check that all operations work correctly.

 









