[[_ Clean Code]]



# Classes and Data Structures

## Objects vs Data Structures/Data containers

OBJECT | DATA STRUCTURE
-- | --
Private properties | Public properties
public API (methods) | (almost) no API (methods)
contain your business logic | store and transport data
abstraction over concretions | only conretions


CLASS FOR OBJECT
```typescript
class Databasr {
	private uri: string ;
	private provider: any;
	private connection: any;

	constructor(uri: string, provider: any){
		this.uri.uri;
		this.provider=provider;
	}

	connect(){
		try {
			this.connection = this.provider.establishConnection(this.uri);
		}catch(error){
			throw enw Error('Could not connect!');
		}
	}

	disconnect(){
			this.connection.close();
		}



}
```

CLASS FOR DATA CONTAINER
```js
class UserCredentials{
	public email: string ;
	public password: string ;
}
```

CLEAN CODE
```js
const database = new Database('my-database:8080', sqlEngine) ;

database.connect() ;
database.disconnet() ;
```


But you can  ==mix== an object concept and a data container concept, than your code will not be clean:
```typescript
class Databasr {
	private uri: string ;
	private provider: any;
	public connection: any;
```
connection is public, so you can close it by
`database.connection.close()`

## Clean classes should be small
>[!tip]
>You typically should prefer many small classes over a few large classes.
>Classes shoud have a single responsibility ==Single-Responsibility Principle== (SRP).
>Classes can have a lot of methods and attributes but have to focus on one responsiblity!!

e.g.  a `Product` class is responsible for product 'issues' (e.g. change the product name) 

Bad, Big class with a lot of responibilities
```typescript
class OnlineShop {

private orders: any;

private offeredProducts: any;

private customers: any;

public addProduct(title: string, price: number) {}

public updateProduct(productId: string, title: string, price: number) {}

public removeProduct(productId: string) {}

public getAvailableItems(productId: string) {}

public restockProduct(productId: string) {}

public createCustomer(email: string, password: string) {}

public loginCustomer(email: string, password: string) {}

public makePurchase(customerId: string, productId: string) {}

public addOrder(customerId: string, productId: string, quantity: number) {}

public refund(orderId: string) {}

public updateCustomerProfile(customerId: string, name: string) {}

// ...

}
```

many small good classes with one responsibility
```typescript
class Order {

public refund() {}

}

class Customer {

private orders: Order[];

constructor(email: string, password: string) {}

public login(email: string, password: string) {}

public updateProfile(name: string) {}

public makePurchase(productId: string) {}

}

class Product {

constructor(title: string, price: number) {}

public update(Id: string, title: string, price: number) {}

public remove(Id: string) {}

}

class Inventory {

private products: Product;

public getAvailableItems(productId: string) {}

public restockProduct(productId: string) {}

}
```


## Cohesion
How much are your class methods using the class properties?
Maximum Cohesion | No Cohesion
--- | ---
all methods each use all properties  | all methods don't use any class properties
a highly cohesive object | data structure / container with utility methods

THE GOAL IS ==HIGH COHESION==!! You schould write highly cohesive classes.





## the "Law Of Demeter"
>[!bug] Avoid this  classes
>`this.customer.lastPurchase.data ;`
>to much properties in one object
(with data container you can use this long chain of properties)

>[!important] Principle of Least Knowledge
>Don't depend on the internals of "strangers" (other objects which you don't directly know)

**The law of Demeter proposed Ian Holland (1987):**
-   Each unit should have only limited knowledge about other units: only units "closely" related to the current unit.
-   Each unit should only talk to its friends; don't talk to strangers.
-   Only talk to your immediate friends.

An object `a` can request a service (call a method) of an object instance `b`, but object `a` should not "reach through" object `b` to access yet another object, `c`, to request its services. Doing so would mean that object `a` implicitly requires greater knowledge of object `b`'s internal structure.


>[!warning] Law of Demeter
>Code in a method may only access direct internals( poperties and methods) of:
>	- the object it belongs to
>	- objects that are stored in properties of that object
>	- objects which are received as method parameters
>	- objects which are creae in the method

e.g. `this.cusomer.lastPurchase.data` -> `data` breaks the law of Demeter



## SOLID PRINCIPLeS

==S==   Single Responsibility  Principle - imporant to clean code
==O==  Open-Closed Principle - important to clean code
==L==   Liskov Substitution Principle
==I==    Interface Segragation Principle
==D==  Dependency Inversion Principle


### Single-Responsibility-Principle (SRP)

> Classes  should have  a single  responsability - a class shouln't  change for more than one reason

In that code you violate a SRP:
```typescript
class ReportDocument{
	generateReport(data: any){}

	createPDF(report: any){}
}
```
generate report - ONE RESPONSIBILITY:
- pulling data,
- connectiong data
- ...

generate PDF - OTHER RESPONSIBILITY:
- make layout
- number of pages
- presentatial logic

good code:
```typescript
class User{
	
	login(email: string, password: string);
	
	signup(email: string, password: string);

	assignRole(role: any) {} ;
}
```

One responsibility: user authentication (it is depends on the app logic)

>[!important]
>- Restricting classes to one core responsibility leads to smaller classes.
>-  Smaller classes tend to be easier to read

## The Open-Closed Principle (OCP)

>[!important] OCP
> A class should be **open for extension** but **closed for modification**.

this class has a one responsibility but it is not closed for modification (new kind of data -> new method to print that data)
```typescript
class Printer{
	printPDF(data: any){}

	printWebDoc(data: any){}

	printPage(dat: any){}

	verifyData(data: any) {}
}
```

polimorphism helps to close classes to modification
Printer class is closed but you can write a new class that extends that Printer class
```typescript
  
interface Printer {

print(data: any);

}

class PrinterImplementation {

verifyData(data: any) {}

}

class WebPrinter extends PrinterImplementation implements Printer {

print(data: any) {

// print web document

}

}

class PDFPrinter extends PrinterImplementation implements Printer {

print(data: any) {

// print PDF document

}

}

class PagePrinter extends PrinterImplementation implements Printer {

print(data: any) {

// print real page

}

}
```

>[!info]
> - Extensibility ensures small class (instead of  growing classes) and can help prevent code duplication (DRY).
> Smaller classes and DRY code increase readability and maintainability





## Liskov Substitution Principle

>[!important] Liskov Substitution Principle
>Objects should be replaceable with instances of their subclasses without altering the behavior

e.g.
```js
class Bird{
	fly(){
		console.log('Flying...') ;
	}
}

class Eagle extends Bird {
	dive(){
		console.log('Diving...') ;
	}
}

const bird = new Bird();
bird.fly()

const eagle = bew Eagle();
eagle.fly();
eagle.dive() ;

// the eagle can relace the bird

class Penguin extends Bird{
	// Problem: ca't fly

}


```

To fix this problem:
- make a new class `FlyingBird` and delete a `fly` method from `Bird` class
- `Eagle` extends `FlyingBird`
- `Pinguine extends Bird`

## Interface Segragation Principle (ISP)
> Many client-specific interfaces are better than one general purpose interface

>[!info] interface
>It is a contract which force classes to implement certain behaviors

```typescript
// too many use cases (connectiong and storing data)
interface Database{
	connect(uri: string) ;
	storeData(data: any) ;
}

class SQLDatabase implements Database {
 connect(uri: string ){
	 // some implementations
 }

 storeData(data: any){
	 // some implementations
 }
}
```
and now we create a new database class:
```typescript
class InMemoryDatabase implements Database {
	connect(uri: string){
		// ???
	}
	storeData(uri: string){
		// some implementation
	}
}
```

TO FOLLOW  ISP:
```typescript
// too many use cases (connectiong and storing data)
interface Database{
	storeData(data: any) ;
}

interface RemoteDatabase{
	connect(uri: string) ;
}
class SQLDatabase implements Database, RemoteDatabase{
 connect(uri: string ){
	 // some implementations
 }

 storeData(data: any){
	 // some implementations
 }
}

class InMemoryDatabase implements Database {
	storeData(uri: string){
		// some implementation
	}
}
```

## Dependency Inversion Principle (DIP)
> You should depend upon abstractions, not concretions

```typescript
// too many use cases (connectiong and storing data)
interface Database{
	storeData(data: any) ;
}

interface RemoteDatabase{
	connect(uri: string) ;
}
class SQLDatabase implements Database, RemoteDatabase{
 connect(uri: string ){
	 // some implementations
 }

 storeData(data: any){
	 // some implementations
 }
}

class InMemoryDatabase implements Database {
	storeData(uri: string){
		// some implementation
	}
}

// this class depends on concretions
class App{
	private database: SQLDatabase | InMemoryDatabase;

contructor(databse: SQLDatabase | InMemoryDatabase){
	if(database instanceof SQLDatabase){
			database.connect('my-url');
		}
	this.database = database;
saveSetting(){
	this.database.storeData('Some data');
	}
}
```

after
```typescript
// this class depends on abstraction -> on interface Database
class App{
	private database: Database ;

contructor(databse: Database){
	
saveSetting(){
	this.database.storeData('Some data') ;
	}
}

const sqlDatabase = new SQLDatabase() ;
sqlDatabase.connect('my-url') ;
const app = new App() ;
```










