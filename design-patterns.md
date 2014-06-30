## Composite

### Purpose

Compose objects into tree structures to represent part-whole hierarchies.
Composite lets clients treat individual objects and compositions of objects
uniformly.

### Key Concepts

1.  Use an abstract class to represent both primitives and their containers
2.  Subclasses share common action methods
3.  Leaf classes simply execute their own action methods
4.  Composite classes execute all composite oject action methods, recursively

### Applicability

1.  You want to represent part-whole hierarchies
2.  Want clients to be able to ignore difference between compositions of objects
    and individual objects. Clients will treat all objects in the composite
    structure uniformly.

### Consequences

#### Pros

1.  Recursive composition structures allow clients to accept a composite object
    wherever they would expect a primitive one.
    1.1 Simplifies client code by reducing number of implementation cases
    1.2 Makes it easier to add new kinds of components; no changes to clients

#### Cons

1.  Can overly generalize your design; hard to constrain the types of
    componenets a composite can have.

### Implementation

1.  Explicit parent references
2.  Sharing components
3.  Maximizing Component interface
4.  Declaring the child management operations
5.  Should Component implement a list of Components?
6.  Child ordering
7.  Caching to improve performance
8.  Who should delete components?
9.  What's the best data structure for storing components?

## Chain of Responsibility (CoR)

### Purpose

Avoid coupling the sender of a request to its receiver by giving more than one
object a chance to handle the request. Chain the receiving objects and pass the
request along the chain until an ojbect handles it.

### Key Concepts

1.  Decouple sender from reciever by constructing a chain
    1.1 sender passes request to successor, recurse from there
    1.2 each successor gets a chance to handle request if capable
    1.3 implicit receiver: sender doesn't know who will handle it in advance

### Applicability

1.  More than one object may handle a request, and the handler isn't known a
    priori -- should be ascertained automatically.
2.  You want to issue a request to one of several objects without explicitly
    specifying the reciever.
3.  The set of objects that can handle a request should be specified
    dynamically.

### Consequences

#### Pros

1.  Reduced coupling -- frees sender from knowing about receiver
2.  Added flexibility in assigning responsibilities to objects -- dynamically
    changing the chain at runtime makes it highly configurable.

#### Cons

1.  Receipt isn't guaranteed -- request can fall off end of chain

### Implementation

1.  The successor chain
2.  Connecting successors
3.  Representing requests

### Similar ideas

1.  Event propogation in the DOM
    1.1 event-driven programming in general

## Command

### Purpose

Encapsulate a request as an object, thereby letting you parameterize clients
with different requests, queue or log requests, and support undoable operations.

### Key Concepts

### Applicability

1.  Parameterize objects by an action to perform
    1.1 Commands are an OO replacement for callbacks
2.  Specify, queue, and execute requests at different times
    2.1 Command object can have lifetime independent of original request
3.  Support undo; command can store state for reversal and a history of commands
    can be used to reverse one or more at a time.
    3.1 Usually need extra methods, such as load, store, unexecute, etc.
4.  Architect a transaction-oriented system.

### Consequences

#### Pros

1.  decouples the object that invokes the operation from the one that knows how
    to perform it.
2.  Commands become first-class objects, which can be subclassed and
    manipulated.
    2.1 Easy to add new commands; no need to change existing classes.
3.  Can assemble commands into Composite commands using the composite pattern.

#### Cons

1.  Can be too heavy-weight when commands are very simple.

### Implementation

1.  How intelligent should a command be?
2.  Should undo/redo be supported?
3.  Avoiding error accumulation in the undo process.

