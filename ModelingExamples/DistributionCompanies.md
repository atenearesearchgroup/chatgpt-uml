# Distribution companies

## Context

We want to model the structure and behavior of a set of distribution companies. 

* Each company has a number of employees, including a director, a manager, and at least one base worker. 
* All employees have a salary. Of course, a person can work in several companies (though never in more than three), and therefore have different salaries. 
* Within the same company, the director has to be paid more than the manager, and the manager more than the base workers. 
* In addition, a person cannot hold two positions in the same company, i.e., a director cannot be a manager or a base worker, a manager cannot be a director or a base worker, and base workers cannot be managers or directors of that company (although they can be in other companies). 
* Each company sells a series of products (e.g., screws, long bits, short bits, nails, hammers, etc.), each with its own price. Of course, the price of items of the same product must be the same within the same company, but it may vary between different companies selling the same product. 
* People who place orders with a company become its customers. 
* Each order includes a number of items of the products sold by the company (for example, an order may be for 10 nails and 2 hammers, or for three chairs and two tables).  
* Each order must exceed a minimum value, otherwise it is not profitable for the company. Each company defines the minimum value of its orders. 
* Each company has two types of customers: normal customers, which are those who have placed at least one order, and VIP customers, which are those who have placed orders totaling more than 1,000 Euros. As soon as a customer becomes a VIP, he gets a 10% discount on all new orders. Let us further assume that the employees of a company are considered VIPs as soon as they start working for the company. 
* Companies have a set of items in stock in their warehouse at any given time. No one can place an order for items that are not in the company's warehouse. 
* Once an order is placed, the item disappears from the company's warehouse and becomes the property of the person who placed the order.
* Finally, the same person cannot have items of more than 10 different product types, regardless of the company where they were purchased. 

The behavior of the system is determined by a set of actions that allow: 

* Purchasing items by placing orders, 
* Replenishing the companies' warehouses, and
* Hiring and firing companies' workers.


## Questions

1. Develop a UML class diagram with the structure of such a system, with all the elements mentioned above, the relationships between them, and all required integrity constraints.

2. Create an object model describing a system with at least two companies, three customers (at least one of which works for a company), plus all those objects that are necessary to ensure the system constraints.

3. Model the behavior of the system, adding the required operations to carry out the actions described above. Include the pre- and postconditions of all operations, and their bodies if the modeling tool supports an action language (e.g., SOIL).  

4. Starting from the initial state defined by the object model defined above, and using a sequence diagram, describe the behavior of the system by which at least 5 orders are placed (2 by 1 new customer and the rest by existing customers), the warehouses of two companies are updated, 2 new people are hired, and another one is fired. 

5. Create an object diagram with the final state of the system after these operations are carried out. 





