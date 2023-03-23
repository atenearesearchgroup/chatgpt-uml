# University Degrees

## Context

We want to model a system composed of video stores, which are companies that have shops dedicated to renting movies. 

* Each video store has a name and a set of associated shops, each with a different address. 
* Customers of a video store can rent movies at any of its shops. 
* Each shop has a set of copies of each movie for rent, and a clerk who attends the store. 
* Customers ask the clerks for the movie they wish to rent and, if a copy of the movie is available at that shop, they are granted a 3 or 5 day loan depending on whether the customer is a regular or VIP customer. 
* The loans must be returned to the same shop where they were rented. 
* Regular customers can have a maximum of three active loans from the same video store, regardless of the shop they where rented from. VIP customers have no such limit.  
* No clerk may be a customer of the shop where he/she works. 
* If a customer returns a copy of a movie late, he/she is blacklisted in that video store and cannot rent any more movies in any of its shops.


## Questions

1. Develop a conceptual model of the structure of such a system in UML, with the corresponding elements, the relationships between them, and all required integrity constraints. 

2. Specify in OCL the following query operations on the class that models the video stores:

    * copies() returns the number of copies that all its shops have.
    * bestStore() returns the shop that has the most loans (if there are several in the same circumstance, it returns any of them). 
    * prestamoMasRetardado() returns the loan of the company's shops that has been overdue for the longest time. If none of them are overdue, it returns null. If there are several in the same circumstance, it returns any of them.

3. Model the behavior of the system by specifying the operations required to represent the loan of a movie and its return,  including their pre- and post-conditions. 

4. Create an object model with at least 2 customers and two video stores, each with two shops, and specify a behavior where one customer borrows a movie that is available, another customer borrows the same movie of which there is also a copy available, the second customer returns it on time, and then the first customer returns its copy late.
