# Theater plays

## Context

We want to model a system with theaters that represent plays.

* In a city there is a group of theaters, which throughout the season represent different plays. 
* Each play has a title, an author and a cast, which is nothing more than the set of characters that appear in it. 
* Each play is performed several times during a season, on specific days and in afternoon and evening sessions. 
* Actors are people who play the characters of a play in a specific performance. 
* In the same performance, a character can only be played by one actor, although the same actor can play several characters. 
* An actor can act in different performances on the same day (of the same or different plays), as long as they do not coincide in the same session (afternoon or evening). 

## Questions

1. Develop an UML class diagram with the structure of such a system, including the appropriate constraints that ensure the consistency of the data handled by the system.

2. Specify in OCL the following query operations in the class representing a theater:

    * Operation "plays()" returns the set of plays that have been performed in the theater in any season.
    * Operation "obrasTemp()" returns the set of plays that have been performed in the theater in a specific season (to be passed as parameter).

3. Specify in OCL the following two additional invariants:

    * An actor may perform in several theaters each season, though only in a single play in each theater.  
    * Several theaters can perform the same play in a season, but they cannot perform it on the same days.

4. Suppose further that each theater makes a profit on each performance of a play, which comes from the fees it charges to attendees. Those attending a performance pay a fee that is calculated by multiplying by 10 Euros the number of characters appearing in the cast of the play. Those attendees who are members of the theater pay half the fee, but pay the theater 1,000 Euros per season. Please extend the system model to include this new information and specify in OCL an operation that calculates the revenue of a theater in a given season.









