
# Intent models

The models in this document represent different user *intents*, i.e., models that the user has in his mind and would like ChatGPT to generate. For each one the exercise consists in asking ChatGPT to produce the
corresponding UML model using one or more prompts.

The models are given by an image, and at most with some constraints written in OCL. We did not want to provide the USE or PlatUML specification so that ChatGPT does not learn from them. In this way, we can use them for testing future versions of ChatGPT.

## Amphibious

<!--- ![amphibious](../images/Amphibious-CD.png "Amphibious") -->

<p align="center">
<img src="../images/Amphibious-CD.png"  width="60%">
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


## Football Matches


<p align="center">
<img src="../images/Matches-CD.png"  width="60%">
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

## Loans - Association Class

<p align="center">
<img src="../images/Loans-AC-CD.png"  width="60%">
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



## Loans - Class

<p align="center">
<img src="../images/Loans-CD.png"  width="60%">
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



## School

<p align="center">
<img src="../images/School-CD.png"  width="60%">
</p>


## Books and copies

<p align="center">
<img src="../images/Books-CD.png"  width="50%">
</p>




## Snarks

<p align="center">
<img src="../images/Snark-CD.png width="60%">
</p>

## Car

<p align="center">
<img src="../images/Car-CD.png"  width="80%">
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



## PurchaseOrders

<p align="center">
<img src="../images/PO-CD.png"  width="60%">
</p>

```
constraints 
context Unit inv InStockOrWithCustomer:
   self.company->size() + self.order->size() = 1
```


## Banks

<p align="center">
<img src="../images/Banks-CD.png"  width="60%">
</p>


```
constraints
  context Person inv ManagerOrClient:
    self.manager->notEmpty() implies 
    	   self.client.branch->excludes(self.manager.branch)
```

## Furniture

<p align="center">
<img src="../images/LB1.png"  width="40%">
</p>


## ScubaGear
<p align="center">
<img src="../images/LB2.png"  width="60%">
</p>


## TennisMatch
<p align="center">
<img src="../images/LB3.png"  width="20%">
</p>


## Courses
<p align="center">
<img src="../images/LB4.png"  width="60%">
</p>


## Airlines-AC
<p align="center">
<img src="../images/LB5.png"  width="60%">
</p>


## Airlines
<p align="center">
<img src="../images/LB6.png"  width="40%">
</p>


## Theather0
<p align="center">
<img src="../images/LB7.png"  width="60%">
</p>

## Events
<p align="center">
<img src="../images/LB8.png"  width="50%">
</p>

 
## Bathroom
<p align="center">
<img src="../images/LB9.png"  width="60%">
</p>

 
## Employees
<p align="center">
<img src="../images/LB10.png"  width="60%">
</p>

 

## SimpleFolder

<p align="center">
<img src="../images/JC1.png"  width="20%">
</p>

 

## FileSystem1
<p align="center">
<img src="../images/JC2.png"  width="40%">
</p>

 

## FileSystem2
<p align="center">
<img src="../images/JC3.png"  width="50%">
</p>

 
## Git
<p align="center">
<img src="../images/JC4.png"  width="60%">
</p>

 
## Robot1
<p align="center">
<img src="../images/JC5.png"  width="40%">
</p>

 
## robot2
<p align="center">
<img src="../images/JC6.png"  width="60%">
</p>

 
## Robot3
<p align="center">
<img src="../images/JC7.png"  width="60%">
</p>

 
## Online Cart
<p align="center">
<img src="../images/JC8.png"  width="60%">
</p>

 
## Purchase Orders2
<p align="center">
<img src="../images/JC9.png"  width="80%">
</p>

 
## Aircraft
<p align="center">
<img src="../images/JC10.png"  width="60%">
</p>

 

## VideoStore1

<p align="center">
<img src="../images/JT1.png"  width="20%">
</p>

 

## VideoStore2
<p align="center">
<img src="../images/JT2.png"  width="50%">
</p>

 

## VideoStore3
<p align="center">
<img src="../images/JT3.png"  width="50%">
</p>

 
## VideoStore4
<p align="center">
<img src="../images/JT4.png"  width="50%">
</p>

 
## Theather1
<p align="center">
<img src="../images/JT5.png"  width="40%">
</p>

 
## Theather2
<p align="center">
<img src="../images/JT6.png"  width="60%">
</p>

 
## Theather3
<p align="center">
<img src="../images/JT7.png"  width="60%">
</p>

 
## Theather4
<p align="center">
<img src="../images/JT8.png"  width="60%">
</p>

 
## Airport1
<p align="center">
<img src="../images/JT9.png"  width="20%">
</p>

 
## Airport2
<p align="center">
<img src="../images/JT10.png"  width="50%">
</p>

 