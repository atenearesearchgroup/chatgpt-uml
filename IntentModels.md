
# Intent models

The models in this document represent different user *intents*, i.e., models that the user has in his mind and would like ChatGPT to generate. For each one the exercise consists in asking ChatGPT to produce the
corresponding UML model using one or more prompts.

The models are given by an image, and at most with some constraints written in OCL. We did not want to provide the USE or PlatUML specification so that ChatGPT does not learn from them. In this way, we can use them for testing future versions of ChatGPT.

All models are labeled with a series of tags indicating the modeling concepts and mechanisms covered by the model. 

Possible tags include: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF) 
 

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

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 


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
**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

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

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

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

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 


## School

<p align="center">
<img src="images/School-CD.png"  width="60%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Books and copies

<p align="center">
<img src="images/Books-CD.png"  width="40%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 


## Snarks

<p align="center">
<img src="images/Snark-CD.png" width="40%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

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

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## PurchaseOrders

<p align="center">
<img src="images/PO-CD.png"  width="60%">
</p>

```
constraints 
context Unit inv InStockOrWithCustomer:
   self.company->size() + self.order->size() = 1
```

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

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

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Furniture

<p align="center">
<img src="images/LB1.png"  width="40%">
</p>


**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## ScubaGear
<p align="center">
<img src="images/LB2.png"  width="60%">
</p>


**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## TennisMatch
<p align="center">
<img src="images/LB3.png"  width="20%">
</p>


**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Courses
<p align="center">
<img src="images/LB4.png"  width="40%">
</p>


**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Airlines-AC
<p align="center">
<img src="images/LB5.png"  width="45%">
</p>


**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Airlines
<p align="center">
<img src="images/LB6.png"  width="35%">
</p>


**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Theather
<p align="center">
<img src="images/LB7.png"  width="50%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Events
<p align="center">
<img src="images/LB8.png"  width="50%">
</p>

 
**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Bathroom
<p align="center">
<img src="images/LB9.png"  width="70%">
</p>

 
**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## Employees
<p align="center">
<img src="images/LB10.png"  width="50%">
</p>

 

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

## SimpleFolder

<p align="center">
<img src="images/JC1.png"  width="15%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 


## FileSystem1
<p align="center">
<img src="images/JC2.png"  width="30%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 

## FileSystem2
<p align="center">
<img src="images/JC3.png"  width="40%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Git
<p align="center">
<img src="images/JC4.png"  width="50%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Robot1
<p align="center">
<img src="images/JC5.png"  width="30%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## robot2
<p align="center">
<img src="images/JC6.png"  width="60%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Robot3
<p align="center">
<img src="images/JC7.png"  width="70%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Online Cart
<p align="center">
<img src="images/JC8.png"  width="60%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Purchase Orders2
<p align="center">
<img src="images/JC9.png"  width="100%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Aircraft
<p align="center">
<img src="images/JC10.png"  width="50%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 

## VideoStore1

<p align="center">
<img src="images/JT1.png"  width="15%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 

## VideoStore2
<p align="center">
<img src="images/JT2.png"  width="30%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 

## VideoStore3
<p align="center">
<img src="images/JT3.png"  width="30%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## VideoStore4
<p align="center">
<img src="images/JT4.png"  width="30%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Theather1
<p align="center">
<img src="images/JT5.png"  width="30%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Theather2
<p align="center">
<img src="images/JT6.png"  width="40%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Theather3
<p align="center">
<img src="images/JT7.png"  width="40%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Theather4
<p align="center">
<img src="images/JT8.png"  width="60%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Airport1
<p align="center">
<img src="images/JT9.png"  width="15%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 
## Airport2
<p align="center">
<img src="images/JT10.png"  width="40%">
</p>

**Tags**: Enumerations, Classes, Attributes, Operations, Generalization, Association, Aggregation, Composition, Association Class, Multiple inheritance, Abstract classes, OCL constraints, Roles (as assoc. ends), Roles (as inherited classes), [Roles (as entity types)](https://link.springer.com/chapter/10.1007/978-3-540-30464-7_7), and [Materialization](http://www.vldb.org/conf/1994/P630.PDF). 

 