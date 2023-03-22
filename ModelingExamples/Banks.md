# The Banks

## Context

Suppose the financial system of a country is composed of banks. 

1) Each bank has branches, which may be spread throughout the country, but there may not be more than three branches of the same bank in one city. 
The structure of a bank's branches is hierarchical, so that a branch may have under it (subordinate) some other branches of the same bank (whether in the same city or in other cities), for whose operations and customers it is also responsible.
2) Customers of a branch are those individuals or companies that have an account open at the branch. Each customer may have one or more accounts at any of a bank's branches. Each account can have only one owner, who opens the account. All branches have one account that they own, where they keep their assets. [0.25]
3) Each account has a balance, which must be positive unless it is a "credit" account. This type of account allows a balance to be negative, with a limit that is established when the account is opened. A customer can request a change in this limit from the branch where the account is held, but the branch must request authorization from the branch directly responsible for the account (except for the head office, at the root of the hierarchy, which can make decisions directly). Changes to the credit limit will be authorized provided that the new limit is lower than the previous one, or if it is only 10% higher than the one the account already had and the current balance exceeds the new limit (for example, if the credit limit is 1000 and you ask to increase it to 1005 with a balance of 1100 Euros on the account, the branch will authorize such a change of limit). [0.75]
4) A customer can perform operations with his account (request balance, deposit or withdraw money, and transfer money to another account), or open an account at any branch. When opening an account, the initial balance is 0. If the account is a credit account, the initial limit is 10 Euros. [0.5]
5) The accounts have a maintenance fee of 1% per year. This means that, once a year (on January 1), each branch deducts 1% from the current balance of all its accounts. If your balance is negative, they transfer 1% of the account's credit limit. That money becomes the property of the branch, and is stored in your account. [0.75]
6) All customers can transfer money between accounts, both from the same bank and from other banks. Transfers between accounts of different banks are charged with a 2% commission, i.e. if 1000 Euros are transferred, 980 Euros are deposited in the destination account. That 2 % of the money becomes the property of the origin and destination branches of the transfer in equal parts (1 % for each one). Transfers between accounts of the same bank are free of charge. [0.75]
7) Companies that have an account with a balance of more than 1 million euros are considered VIP by that bank and have a number of advantages. Firstly, in a transfer between banks, the part corresponding to the origin or destination account that is that bank's is not taxed with the corresponding 1%. Secondly, these accounts do not pay an annual maintenance fee.  [0.75]
8) Finally, accounts whose owners are bank branches pay neither annual fees nor transfer fees at any bank. [0.5]

## Questions

(a) Develop the conceptual model of the structure of such a system in UML, including the appropriate constraints. 
(b) Specify the behavior of the system that allows modeling the operations described in the statement and its operation. Include the appropriate pre- and post-conditions in the specified operations and the body of the operations. 
(c) Specify a system with 2 banks, each with two branches, and each branch with 3 accounts, one of which must be a credit account. There must be at least two customers with multiple accounts at different banks, and one VIP company. Make transfers between the accounts over 3 annuities, so as to cover all possible cases of collection and waiver of maintenance and transfer fees, and check that all operations work correctly. [2]

 









