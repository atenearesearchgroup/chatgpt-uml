# Book management

## Context

We want to model a computerized system for book management, whose structure is described below. 

* Each book has a title and one or more authors (e.g., Don Quixote, Miguel de Cervantes). 
* In addition to the authors' names, their date of birth and death (if they are deceased) are also stored. 
* Different editions of each book may exist, including the original one. 
* An edition may be of one type (paperback, hardcover or deluxe), has a number of pages and is published in one year, by one publisher and in one language. 
* Each edition may have a set of illustrators, who are in charge of the drawings of that edition (if any), as well as a set of translators, if the book has been translated from its original language. 
* Publishers print a number of copies of each edition. Each copy has an owner, which can be the publisher itself (if no one has bought it yet -- this is the default option), a bookstore, a library, or an individual. 

The behavior of the system allows books to be bought and borrowed. 
* Libraries can lend books to their registered users or to other libraries. 
* Individuals can only buy books through bookstores or from other individuals. 
* However, libraries and stores can buy them from publishers directly, from other stores or from individuals. 
* Publishers cannot buy books. 
* Finally, individuals may sell books that they own, but not books that they have borrowed from a library. 
* Libraries cannot sell books, only lend them, only if they own them and they are not borrowed.  
* Stores may not borrow books from any library.  
* Likewise, books may not be returned to a library that have not been previously borrowed.



## Questions

1. Develop a UML model with the structure of the system described above, with the corresponding elements and their relationships, incorporating also the following integrity constraints:

    * The values of all numeric data types must be correct (including, among others, that years and page numbers must be positive).  
    * No edition of a book may be earlier than its original edition.
    * When the number of copies of any book, including all editions, exceeds 10,000, the book is considered a best-seller. 
    * A person cannot own more than 100 copies of the books he has authored.

2. Model the behavior of the system, adding the required operations to carry out the actions described above, in particular the purchase, loan and return of the books. Include the pre- and postconditions of all operations, and their bodies if the modeling tool supports an action language (e.g., SOIL). It is important to respect the conditions indicated in the statement, such as that individuals cannot buy books from publishers, or that they cannot return books that they have not previously borrowed. 

3. Describe the behavior of the system in the following two scenarios, by means of their corresponding sequence diagrams:

    * An individual buys an original copy from a store, which in turn has purchased from a publisher.
    * An individual returns a book that he had borrowed from a library.

For both scenarios you should include two object diagrams, with the state of the system before and after the operations are carried out. 













