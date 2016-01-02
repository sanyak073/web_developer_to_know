# Most popular interview's questions for .Net Web Developer position

Design pattern can separate 3 important parts:
    Creational Patterns
    Structural Patterns
    Behavioral Patterns

Creational patterns patterns have to do with class instantiation. They can be further divided into class-creation patterns and object-creational patterns. While class-creation patterns use inheritance effectively in the instantiation process, object-creation patterns use delegation to get the job done.

Structural patterns concern class and object composition. They use inheritance to compose interfaces and define ways to compose objects to obtain new functionality.

Behavioral patterns Most of these design patterns are specifically concerned with communication between objects.

#Creational patterns
  Abstract factory (recognizeable by creational methods returning the factory itself which in turn can be used to create another abstract/interface type)
  Builder (recognizeable by creational methods returning the instance itself)
  Factory method (recognizeable by creational methods returning an implementation of an abstract/interface type)
  Prototype (recognizeable by creational methods returning a different instance of itself with the same properties)

#Structural patterns
  Adapter (recognizeable by creational methods taking an instance of different abstract/interface type and returning an implementation of own/another abstract/interface type which decorates/overrides the given instance)
  Bridge (recognizeable by creational methods taking an instance of different abstract/interface type and returning an implementation of own abstract/interface type which delegates/uses the given instance)
  Composite (recognizeable by behavioral methods taking an instance of same abstract/interface type into a tree structure)
  Decorator (recognizeable by creational methods taking an instance of same abstract/interface type which adds additional behaviour)
  Facade (recognizeable by behavioral methods which internally uses instances of different independent abstract/interface types)
  Flyweight (recognizeable by creational methods returning a cached instance, a bit the "multiton" idea)
  Proxy (recognizeable by creational methods which returns an implementation of given abstract/interface type which in turn 

#Behavioral patterns
  Chain of responsibility (recognizeable by behavioral methods which (indirectly) invokes the same method in another implementation of same abstract/interface type in a queue)
  Command (recognizeable by behavioral methods in an abstract/interface type which invokes a method in an implementation of a different abstract/interface type which has been encapsulated by the command implementation during its creation)
  Interpreter (recognizeable by behavioral methods returning a structurally different instance/type of the given instance/type; note that parsing/formatting is not part of the pattern, determining the pattern and how to apply it is)
  Iterator (recognizeable by behavioral methods sequentially returning instances of a different type from a queue)
  Mediator (recognizeable by behavioral methods taking an instance of different abstract/interface type (usually using the command pattern) which delegates/uses the given instance)
  Memento (recognizeable by behavioral methods which internally changes the state of the whole instance)
  Observer (or Publish/Subscribe) (recognizeable by behavioral methods which invokes a method on an instance of another abstract/interface type, depending on own state)
  State (recognizeable by behavioral methods which changes its behaviour depending on the instance's state which can be controlled externally)
  Strategy (recognizeable by behavioral methods in an abstract/interface type which invokes a method in an implementation of a different abstract/interface type which has been passed-in as method argument into the strategy implementation)
  Template method (recognizeable by behavioral methods which already have a "default" behaviour definied by an abstract type)
  Visitor (recognizeable by two different abstract/interface types which has methods definied which takes each the other abstract/interface type; the one actually calls the method of the other and the other executes the desired strategy on it)

#MVC/MVVM is not an either/or choice.
The two patterns crop up, in different ways, in both ASP.Net and Silverlight/WPF development.

For ASP.Net, MVVM is used to two-way bind data within views. This is usually a client-side implementation (e.g. using Knockout.js). MVC on the other hand is a way of separating concerns on the server-side.

For Silverlight and WPF, the MVVM pattern is more encompassing and can appear to act as a replacement for MVC (or other patterns of organising software into separate responsibilities). One assumption, that frequently came out of this pattern, was that the ViewModel simply replaced the controller in MVC (as if you could just substitute VM for C in the acronym and all would be forgiven)...

The ViewModel does not necessarily replace the need for separate Controllers.
The problem is: that to be independently testable*, and especially reusable when needed, a view-model has no idea what view is displaying it, but more importantly no idea where its data is coming from.

*Note: in practice Controllers remove most of the logic, from the ViewModel, that requires unit testing. The VM then becomes a dumb container that requires little, if any, testing. This is a good thing as the VM is just a bridge, between the designer and the coder, so should be kept simple.

Even in MVVM, controllers will typically contain all processing logic and decide what data to display in which views using which view models.

From what we have seen so far the main benefit of the ViewModel pattern to remove code from XAML code-behind to make XAML editing a more independent task. We still create controllers, as and when needed, to control (no pun intended) the overall logic of our applications.

The basic MVCVM guidelines we follow are:
    Views display a certain shape of data. They have no idea where the data comes from.
    ViewModels hold a certain shape of data and commands, they do not know where the data, or code, comes from or how it is displayed.
    Models hold the actual data (various context, store or other methods)
    Controllers listen for, and publish, events. Controllers provide the logic that controls what data is seen and where. Controllers provide the command code to the ViewModel so that the ViewModel is actually reusable.
    We also noted that the Sculpture code-gen framework implements MVVM and a pattern similar to Prism AND it also makes extensive use of controllers to separate all use-case logic.

An additional benefit of using an MVCVM model is that only the controller objects need to exist in memory for the life of the application and the controllers contain mainly code and little state data (i.e. tiny memory overhead). This makes for much less memory-intensive apps than solutions where view-models have to be retained and it is ideal for certain types of mobile development (e.g. Windows Mobile using Silverlight/Prism/MEF). This does of course depend on the type of application as you may still need to retain the occasional cached VMs for responsiveness.
