
# Intent models

The models in this document represent different user *intents*, i.e., models that the user has in his mind and would like ChatGPT to generate. For each one the exercise consists in asking ChatGPT to produce the
corresponding UML model using one or more prompts.

The models are given by an image, and at most with some constraints written in OCL. We did not want to provide the USE or PlatUML specification so that ChatGPT does not learn from them. In this way, we can use them for testing future versions of ChatGPT.

All models are labeled with a series of tags indicating the modeling concepts and mechanisms covered by the model. 

Possible tags include: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Association reified as a Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 
 

## Amphibious

<!--- ![amphibious](images/Amphibious-CD.png "Amphibious") -->

<p align="center">
<img src="images/Amphibious-CD.png"  width="60%">
</p>

```
constraints 
context LandVehicle inv LandMaxSpeed: 
    self.maxSpeed = 30
context LandVehicle inv LandEnvironment: 
    self.environment = #land
context MarineVehicle inv MarineMaxSpeed: 
    self.maxSpeed = 10
context MarineVehicle inv MarineEnvironment: 
    self.environment = #water
context AmphibiousVehicle  inv AmphibiousMaxSpeed: 
    self.maxSpeed = if self.environment = #water then 10 else 30 endif
context AmphibiousVehicle  inv AmphibiousEnvironment: 
    self.environment = #water or self.environment = #land
end
```

* **Tags**: Enumerations, Classes, Attributes, Generalization,  Multiple inheritance, Abstract classes, OCL constraints. 


## Football Matches


<p align="center">
<img src="images/Matches-CD.png"  width="60%">
</p>


```
constraints
context League inv MatchesOK: -- matches must be between teams in the same league
  self.match->forAll(m|
    m.local.league->includes(self) and m.visitor.league->includes(self))
context Match inv DifferentTeams: self.local<>self.visitor
context Match inv LocalWinner: 
  self.finished and self.localGoals>self.visitorGoals 
    implies self.winner = self.local
context Match inv VisitorWinner: 
  self.finished and self.localGoals<self.visitorGoals 
    implies self.winner = self.visitor
context Match inv NoWinner: not self.finished or 
  (self.finished and self.localGoals=self.visitorGoals) 
    implies self.winner->isEmpty()
context Match inv GoalsOK: 
  self.localGoals>=0 and self.visitorGoals>=0
```
* **Tags**: Classes, Attributes, Operations, Association, Aggregation, Association Class, OCL constraints. 

## Loans - Association Class

<p align="center">
<img src="images/Loans-AC-CD.png"  width="40%">
</p>


```
constraints
context Customer inv OnlyOneLoan12Installments:
    self.loan->select(installments>12)->size()<=1
context Bank inv ThirtyPercentLoans12Installments:
    (self.loan->select(installments>12)->size() * 100.0 / self.loan->size()) <= 30
context Customer inv DifferentYears:
    self.loan->forAll(l1,l2|l1<>l2 implies l1.startingYear<>l2.startingYear)
```

* **Tags**: Classes, Attributes, Operations, Association Class, OCL constraints, Roles (as assoc. ends). 

## Loans - Class

<p align="center">
<img src="images/Loans-CD.png"  width="80%">
</p>


```
constraints
context Customer inv OnlyOneLoan12Installments:
    self.loan->select(installments>12)->size()<=1
context Bank inv ThirtyPercentLoans12Installments:
    (self.loan->select(installments>12)->size() * 100.0 / self.loan->size()) <= 30
context Customer inv DifferentYears:
    self.loan->forAll(l1,l2|l1<>l2 implies l1.startingYear<>l2.startingYear)
```

* **Tags**: Classes, Attributes, Operations, Association reified as a Class, OCL constraints. 


## School

<p align="center">
<img src="images/School-CD.png"  width="60%">
</p>

* **Tags**: Classes, Attributes, Generalization, Association, Composition, Roles (as inherited classes). 

## Books and copies

<p align="center">
<img src="images/Books-CD.png"  width="40%">
</p>

* **Tags**: Classes, Attributes, Association, [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 


## Snarks

<p align="center">
<img src="images/Snark-CD.png" width="40%">
</p>

* **Tags**: Classes, Attributes, Association, A[Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7),  [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Car

<p align="center">
<img src="images/Car-CD.png"  width="80%">
</p>

```
constraints
  context Model inv ModelUniqueNames: 
    Model.allInstances->isUnique(name)
  context Make inv MakeUniqueNames:   
    Make.allInstances->isUnique(name)
  context Model inv SameSeatSizes:
    self.car.seat->collect(size)->asSet()->size()=1
  context Car inv SameWheelDiameter:
    self.wheel->collect(diameter)->asSet()->size()=1
```

* **Tags**: Classes, Attributes, Association, Composition, OCL constraints, [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## PurchaseOrders

<p align="center">
<img src="images/PO-CD.png"  width="60%">
</p>

```
constraints 
context Unit inv InStockOrWithCustomer:
   self.company->size() + self.order->size() = 1
```

* **Tags**: Classes, Attributes, Association, Aggregation, OCL constraints, Roles (as assoc. ends). 

## Banks

<p align="center">
<img src="images/Banks-CD.png"  width="60%">
</p>


```
constraints
  context Person inv ManagerOrClient:
    self.manager->notEmpty() implies 
    	   self.client.branch->excludes(self.manager.branch)
```

* **Tags**: Enumerations, Classes, Attributes, Association, Composition, OCL constraints, [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7). 

## Furniture

<p align="center">
<img src="images/LB1.png"  width="40%">
</p>


* **Tags**: Enumerations, Classes, Attributes, Generalization. 

## ScubaGear
<p align="center">
<img src="images/LB2.png"  width="60%">
</p>


* **Tags**: Classes, Attributes, Operations, Composition. 

## TennisMatch
<p align="center">
<img src="images/LB3.png"  width="20%">
</p>


* **Tags**: Classes, Attributes, Operations. 

## Courses
<p align="center">
<img src="images/LB4.png"  width="40%">
</p>


* **Tags**: Classes, Attributes, Association, Aggregation. 

## Airlines-AC
<p align="center">
<img src="images/LB5.png"  width="45%">
</p>


* **Tags**: Classes, Attributes, Operations, Association Class. 

## Airlines
<p align="center">
<img src="images/LB6.png"  width="35%">
</p>


* **Tags**: Classes, Attributes, Operations, Association reified as a Class. 

## Theather
<p align="center">
<img src="images/LB7.png"  width="50%">
</p>

* **Tags**: Classes, Attributes, Association, Composition, [Materialization](http://www.vldb.org/conf/1994/P630.PDF).

## Events
<p align="center">
<img src="images/LB8.png"  width="50%">
</p>

 
* **Tags**: Enumerations, Classes, Attributes, Generalization, Association, Aggregation, Roles (as assoc. ends).

## Bathroom
<p align="center">
<img src="images/LB9.png"  width="70%">
</p>

 
* **Tags**: Classes, Composition.

## Employees
<p align="center">
<img src="images/LB10.png"  width="50%">
</p>

 

* **Tags**: Classes, Attributes, Association Class.

## SimpleFolder

<p align="center">
<img src="images/JC1.png"  width="15%">
</p>

* **Tags**: Classes, Attributes, Association.


## FileSystem1
<p align="center">
<img src="images/JC2.png"  width="30%">
</p>

* **Tags**: Classes, Generalization, Aggregation.

 

## FileSystem2
<p align="center">
<img src="images/JC3.png"  width="40%">
</p>

* **Tags**: Classes, Attributes, Generalization, Aggregation.

 
## Git
<p align="center">
<img src="images/JC4.png"  width="50%">
</p>

* **Tags**: Classes, Attributes, Generalization, Aggregation.

 
## Robot1
<p align="center">
<img src="images/JC5.png"  width="30%">
</p>

* **Tags**: Enumerations, Classes, Attributes, Association Class.

 
## robot2
<p align="center">
<img src="images/JC6.png"  width="60%">
</p>

* **Tags**: Enumerations, Classes, Attributes, Generalization, Association class.

 
## Robot3
<p align="center">
<img src="images/JC7.png"  width="70%">
</p>

* **Tags**: Enumerations, Classes, Attributes, Generalization, Aggregation, Association class. 

 
## Online Cart
<p align="center">
<img src="images/JC8.png"  width="60%">
</p>

* **Tags**: Classes, Attributes, Aggregation, Composition, Association reified as a Class.

 
## Purchase Orders2
<p align="center">
<img src="images/JC9.png"  width="100%">
</p>

* **Tags**: Classes, Attributes, Generalization, Aggregation, Composition, Association reified as a Class. 

 
## Aircraft
<p align="center">
<img src="images/JC10.png"  width="50%">
</p>

* **Tags**: Classes, Generalization, Association, Composition.

 

## VideoStore1

<p align="center">
<img src="images/JT1.png"  width="15%">
</p>

* **Tags**: Classes, Attributes, Association.

 

## VideoStore2
<p align="center">
<img src="images/JT2.png"  width="30%">
</p>

* **Tags**: Classes, Attributes, Association, Aggregation.

 

## VideoStore3
<p align="center">
<img src="images/JT3.png"  width="30%">
</p>

* **Tags**: Classes, Attributes, Association, Composition.

 
## VideoStore4
<p align="center">
<img src="images/JT4.png"  width="30%">
</p>

* **Tags**: Classes, Attributes, Operations, Association, Composition.

 
## Theather1
<p align="center">
<img src="images/JT5.png"  width="30%">
</p>

* **Tags**: Classes, Attributes, Generalization, Association.

 
## Theather2
<p align="center">
<img src="images/JT6.png"  width="40%">
</p>

* **Tags**: Enumerations, Classes, Attributes, Generalization, Association.

 
## Theather3
<p align="center">
<img src="images/JT7.png"  width="40%">
</p>

* **Tags**: Enumerations, Classes, Attributes, Generalization, Association, Aggregation, Association Class.

 
## Theather4
<p align="center">
<img src="images/JT8.png"  width="60%">
</p>

* **Tags**: Enumerations, Classes, Attributes, Generalization, Association, Aggregation, Association Class, Roles (as inherited classes).

 
## Airport1
<p align="center">
<img src="images/JT9.png"  width="15%">
</p>

* **Tags**: Classes, Attributes, Association.

 
## Airport2
<p align="center">
<img src="images/JT10.png"  width="40%">
</p>

* **Tags**: Classes, Attributes, Operations, Association.

 