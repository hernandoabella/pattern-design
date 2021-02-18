# Patrones de Diseño

Design patterns are optimized, reusable solutions to the programming problems that we encounter every day.

a design pattern is a description, or template, for how to solve a problem that can be used in may different situations. it's not a language-specific. A good design pattern should be implementable in most if not all languages, depending on the capabilities of the language.

there are three basic kinds of design patterns:

creational

abstract factory, builder, factory method, object pool, prototype, singleton.

structural

adapter, bridge, composite, decorator, facade, flyweight, proxy.

behavioral

chain of responsibility, command, interpreter, iterator, mediator, memento, observer, state, strategy, template method, visitor.

generally, the three groups above define how your program eleemnts relate to each other, how they gt created, and how they communicate with each other.

why use them?

design patterns are well-thought out solutions to programming problems. let's draw a parallel with a real-world example. suppose you are standing at the base of a mountain and have been given the task of reaching its top by the end of the day. assuming that you are unaware of the available routes to the montain top0, what will you do? of course, you will start to climb up as per you own understanding. your lack of knowledge about the right route makes it extremely difficult for you to decide the beest possible route.

if somebody gives you a detailed map along with all posible routes, including the pros and cons of each, then you will be in a much better position to begin your journey and choose the right route.

simply put a design pattern is a proven solution to solve design problems.


## singleton design pattern

singleton is a creating design pattern, which ensures that only one instance of a class is created.

singleton may be used when:

- you need access to a shared resource.
- access to a shared resource will be requested from multiple, separate parts of your program.
- only one object can be instantiated.

a good example is a llegger, which is used in every part of the system to log some information. for example, in a social network, every activity of a user should be logged (login, logout, comment, posts, likes).

instead of instatiating a new logger instance over and over again for each activity type, it would be better to have a single instance and access it when neededd. in other words, it is better to use the same logger instance to log user llogins, logouts, comments, posts, and likes, when necessary.

singletons are inteded to be used when a class must have exactly one instance, no more, no less.

## factory method 

factory method is a creational pattern that defines an interface for creating an object, but lets subclasses decide which class to instantiate.

the best time to use the factory method pattern is when you have multiple variations of a single entity.
for example, let's consider a program that creates different shapes. for this program, we need to define a shapefactory tyhat will act as a common, interface for creating shapes. using this interface each subclass will create the specific shape by implementing the shapefactory's corrisponding "create" method.

to better understand the factory method concept, consider a real-world employment agency. the agency helps clients fill positions for their company.

the client provides the hinring criteria and then leaves the details of assessing candidates to the agency. the giring agency takes care of a potential candidates's eleigibility, skill, and experience verification to ensure that the candidate matches the hiring criteria. in this case, the hiring agency acts as the ffactory. it allows the client to creates new objects without having to know the details of how they're created.

we created objects without exposijng the creating logic to the client and refere  to newly created objects usign a common interface (employment agency).

the factory method pattern relies on inheritance, as object creating is delegated to subclases that implement the factory method to create objects.

the factory method is usually used when creating frameworks, which standadize the architectural model for a range of applications, but allow for individual applications to define their own objects and their instantiation.

a Factory is a creator of objects that have a common interface.

## abstrac factory

the abstract factory is a creational pattern, similar to the factory method patetern, with the key difference being that abstract factory privides and interface for creating families of related or dependent objects without specifing their concrete classes.

often, design start out using factory method and envolve toward abstract factory as more flexibility is needed.

imagine an application needs to run on different operating systems. in order to achive this, we need to encapsulate the dependencies of our application. 

one approach is to have a "factory" object that has the responsibility of providing creating services for the entire platform family. each time we need a new object for our application, we use the factory.

this makes a class independient of how its objects are created (which concrete classes are instantiated).

consider a "factory" to create ui elements. the same factory can create buttons, textboxes, windows, and other elements for two operating systems - windows and macos.

when we want to create a new button, we do not instantiate a new button class for a particular operating system. insted, we request the factory create a button, and the factory does so, considering the parameters of the operating system. the same applies for any other ui object. as a result, we get the object we need without getting into detail of how the objects are created.

bassically, the abstract factory pattern provides a way to encapsulate a group of individual factories that have a common theme without specifying their concrete classes.

because the service provided by the factory object is so pervasive, it is a routinely implemented as a singleton.

## builder

the builder design pattern is a creational pattern that sepaates the construction of a complex object from its representationction process can create different representations.

simply said, it builds a complex object using simple objects and a step-by-step approach.

for example, let's say we need to build cars. each car has many options. the combination of groups would lead to a huge list of constructos for the car class. to avoid this, we will create a builder class, carbuilder, we will send each option step by step to the carbuilder and then construct the final car with the correct options.

this approach makes it flexible to add and remove options from the car.
sometimes creational patterns are complementary: builder can use one of the other patterns to implement which components are built.

## object pool

the object pool design pattern is useful when it is necessary to work with a large number of objects that are particularly expensive to instatiate, especially if each object is only needed for a short period of time.

instead of creating and destroying the expensive objects, the object pool pattern sugges reusing the already created objects.

when a new object is needed, it is requested from the poool. if a previously prepared object is available it is returned immediately, avoiding the instantiation cost. if no objects are present in the pool, a new item is created and returned. when the object has been used and is no longer needed, it is returned to the pool, allowing it to be used again in the future without repeating the expensive instantiation process.

for example, the object pool design pattern is used in the .NET framework data provider for sql server. as sql server database connections can be slow to create, a pool of conections is maintained. when yuo close a connection, the connection is held in a new connection. this substantially inscreases the speed of making connections.

object pools are usually implemented as singletons.

## prototype 

the prototype design pattern is a creational pattern that uses a prototype to create new objects by copying this prototype. in other words, inseted of creating new objects, we clone them from the prototype.

the pattern is used when object creation is resource expensive. by clonning new object in the standard way.

mitiotic cell division, which results in two identical cells, is an example of the prototype pattern. when a cell splits, two cells of identical genotype result. in other words, the cell clones itself.

prototype is unique among the other creational patterns as it doesn't require a class - only an object.

## adapter

the adapter pattern is a structural design pattern that allows the interface of an existing class to be used as another interface. it is often used to make existing classes work with other without modifying their source code.

for example, let's consider you have an old class that implements some functionality needed in your new project. however, the way it is written is not compatible with the philosophy and architecture of the system currently being developed. in order to use the old class without rewriting the whole functionality from scratch, we can create an adapter, also called a wrapper, that translates, or maps, the old component to the new system.

your program will then call the wrapper, which will redirect to the corresponding methods in the old class.

the key idea in this pattern is to work through a separeted adapter that adapts the interface of an already exisintg class without changing it.

## bridge 

the bridge pattern is designed to separate the abstraction from the implementations so they can be used and changed independently.

let's look at an example to understand when this is useful and wht this "confusing" definition means.

say you need to create a shape drawigin application that should work on both windows and macos.

you could create a shape interface, inherit from it the types of the shapes, like rectangle or cirlce, and then inherit from those to create the os-specific implementations.

the class hierarchy would look like this:

                    
                  shape
              rectangle         circle
              
          winrect marcrect   wincircle maccircle
          
          

