<!-----

You have some errors, warnings, or alerts. If you are using reckless mode, turn it off to see inline alerts.
* ERRORs: 0
* WARNINGs: 0
* ALERTS: 2

Conversion time: 1.9 seconds.


Using this Markdown file:

1. Paste this output into your source file.
2. See the notes and action items below regarding this conversion run.
3. Check the rendered output (headings, lists, code blocks, tables) for proper
   formatting and use a linkchecker before you publish this page.

Conversion notes:

* Docs to Markdown version 1.0β34
* Sun Mar 19 2023 22:57:13 GMT-0700 (PDT)
* Source doc: MODELOS de AV
* This document has images: check for >>>>>  gd2md-html alert:  inline image link in generated source and store images to your server. NOTE: Images in exported zip file from Google Docs may not appear in  the same order as they do in your doc. Please check the images!

----->


<p style="color: red; font-weight: bold">>>>>>  gd2md-html alert:  ERRORs: 0; WARNINGs: 0; ALERTS: 2.</p>
<ul style="color: red; font-weight: bold"><li>See top comment block for details on ERRORs and WARNINGs. <li>In the converted Markdown or HTML, search for inline alerts that start with >>>>>  gd2md-html alert:  for specific instances that need correction.</ul>

<p style="color: red; font-weight: bold">Links to alert messages:</p><a href="#gdcalert1">alert1</a>
<a href="#gdcalert2">alert2</a>

<p style="color: red; font-weight: bold">>>>>> PLEASE check and correct alert issues and delete this message and the inline alerts.<hr></p>



## Amphibious



<p id="gdcalert1" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image1.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert2">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image1.png "image_tooltip")



```
model Amphibious
enum Environment {land, water, air}
abstract class Vehicle 
  attributes
    position: Integer init: 0
    speed: Integer
    maxSpeed : Integer
    environment: Environment
  operations
    move(time: Integer)
end
class LandVehicle  < Vehicle
constraints 
   inv LandMaxSpeed: self.maxSpeed = 30
   inv LandEnvironment: self.environment = #land
end
class MarineVehicle  < Vehicle
constraints 
   inv MarineMaxSpeed: self.maxSpeed = 10
   inv MarineEnvironment: self.environment = #water
end
class AmphibiousVehicle  < MarineVehicle, LandVehicle
constraints 
   inv AmphibiousMaxSpeed: 
self.maxSpeed = if self.environment = #water then 10 else 30 endif
   inv AmphibiousEnvironment: 
self.environment = #water or self.environment = #land
end
```


**ENUNCIADO**

Build a UML class diagram that represents different types of vehicles. An abstract class Vehicle contains the characteristics of all of possible vehicles, although each type of vehicle implements them in a different way.  All vehicles have a position, they can move at a certain speed, and in a certain Environment (which can be "land", "water" or "air"). A move() operation moves the vehicle for the number of seconds indicated by its argument. 

The model allows defining instances of Land, Marine and Amphibious vehicles. The former move only in "land" environments, and can move at a maximum speed of 30 m/s. Marine vehicles can only move in "water" environments, and their maximum speed is 10 m/s. Finally, amphibious vehicles can move in "land" or "water" environments, and their maximum speed coincides with that of land or marine vehicles depending on the environment they are in. 

Resultado en PlantUML que da ChatGPT para ese enunciado.

@startuml

abstract class Vehicle {

  position: String

  speed: Integer

  environment: String

  +move(time: Integer)

}

class LandVehicle {

  +move(time: Integer)

}

class MarineVehicle {

  +move(time: Integer)

}

class AmphibiousVehicle {

  +move(time: Integer)

}

Vehicle &lt;|-- LandVehicle

Vehicle &lt;|-- MarineVehicle

Vehicle &lt;|-- AmphibiousVehicle

@enduml


---


## Football Matches



<p id="gdcalert2" ><span style="color: red; font-weight: bold">>>>>>  gd2md-html alert: inline image link here (to images/image2.png). Store image on your image server and adjust path/filename/extension if necessary. </span><br>(<a href="#">Back to top</a>)(<a href="#gdcalert3">Next alert</a>)<br><span style="color: red; font-weight: bold">>>>>> </span></p>


![alt_text](images/image2.png "image_tooltip")



```
model FootballLeague

class League
end
class Team
end
class Stadium
end

aggregation Teams between 
    League [*]
    Team [*]
end

aggregation Matches between
    League [1]
    Match [*]
end

association HomeStadium between
Team [*] role team 
Stadium [1] role stadium 
end

associationclass Match between
Team [*] role local
Team [*] role visitor
attributes
finished:Boolean init:false
localGoals:Integer init:0
visitorGoals:Integer init:0
operations
localGoal()
    pre: not self.finished
    post: self.localGoals = self.localGoals@pre + 1
visitorGoal()
    pre: not self.finished
    post: self.visitorGoals = self.visitorGoals@pre + 1
end

association Winner between
  Match [*] role wonMatch
  Team [0..1] role winner derive = 
if (self.finished and self.localGoals>self.visitorGoals) then self.local 
    else if (self.finished and self.localGoals<self.visitorGoals) then 
         self.visitor
     else null
     endif
endif  
end

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
context Match inv GoalsOK: self.localGoals>=0 and self.visitorGoals>=0
```




**ENUNCIADO**

Build a UML class diagram that represents a football league where teams play against each other in matches. Each team has a home stadium, and in each match one team plays as either the local or visiting team. The information collected from a match includes the number of goals scored by the local and visiting teams, and whether or not the match has been played.

In addition, once played, the match collects information about the team that won the match, in case there is no goal draw. During the league, each team plays one local and one visiting match against all other teams. Of course, a team cannot play against itself. Two operations, localGoal() and visitorGoal(), take care of updating the result of the match while it is being played.  Once the match is finished, these two operations have no effect.

Resultado en PlantUML que da ChatGPT para ese enunciado.

@startuml

class League {

  -teams: Team[]

  -matches: Match[]

}

class Team {

  -name: String

  -stadium: Stadium

  -matches: Match[]

}

class Stadium {

  -name: String

}

class Match {

  -localTeam: Team

  -visitorTeam: Team

  -localGoals: int

  -visitorGoals: int

  -played: boolean

  -winner: Team

  +localGoal()

  +visitorGoal()

}

League "1" -- "*" Team

Team "1" -- "*" Match

Match "1" -- "1" Team : localTeam

Match "1" -- "1" Team : visitorTeam

Match "1" -- "1" Stadium : localTeam.stadium

@enduml

TRADUCIDO DE USE A PLANTUML:

Here's the PlantUML code that represents the FootballLeague model:

kotlin

Copy code

@startuml

class League

class Team

class Stadium

Teams "0..*" -- "*" Team

League "1" -- "*" Match

Team "*" -- "*" Match : plays

Team "*" --> "1" Stadium : home stadium

class Match {

  finished : Boolean = false

  localGoals : Integer = 0

  visitorGoals : Integer = 0

  +localGoal() : void

  +visitorGoal() : void

}

Match "*" -- "*" Winner

Winner --> "0..1" Team : winner

@enduml

In this PlantUML code, we define the classes League, Team, Stadium, and Match. We then define the associations and aggregation relationships between these classes using the appropriate PlantUML keywords (-->, --, and *--*). Finally, we define the Winner association class and its relationship with Match and Team.

Note that the PlantUML code does not include the constraints from the original USE model, as PlantUML is a visualization tool and not a modeling language with formal semantics. However, you can still use PlantUML to create diagrams that help you understand and communicate your model.


## Loans - Association Class


```
model loans
class Customer
end
class Bank
end
associationclass Loan between 
    Customer [*]
    Bank [*]
attributes
    totalAmount : Integer
    startingYear : Integer
    installments : Integer
    outstandingAmount : Integer
operations
    payInstallment()
end
constraints
context Customer inv OnlyOneLoan12Installments:
    self.loan->select(installments>12)->size()<=1
context Bank inv ThirtyPercentLoans12Installments:
    (self.loan->select(installments>12)->size() * 100.0 / self.loan->size()) <= 30
context Customer inv DifferentYears:
    self.loan->forAll(l1,l2|l1<>l2 implies l1.startingYear<>l2.startingYear)
```


**ENUNCIADO**

Build a UML class diagram that represents possible loans from a bank to its customers. Each customer may have **_at most one loan_** with each bank.

Information associated with each loan should include the total amount of the loan, the starting year, the number of installments in which the loan is to be repaid and the amount currently outstanding. The amount to be paid in each of the installments corresponds to the total amount of the loan divided by the number of installments. The customer pays each of these installments using the operation "payInstallment()"  which reduces the outstanding amount by the amount of one installment, until the full amount of the loan is paid. In addition, the following requirements must be met: 

(1) A customer cannot have more than one loan with a number of installments greater than 12, although it can have many others of a shorter duration.

(2) A bank may not have more than 30 % of its loans with a number of installments greater than 12.

(3) The starting years of the loans of the same customer cannot coincide, as it is assumed that a person cannot sign two loans in the same year.


## Loans - Class


```
model loans
class Customer
end
class Bank
end
class Loan  
  attributes
    totalAmount : Integer
    startingYear : Integer
    installments : Integer
    outstandingAmount : Integer
  operations
    payInstallment()
end
association CustomerLoans between
    Customer [1]
    Loan [*] 
end
association BankLoans between 
    Bank [1]
    Loan [*]
end
constraints
context Customer inv OnlyOneLoan12Installments:
    self.loan->select(installments>12)->size()<=1
context Bank inv ThirtyPercentLoans12Installments:
    (self.loan->select(installments>12)->size() * 100.0 / self.loan->size()) <= 30
context Customer inv DifferentYears:
    self.loan->forAll(l1,l2|l1<>l2 implies l1.startingYear<>l2.startingYear)
```


**ENUNCIADO**

Build a UML class diagram that represents possible loans from a bank to its customers. Each customer may have**_ multiple loans_** with each bank.

Information associated with each loan should include the total amount of the loan, the starting year, the number of installments in which the loan is to be repaid and the amount currently outstanding. The amount to be paid in each of the installments corresponds to the total amount of the loan divided by the number of installments. The customer pays each of these installments using the operation "payInstallment()"  which reduces the outstanding amount by the amount of one installment until the full amount of the loan is paid. In addition, the following requirements must be met: 

(1) A customer cannot have more than one loan with a number of installments greater than 12, although it can have many others of a shorter duration.

(2) A bank may not have more than 30 % of its loans with a number of installments greater than 12.

(3) The starting years of the loans of the same customer cannot coincide, as it is assumed that a person cannot sign two loans in the same year.


## School


```
model School
class Person 
attributes
  firstName: String
  lastName: String
  age : Integer
end
class Student < Person
  attributes
  studentId:String
end
class Teacher < Person
  attributes
  salary: Real
end
class School 
  attributes
  name: String
  address: String
end
composition Enrollment between 
  School [1]
  Student [*]
end
composition Faculty between 
  School [1]
  Teacher [*]
end
association Tutorship between 
    Teacher [1] 
    Student [*]
end
```




**ENUNCIADO**

Build a UML class diagram that represents schools composed of Persons, who can be either Teachers or Students. Persons have a first and last name, and an age. Teachers have a salary and students have a studentId. Schools have a name and an address, and contain a set of teachers and a set of students. Teachers may also act as tutors of several students.

Lo que devuelve ChatGPT es:

@startuml

class School {

  +name: String

  +address: String

  +teachers: Set&lt;Teacher>

  +students: Set&lt;Student>

}

class Person {

  +firstName: String

  +lastName: String

  +age: int

}

class Teacher {

  +salary: float

  +tutoredStudents: Set&lt;Student>

}

class Student {

  +studentId: String

}

Person &lt;|-- Teacher

Person &lt;|-- Student

School "1" -- "*" Teacher

School "1" -- "*" Student

Teacher "0..*" -- "0..*" Student : Tutors

@enduml




## Books and copies


```
model Books

class Book
  attributes
    title : String
    year : Integer
end

class Edition
  attributes
    publisher : String
    city : String
    editionYear : Integer
    ISBN : String
end

class BookCopy 
  attributes 
    SerialNumber : String
end 

class Person
end

association Ownership between 
  Person [0..1] role owner
  BookCopy [*] role ownedBook 
end

association Authorship between 
  Book [*] role authoredBook 
  Person [*] role author
end

association Editionship between 
    Book [1]
    Edition [*]
end

association Copies between 
    Edition [1]
    BookCopy [*]
end
```




**ENUNCIADO**

Build a UML class diagram that represents Books and their copies. Books may have different editions, and each copy of a book belongs to one edition. In addition, books are authored by persons, which can also own copies of books.

Lo que devuelve ChatGPT es:


```
@startuml
class Book {
  +title: String
  +author: Person
  +editions: Set<Edition>
}

class Edition {
  +editionNumber: int
  +year: int
  +copies: Set<BookCopy>
}

class BookCopy {
  +copyId: String
  +owner: Person
}

class Person {
  +firstName: String
  +lastName: String
  +ownedCopies: Set<BookCopy>
}

Book "1" -- "0..*" Edition : hasEditions
Edition "1" -- "0..*" BookCopy : hasCopies
Person "0..*" -- "0..*" BookCopy : owns
Book "1" -- "1" Person : authoredBy
@enduml


---
```



## 


## Snarks


```
model Snarks

class Snark
end

association Pat between 
Snark [0..2] role pat 
Snark [*] 
end 

class Brred
  attributes
    fur:Boolean
end

class Snarkdo 
  attributes
    teet : Integer
end 

class Zumbat
end

association Rete between 
  Zumbat [0..1] role reter
  Snarkdo [*] role retal
end

association Axum between 
  Snark [*] role axumedSnark 
  Zumbat [*] 
end

association SnarkBrred between 
    Snark [1]
    Brred [*]
end

association SnarkdoHood between 
    Brred [1]
    Snarkdo [*]
end
```


ENUNCIADO

Build a UML class diagram that represents Snarks. A Snark can be related to at most 2 other snarks, and to Brreds. Breeds may be related to different Snardos. In addition, Snarks are axumed by zumbats, which can also rete snarkdos.

Dependiendo de la sesion, puede dar resultados muy diferentes:

COn una sesion nueva: 

@startuml

class Snark {

  -id: string

  -relatedSnark1: Snark

  -relatedSnark2: Snark

  +getId(): string

  +getRelatedSnark1(): Snark

  +getRelatedSnark2(): Snark

  +setRelatedSnark1(Snark): void

  +setRelatedSnark2(Snark): void

}

class Breed {

  -name: string

  -snarkdos: int

  +getName(): string

  +getSnarkdos(): int

  +setSnarkdos(int): void

}

class Zumbat {

  -id: string

  -snarkdos: int

  +getId(): string

  +getSnarkdos(): int

  +setSnarkdos(int): void

  +assumeSnark(Snark): void

}

Snark --|> Breed

Snark --|> Zumbat

@enduml



Con una sesion en donde hemos modelado algo ya:

@startuml

class Snark {

  +name: String

  +age: Integer

}

class Breed {

  +name: String

  +type: String

}

class Zumbat {

  +name: String

  +snarkCount: Integer

}

Snark "1" -- "2" Snark

Snark "1" -- "many" Breed

Zumbat "1" -- "many" Snark

@enduml




## Cars


```
model Car
class Make
  attributes
    name:String
end
class Model
  attributes 
     name:String
end
class Car
  attributes numberPlate:String
end
class Engine
  attributes diameter:Real
end
class Wheel
  attributes diameter:Real
end
class Seat
  attributes size:Real
end
composition CarWheels between 
    Car [1]
    Wheel [4]
end
composition CarEngine between 
    Car [1]
    Engine [1]
end
composition CarSeat between 
    Car [1]
    Seat [*]
end
association MakeModel between
    Make [1] 
    Model [*]
end
association ModelCar between
    Model [1] 
    Car [*]
end
constraints
  context Model inv ModelUniqueNames: Model.allInstances->isUnique(name)
  context Make inv MakeUniqueNames:   Make.allInstances->isUnique(name)
  context Model inv SameSeatSizes:
        self.car.seat->collect(size)->asSet()->size()=1
  context Car inv SameWheelDiameter:
        self.wheel->collect(diameter)->asSet()->size()=1
```


**ENUNCIADO**

Build a UML class diagram in PlantUML that represents cars. Cars belong to models, which in turn belong to makes. Each car has four wheels, one engine and one set of seats. Every make and model have a unique name. Each wheel has a diameter, which must be the same for all wheels of the same car. Each engine has a certain power.  Likewise, the seats have a size, which must be the same for all the seats of the cars of the same model. Each car has a number plate that identifies it.

@startuml

class Car {

  -model: Model

  -numberPlate: String

  +engine: Engine

  +seats: Seats

  +wheel: Wheel

}

class Engine {

  -power: String

}

class Seats {

  -size: String

}

class Wheel {

  -diameter: String

}

class Make {

  -name: String

  +model: Model

}

class Model {

  -name: String

  -make: Make

}

Car "1" -- "4" Wheel

Car "1" -- "1" Engine

Car "1" -- "1" Seats

Car "1" o-- "1" Model

Model o-- "1" Make

@enduml


## PurchaseOrders


```
model nozamA
class Company
attributes name : String
end
class Customer
end 
class Product 
attributes price:Integer 
end 
class Unit 
attributes 
    serialNumber:String
    price:Integer derive: self.product.price
end 
class Order 
attributes 
    totalAmount:Integer 
derive:self.unit->collect(price)->sum()
end
aggregation Catalog between 
Company [1] 
Product [*]
end 
association ProductUnit between 
Product [1]
Unit [*]
end 
aggregation Stock between 
Company [0..1]
Unit [*]
end 
aggregation orderContent between
Order [0..1]
Unit [1..*]
end 
aggregation Orders between 
Customer [1]
Order [*]
end 

constraints 
context Unit inv InStockOrWithCustomer:
   self.company->size() + self.order->size() = 1
```




ENUNCIADO

The company nozamA sells different products to its customers. To buy a product, the customer must tell the company how many units of that product he wants to buy. The company generates an order if there are enough units of that product in stock. Once an i included in an order, it is no longer in the stock of the company. The order includes the total amount to be paid by the customer, which corresponds to the sum of the prices of the units included in the order. All units must have a serial number. All units of a product must have the same price, which matches the price of the product. An order must contain at least one item. Build a UML class diagram in PlantUML that represents this system. 

@startuml

class Product {

  - serialNumber: String

  - price: Double

  - stock: Integer

}

class OrderItem {

  - product: Product

  - units: Integer

}

class Order {

  - items: List&lt;OrderItem>

  - totalAmount: Double

  + addItem(product: Product, units: Integer)

}

class Customer {

  - placeOrder(product: Product, units: Integer): Order

}

Product &lt;|-- OrderItem

Order &lt;-- OrderItem

Product &lt;|-- Order

Order --> Customer

@enduml


---




## Banks


```
model Banks
enum Gender {male, female, other}
class Person 
attributes
  age:Integer
  name:String
  gender:Gender
end
class Bank
end
class Branch
end
composition BankBranches between 
Bank [1]
Branch [*]
end
class Manager
  attributes
    salary:Integer
end
class Client
end
composition Management between 
  Branch [1]
  Manager [1]
end
composition Clientship between 
  Branch [1]
  Client [*]
end
association ManagerRole between
  Manager [0..1] role manager
  Person [1] role roleFiller
end
association ClientRole between
  Client [0..1] role client
  Person [1] role roleFiller
end
constraints
  context Person inv ManagerOrClient:
self.manager->notEmpty() implies 
    	   self.client.branch->excludes(self.manager.branch)
```




**ENUNCIADO**

Build a UML class diagram in PlantUML that represents a model of banks. Each bank owns a set of branches. Each branch has a manager and a set of customers. The manager has a salary. The roles of manager and customers of a branch are played by persons. Each person has a name, a gender (male, female, other) and an age. The person who plays the role of a branch manager cannot be a customer of that branch.


```
@startuml
class Bank {
  - branches: Set<Branch>
}
class Branch {
  - manager: Manager
  - customers: Set<Customer>
}
class Manager {
  - salary: Double
  - person: Person
}
class Customer {
  - person: Person
}
class Person {
  - name: String
  - gender: Gender
  - age: Integer
}
enum Gender {
  MALE
  FEMALE
  OTHER
}
Bank ---> Branch
Branch ---> Manager
Branch ---> Customer
Manager --> Person
Customer --> Person
@enduml
