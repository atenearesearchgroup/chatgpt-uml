# Movie Theaters

## Context

We want to model a system that represents chains of movie theaters in a given country, with the following restrictions. 

* Each chain owns several movie theaters in different cities of the country. 
* The laws of that country prevent more than two movie theaters of the same chain in the same city. 
* Each theater has a number of rooms where movies are shown. 
* Each film has a duration and a director, and the chains have to pay a fee to the producer of the film each time they show it. 
* Each room has a maximum number of seats to accommodate the audience. 
* Each room may screen a maximum of five movies on the same day, whether they are the same film or not. 
* At least 20 minutes must elapse between the end of one screening and the beginning of the next in the same room. 
* Another rule in the country prevents films by a single director from being shown in the same cinema on the same day. 
* Customers buy their tickets centrally at each cinema chain, indicating the movie they want to see, the cinema of the chain where they want to see it, the day, the room, the start time, and the number of tickets they want. 
* Ticket prices for each movie are set by the chain. The price of a movie is the same for all theaters of the same chain. 
* Customers cannot buy more tickets than are currently available in the desired room. 
* A customer who has purchased a series of tickets may also return them if he/she does so before the movie starts. 
* Each chain has a loyalty card, and offers discounts at its theaters for customers who have it. Discounts are decided by each chain, but cannot exceed 50% of the ticket value, nor be less than 20%. 


## Questions

1. 1. Develop a UML class diagram with the structure of such a system, with all the elements mentioned above, the relationships between them, and all required integrity constraints. Examples of such constraints include that screenings of movies in the same theater room cannot overlap (i.e., the end of one must be after the beginning of the next), in addition to those described above.

2.	Model the behavior of the system, defining the necessary operations to buy and return tickets. Include the appropriate pre- and postconditions in the specified operations, as well as the body of the operations.

3. Specify a system with a chain (Yelmo) with two cinemas (Vialia and Rincon), each with two rooms, showing three different movies per day, during two days (D1 and D2). The movies can be: Joker, Batman, Superman, Aquaman and Dr.Strange. Each room has 20 seats. Model a system with 3 customers, one of whom has a loyalty card with the Yelmo chain and the others do not, and who buy and return several tickets at least 2 times. Assume that the duration of all movies is the same (120 minutes) and that the directors are, respectively, Todd Phillips, Christopher Nolan, Richard Donner, James Wan and Scott Derrickson. Show the sequence diagram of the invocations. Include at least one situation where you try to buy more tickets than the room allows and justify the way you propose to handle that situation.

 









