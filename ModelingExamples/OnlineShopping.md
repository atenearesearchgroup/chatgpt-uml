# Online shopping

## Context

The company nozamA sells different products to its customers. To purchase a product, the customer indicates the company how many units of the product he wants to buy. The company generates an order if there are enough units of that product in stock. The customer, after receiving the Order, passes it to his favorite transport company to send the items to his postal address. As a result of the shipment, a delivery note is generated, which is associated with the order, and which includes the total amount to be paid by the customer.  After shipment, the corresponding items become the property of the customer.

## Questions

1. Develop a UML model with the structure of the system described above, with the corresponding elements and their relationships, incorporating also the following integrity constraints:

* All units should have a serial number, which must be unique.
* All units of a product must have the same price, which coincides with the price established for the product.
* When more than ten items are included in one order, a discount of 10 % of the total invoice amount is applied.
* Every order must contain at least one item, and can only contain items of the same product.
* Any user can own at most 30 items of the same product, regardless of how many orders he/she has used to purchase them.

2. Model the behavior of the system, adding the required operations to carry out the actions described above. Include the pre- and postconditions of all operations, and their bodies if the modeling tool supports an action language (e.g., SOIL).  

3. Describe the behavior of the system in the following two scenarios, by means of their corresponding sequence diagrams:

* A company has 4 units of a product X.  A customer first buys 3 units of that product, and then buys one more. 
* A company has 4 units of a product X. A customer requests to buy 5 units of the product.

For both scenarios you should include two object diagrams, with the state of the system before and after the operations are carried out. 











