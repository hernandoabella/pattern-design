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

## abstract factory

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
          
now, consider that you need to support more shape types and more OSes. that would lead to a significant number of classes being 0added - the number of types multiplied by the numer of OS versions.

so, basicallly, to support five shape types on three different OSes, you would need to write 5*3=15 implementations.

however, the bridge pattern suggets refactoring this into two separate hierarchies - one for platform-independent abstractions (shapes), and the other for platform-dependent implementations (Oses).

here is a refactored diagram:

      shape                  shapeimplementation
      
 rectangle  circle      windows             macos     
          
          
the relationship between shape and shapeimplementation is the bridge.

this pattern is used in situations where it would be best to isolate the handling of the system-dependent stuff from the handling of the system-independent stuff.

the bridge pattern is oftten confused with the adapter pattern.

adapter makes things work after they're designed; bridge is designed up-front to let the abstracction and the implementation vary independently. further, adapter is retrofitted to make unrelated classes work together. 

in other words, an adapter is a patch. a bridge is put in place on purpose.


## composite

the composite pattern describes a group of objects that is treated the same way as a single instance of the same type of object.

composite should be used when clients ignore the difference between compositions of objects and individual objects.

for example, when dealing with tree-structured data, programmers often must discrimate between a leaf-node and a branch. this makes code more complex, and therefore, more error-prone.

the solution is an interface that allows treating complex and primitive objects uniformly.

other examples are menus that contain menu items, each of which could be a menu. directories that containe files, each of which could be a directory.

the key concept is that you can manipulate a single instance of the object just as yo would manipulate a group of them.

## decorator

the decorator design pattern allows behavior to be added to an individual object, either statically or dynamically, without affecting the behavior of other objects from the same class.

this is achieved by designing a new decorator class that wraps the original class. this pattern is designed so that multiple decorators can be stacked on top of each other, each adding a new functionality.

the goal is to mkae it so that the extended behavior can be applied to one specific instance, and, at the same time, still be able to create an original instance that doesn't have the new behavior.

this pattern is an alternative to subclassing, which refers to creating a class that inherits functioanlity from a parent class. as opposed to subclassing, which adds the behavior at compile time, "decorating" allows you to add new behavior during runtime, if the situation calls for it.

for example, consider a window in a windowing system. assume windows are represented y instances of the window class, and assume this class has no functionality for adding scrollbars.

we could create a subclass scrollingwindow that provides them, or create a scrollingwindowdecorator that add this functionality to existing window objects. at this poin, either solution would be fine.

now, assume one also desires the ability to add borders to windows. if we had used subclassing then we have a problem , as we will need to create separate subclasses with the borders functionality for all possible types of windows.

with the decorator, we have the ability to add scrollbars and/or borders to any of our windows objects.

notice that if the functionality needs to be added to all windows, you could modify the base class and that will do. however, sometimes (e.g., when using external frameworks) it is not possible, legal, or convenient to modify the base classs.

the I/O streams implementations of both Java and the .NET framework follow the decorator pattern by exteding the base subclass to add features to the stream classes.

## facade

the facade design pattern provides a unified interface to a set of interfaces in a subsystem, thus making a complex subsystem easier to use.

a facade is an object that provides a simplified interface to a larger body of code, such as a class library.

a facade can:

- make a software library easier to use, understand, and test, since the facade has convenient methos for common tasks,

- make the library more readable, 

- wrap a poorly designed collection of APIs with a single well-designed API.

The facade design pattern is often used when a system is very complex or difficult to understand because the system has a large number of interdependent classes or its source code is unavailable. this pattern hides the complexities of the larger system and provides a simpler interface to the client. it typically involves a single wrapper class that contains a set of members required by the client.

these members access the system on behalf of the facade client and hide the implementations details.

the # in jquery, which provides a simple interface to common operations, is an example of the facade design pattern.

adapter and facade are both wrappers, but they are different kinds of wrappers. the intent of facede is to produce a simpler interface, and the intent of adapter is to design an existing interface.

## flyweight 

the flyweight design pattern efficiently supports a large number of objects.

a flyweight is an object that minimizes memory usage by sharing as much data as possible with other similar objects; it is a way to use objects in large numbers when a simple repeated representation would use an unacceptable amount of memory.

for example, when representing large teext documents, creating an object for each character in the document would result in a huge number of objects that could'nt be processed efficiently. insted, for every character there might be a reference to a flyweight glyph object shared by every isntance of the same character in the document; only the position of each ccharacter in the document would need to be stored internally.

as another example, modern web browsers use this technique to prevent loading the same images twich. when browser loads a web page, it traverses throught all images on that page. the browser loads all new images an places them in the internal cache.

for already loaded images, a flyweight object is created, which has some unique data-like position whithin the page, but the image itself is referenced from the cache.

to enable safe sharing between clients and threads, flyweight objects must be immutable.

flyweight objects are by definition value objects. the identity of the object instance is of no consequence; therefore, two flyweight equal.

## proxy

the proxy design pattern provides a placeholder for another object to control access to it.

a proxy is a class functionaning as an interface to something else, such as a network connection, a large object in memory, a file, or some other resource that is expensive or impossible to duplicate.

a proxy acts as a wrapper object that is being called by the client to access the real serving object behind the scenes. for the client, usage of a proxy object is similar to using the real object, because both implement the same interface.

possible usage scenarios.

### remote proxy

in distributed object communication, a local object represents a remote object. the local object is a proxy for the remote object, and method invocation on the local object results in remote method invocation on the remote object. an example would be an atm implementation, where the atm might hold proxy objects for bank information that exists in the remote server.

### virtual proxy

in place of a complex or heavy object, a skeleton representation may be advantageous in some cases.

when an underlying images is huge in size, it may be represented using a virtual proxy object, loading the real object on demand.

### protection proxy

a protection proxy might be used to control access to a resource based on access rights.

a proxy can:

- hide information about the real object form the client.

- perform optimization like on-demand loading.

- do additional housekeeping jobs like audit tasks.



