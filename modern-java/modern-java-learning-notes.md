# Modern Java Learning Notes

## Basics

- Primitive Types:
  - `int` (`byte`, `short`, `long`) default value (only if the primitive type is an instance field) 0
  - `double` (`float`) default value (only if the primitive type is an instance field) 0.0
  - `char` default value default value (only if the primitive type is an instance field) 0x0
  - `boolean` default value default value (only if the primitive type is an instance field) false
- `String` default value default value (only if the primitive type is an instance field) null
- Unlike instance fields, local variables inside a method must to be initialized before they are used. Otherwise, the compiler will throw an error.
- Literals: `0, 21.3, 'c', "Hello"` and `true` are literals
- Variables: `int x = 23;` makes x a variable
- Arrays and Array initialization
  - `int[] x = new int[N]`
  - `double[] y = {1.1, 2.3, 4.5}`
  - `Integer[] z = new Integer[]{ 1, 2, 3}`
  - In the cases of initialization, the final comma in the list of initializers is optional
- `ArrayList<T>`
- Operators
  - Arithmetic: `+`, `-`, `*`, `/`, `%`
  - Relational: `>`, `>=`, `<`, `<=`, `==`, `!=`
  - Logical: `&&`, `||`, `!`
- Control Flow
  - `if-else if-else`
  - `switch`
  - `for( ; ; )`
  - `for (var : collection)`
- Console Input/Output
  - `System.out`
  - `System.in`
  - `Scanner`
- Varargs
  - `void add(int... num)`
  - When the `add` method is called, you do not "need" to pass an array of `int`. The compiler takes care of that. However, if you already had an array of `int`, you could pass that as well
  - Varargs works with primitive types (does not depend on autoboxing) just as well as it works with class types.
  - Array Class Type: `class [Ljava.lang.Character;` (for array of class `Character`) or `class [Ljava.lang.Integer;` (for array of class `Integer`) or `class [I` (for array of primitive `int` type). Notice no semi-colon for primitive int array types
  - Varargs do tend to make method overloading difficult. Or at least, error prone.
- You can create a `main()` for each of your classes; this allows easy testing for each class. You don’t need to remove the `main()` when you’re finished; you can leave it in for later testing. Even if you have many classes in a program, the only `main()` that runs is the one invoked on the command line. Even if a class has `package` (read, default) access, a `public main()` is accessible. In particular cases you might have to make adjustments, but this is a useful guideline.

## Enumerations

- `enum` may appear to be a new data type. However, `enum` is a class that have their own methods (`ordinal()`, `values()` etc.)
- `enum` names can produce a much clearer expression of intent.
- Can be used in `switch` statements

## Object-Oriented Programming

- OOP Concepts:
  - Encapsulation: Wrapping data and methods within classes in combination with implementation hiding is called encapsulation
  - Abstraction: All programming languages are abstractions. Assembly language is a minimal abstraction of the underlying machine. Many so-called "imperative" languages (such as FORTRAN, BASIC, and C) were themselves abstractions of assembly language. Bottom line, abstraction's main goal is to handle complexity by hiding unnecessary details from the user. OOP provides a more flexible and powerful language abstraction. How? Similar to a Car that you drive, you just need to know which methods of the object are available to call and which input parameters are needed to trigger a specific operation. You don’t need to understand how this method is implemented and which kinds of actions it has to perform to create the expected result.
  - Inheritance: As the name suggests, in OOP, a class can inherit methods from a _parent_ class and extended.
  - Polymorphism: Also called Dynamic Binding, Late Binding or Runtime Binding. As we discussed, inheritance allows you to create class hierarchies, where a base class gives its behavior and attributes to a derived class. You are then free to modify or extend its functionality. Polymorphism ensures that the proper method will be executed based on the calling object’s type. It allows creation of _extensible programs_ that can be "grown" not only during the original creation of the project, but also when new features are desired.
- _An object has state, behavior and identity (Grady Booch)_. This means an object can have internal data (which gives it state), methods (to produce behavior), and each object is uniquely distinguished from every other object—that is, every object has a unique address in memory.
- **Basics**
  - `<access-specifier> class Name`
  - `new ClassName(args list...)` to instantiate a class
  - A `class` is basically a special kind of custom `type` (instead of being pre-defined types that come with Java language) that we create which comes with two types of elements or members:
    - fields (think, state), sometimes called _data members_
    - methods (think, behavior), sometimes called _member functions_
  - When you see the word `class` think type and vice-versa.
  - Each object has a state, behavior and identity
  - The order of the fields defined within a class determines the order of initialization
  - The field definitions can be scattered throughout and in between method definitions, but the fields are initialized before any methods can be called, even the constructor!
  - `this`
    - When used, it is in the sense of "the current object". As a result, it can only be used in non-static methods
- **Constructors:**
  - If you create a class that has no constructors, the compiler will automatically create a no-arg constructor for you
  - However, if you define any constructors (with or without arguments), the compiler will **NOT** synthesize one for you
  - Constructor looks like a Java method, except it does **NOT** have a return type
  - Also, the convention of having Java method names starting with a lowercase first letter does not apply in the case of constructors
  - Inside a constructor, the `this` keyword takes on a different meaning when you give it an argument list. It makes an explicit call to the constructor that matches that argument list
    - `this(args list)` call must be the first thing you do inside the constructor
    - Cannot use `this(args list...)` more than once inside a constructor!
    - Cannot use `this(args list...)` inside a non-constructor Java method
- **Static Members (Fields and Methods)**
  - Class level, as opposed to instance/object level member
  - Don't need an object reference to call `static` methods
  - You can call `static` methods from instance/object of that class (or another class, provided you have access), but cannot call `non-static` methods or fields from `static` methods
  - Even though it does not explicitly use the `static` keyword, the constructor is actually a `static` method.
  - `static` initialization: Order of initialization is `statics` first, then the non-static objects. The first time you create an object of type _C_ or the first time you access a static method or static field of class _C_, the Java interpreter must locate the _C.class_ which it does by searching through the classpath. As the _C.class_ is loaded (creating a _Class_ object), all of its static initializers are run. Thus, static initialization takes places only once, as the _Class_ object is loaded for the first time
  - Instance Variables
  - Instance Methods
  - Explicit `static` initialization (also called `static` block). It looks a little like a method, but it's just the `static` keyword followed by a block of code. This code, like other `static` data initializations, is executed only once: the first time you make an object of that class or the first time you access a `static` member of that class (even if you never make an object of that class)
  - `non-static` instance initialization. These guarantee that certain operations occur regardless of which explicit constructor is called
- **Method Overloading**
  - Each overloaded method MUST have the same name (duh) and must take a unique list of argument types
  - Return types does not matter in deciding whether a method is overloaded or not
  - Only non-private methods can be overridden
  - The @Override annotation prevents you from accidentally overloading
  - There is no such thing as field overloading. When a `Derived` class names a field (say, `var1`) with the same name as the `Parent` class, the `Derived` class ends up getting two fields (`var1`) by the same name. You can access the `var1` variable of the `Parent` class by using `super.var1`.
- **Static Nested Class** is a class (think, type) inside another class. A static nested class is simply one that is declared as `static`, thereby ensuring that the type is a class type, not a member type
  - Each static nested class object does not have a reference to the object of the enclosing class, just like a static method does not have the `this` reference
  - Use a static nested class when the instances of the nested class don’t need to know to which instance of the enclosing class they belong.
- **Inner Class** is also a class inside another class, except it is an instance type and not a class type.
  - Each inner class object has a reference to an object of the enclosing class. That means an instance method of an inner class can access instance variables of its outer class.
  - Use an inner class when the instances do need to know to which instance of the enclosing class they belong.
- **Local class** is a class defined inside a method. You would do this for classes that are just tactical. This occurs often when a class implements an interface and the caller of the method only cares about the interface, not the class.
  - Advantages of Local Class:
    - Class name is hidden in the scope of the method
    - The methods of the class can access variables from the enclosing scope, just like the variables of a lambda expression.
- **Anonymous Class** is also a class defined inside a method, except it does not have any name. The expression `new Interface() { methods }` means define a class implementing the interface that has the given methods, and construct one object of that class
  - the `()` in the `new` expression indicate the construction arguments. A default constructor of the anonymous class is invoked
  - Before Java had lambda expressions, anonymous inner classes were the most concise syntax available for providing runnables, comparators, and other functional objects.
- **Garbage Collection/Cleanup:**
  - Garbage collection is only about memory.That is, the sole reason for the existence of the garbage collector is to recover memory your program is no longer using.
  - Java's GC only knows how to release memory allocated with `new`
  - The need for `finalize()` is limited to special cases where your object can allocate storage in some way other than creating an object. But, you might observe, everything in Java is an object, so how can this be?
  - It would seem that `finalize()` is in place because you might do something C-like by allocating memory using a mechanism other than the normal one in Java. This can happen primarily through native methods, which are a way to call non-Java code from Java.
  - Java doesn’t allow you to create local objects (on the stack) — you must always use `new`. So, they are always created on the heap.
  - Bottom line, you won’t use `finalize()` much since you won't, in all likelihood, be interacting with non-Java code inside your Java code. "...Finalizers are unpredictable, often dangerous, and
    generally unnecessary" - Joshua Bloch
  - Types of GC approaches:
    - stop-and-copy
    - mark-and-sweep
    - Adaptive generational stop-and-copy mark-and-sweep
- **Code Organization in Java**
  - If you’ve programmed with a compiled language, you might be used to the compiler spitting out an intermediate form (usually an “obj” file) that is then packaged together with others of its kind using a linker (to create an executable file) or a librarian (to create a library). That’s **NOT** how Java works.
  - A working program is a bunch of `.class` files, which can be packaged and compressed into a Java ARchive (JAR) file (using the jar archiver). The Java interpreter is responsible for finding, loading, and interpreting these files.
  - A library in Java is a group of these `.class` files. Each source file usually has a `public` class and any number of non-public classes, so there’s one public component for each source file. To say that all these components belong together, use the `package` keyword.
  - If you use a `package` statement, it must appear as the first non-comment in the file.
  - In other words, a Java `package` contains a group of classes, organized under a single namespace
  - Note that the convention for Java package names is to use all lowercase letters, even for intermediate words.
  - To import a single class from a `package`, you use the `import` keyword. For example, `import java.util.ArrayList`. Note: By using this particular `import` statement, class `ArrayList` is available for us. That said, none of the other classes from `java.util` package are. To import everything, you could use `import java.util.*`.
  - The `package` and `import` keywords divide up the single global namespace so names don’t clash.
- **Access Modifiers:**
  - The class controls the code that has access to its members.
  - If you don’t provide an access specifier, it means “package access.” So one way or another, everything has some kind of access control.
  - For the record, there is no keyword for package access. It means that all the other classes in the current package have access to a member with no access modifier. To all the classes _outside_ of this package, the member appears as private.
  - Package access is one reason for grouping classes together in a package
  - A compilation unit — a file — can belong to only a single package so all the classes within a single compilation unit are automatically available to each other via package access.
  - `public`: Any Java class can access the field and/or method declared `public` in this class
  - `private`: No Java class, other than members in the same class, can access fields and/or methods declared `private` in this class. Any method that you’re certain is only a “helper” method for that class can be made `private`
  - `protected` (think, _Inheritance_ access): Sometimes the creator of the base class would like to take a particular member and grant access to derived classes but not the world in general, _regardless of whether the derived classes are in the same package as the base class_. That’s what `protected` does. `protected` also gives package access—that is, other classes in the same package can access protected elements. The protected keyword is a nod to pragmatism. It says, “This is private as far as the class user is concerned, but available to anyone who inherits from this class or anyone else in the same package.” (protected also provides package access.)
  - Btw, Declaring a constructor `public` inside a package-access class doesn’t actually make it public! The compiler will complain if you tried doing it.
  - Note that a class cannot be `private`
- **Composition, Inheritance and Delegation:**
  - One of the most compelling reasons for object-oriented programming is code reuse.
  - You reuse code by creating new classes, but instead of creating them from scratch, you use existing classes that someone has already built and debugged.
  - Composition is when you create objects of your existing class inside the new class. In other words, the new class is _composed_ of objects of existing classes.
  - Use Composition when you want the functionality of an existing class inside your new class, but not its interface.
  - Inheritance is when you create a new class as a type of an existing class. You literally take the form of the existing class and add code to it without modifying the existing class
  - When you inherit, you take an existing class and make a special version of it. This usually means taking a general-purpose class and specializing it for a particular need.
  - Classes can extend (`extends`) a single parent class at a time
  - `super`
  - An `abstract` class is a class which includes one or more method which is of type _abstract_. The method has no concrete implementation
  - The `is-a` relationship is expressed with inheritance, and the `has-a` relationship is expressed with composition.
  - It turns out you’re always inheriting when you create a class, because unless you explicitly inherit from some other class, you implicitly inherit from Java’s standard root class `Object`.
  - As a general rule while using inheritance, make all fields `private` and all methods `public`. `protected` members (fields and methods) also allow access by derived classes
  - The construction happens from the base “outward,” so the base class is initialized before the derived-class constructors can access it. Even if you don’t create a constructor for a dervied class, the compiler will synthesize a no-arg constructor for you that calls the base-class constructor.
  - The call to the base-class constructor must be the first action inside the derived-class constructor.
  - Delegation is midway between inheritance and composition, because you place a member object in the class you’re building (like composition), but at the same time you expose all the methods from the member object in your new class (like inheritance). Delegation is not organically supported by Java.
  - Although the compiler forces you to initialize the base classes, and requires you do it right at the beginning of the constructor, it doesn’t watch over you to make sure you initialize the member objects.
  - The most important aspect of inheritance is _not_ that it provides methods for the new class. It’s the relationship expressed between the new class and the base class. This relationship can be summarized by saying, **“The new class is a type of the existing class.”**
  - Casting from a derived type to a base type moves up on the inheritance diagram, so it’s commonly called _upcasting_. _Upcasting_ is always safe because you’re going from a more specific type to a more general type.
  - You can also perform the reverse of upcasting, called _downcasting_
  - Although inheritance gets a lot of emphasis when teaching OOP, it doesn’t mean you should use it everywhere you possibly can. On the contrary, use it sparingly, only when it’s clear that inheritance is useful. If you remember to ask, “Do I need to upcast?” you’ll have a good tool for deciding between composition and inheritance.
  - `final`: Java’s final keyword has slightly different meanings depending on context, but in general it says, “This cannot be changed.”
    - `final` data: Many programming languages have a way to tell the compiler that a piece of data is constant. In Java, you don't. You use `final` modifier to make a variable constant, either at compile time or runtime.
    - By convention, `final static` primitives with constant initial values (that is, compile-time constants) are named with all capitals, with words separated by underscores. (This is just like C constants, which is where that style originated.)
    - Making references final seems less useful than making primitives final.
    - `final` method: The big reason to make a method final is to put a lock on the method to prevent an inheriting class from changing that method’s meaning by overriding it. While initially encouraged for performance benefits as well, you should let the compiler and JVM handle efficiency issues and make a method `final` **only** to explicitly prevent overriding.
    - Any `private` methods in a class are implicitly `final`.
    - `final` class: When you say that an entire class is final (by preceding its definition with the final keyword), you’re preventing all inheritance from this class.
    - All methods in a `final class` are implicitly `final` because there’s no way to override them.
  - _How does the Class Loading work?_
    - When you run `java DerivedClass`, the JVM tries to access `DerivedClass.main()` (a static method), so the loader goes out and finds the compiled code for the `DerivedClass`, in the file `DerivedClass.class`. While loading that, the loader notices that there's a `ParentClass`, which it also loads. This happens whether or not you make an object of `ParentClass` class.
    - If the `ParentClass` class has its own base class (`RootParentClass`), that second base class will also be loaded, and so on.
    - Next, the `static` initialization in the top most parent (in this case, `RootParentClass`) is performed, then the next derived class (`ParentClass`), and so on. This is important because the derived-class `static` initialization might depend on the base-class member being initialized properly.
    - Now, the necessary classes have been loaded, so the object can be created.
    - First, all the primitives in this object are set to their default values and the object references are set to `null` - this happens in one fell swoop by setting the memory in the object to binary zero.
    - Then the base-class constructor(s) is called. Here the call is automatic, but you can also specify the base-class constructor call (as the first operation using `super`).
    - The base-class constructor(s) goes through the same process in the same order as the derived-class constructor. After the base-class constructor completes, the instance variables are initialized in the textual order they were entered.
    - Finally, after all the base-class constructors have been instantiated from the topmost down to the derived class (`RootParentClass` => `ParentClass` => `DerivedClass`), the rest of the body of the `DerivedClass` constructor is executed.
- **Polymorphism**
  - Connecting a method call to a method body is called binding
  - When binding is performed before the program runs (by the compiler and linker, if there is one), it’s called early binding. You might not have heard the term before because it has never been an option with procedural languages. C, for example, has only one kind of method call, and that’s early binding.
  - Late binding means the binding occurs at run time, based on the type of object. It is also called _dynamic binding_ or _runtime binding_.
  - All method binding in Java uses late binding unless the method is `static` or `final` (`private` methods are implicitly `final`). Basically, in Java, late binding happens automatically!
  - Declaring a method `final` effectively "turns off" dynamic binding
  - Put another way, polymorphism is an important technique for the programmer to "separate the things that change from the things that stay the same."
  - Once you learn about polymorphism, you can begin to think everything happens polymorphically. However, only ordinary method calls can be polymorphic
    - For example, if you access a field directly, that access is resolved at compile time
    - Also, if a method is `static`, it does not behave polymorphically! No surprises there. `static` methods are associated with the class, and not the individual objects.
  - Constructors and Polymorphism:
    - Since Constructors are implicitly `static` methods, they are not polymorphic.
    - The base-class constructor is called. This step is repeated recursively such that the root of the hierarchy is constructed first, followed by the next-derived class, etc., until the most-derived class is reached
    - Member initializers are called in the order of declaration
    - The body of the derived-class constructor is called
- **Interfaces**
  - all interface methods are `public` by default
  - any variable in an interface is `public static final` (Constants)
  - Interface with non-abstract methods (with concrete implementations)
    - `static` Methods
    - `default` Methods
    - `private` Method
  - classes can implement (`implements`) multiple interfaces

## Lambdas

- You know an interface in Java. Before diving into Lambdas in Java, it helps to understand what a Functional interface is. Basically, any Java interface with a single abstract method, also sometimes called SAM, is a _Functional Interface_. That said, a functional interface may still have multiple default methods
- Java does not **natively** support Function types. As a matter of fact, everything (almost) is an object in Java
  - In most programming languages that support function literals, you can declare function types such as `(String, String) -> int`, declare variables of those types, put functions into those variables, and invoke them.
- _Lambda expressions_ is conceptually a "block of code" that gets passed around to be executed later, once or multiple times
- In Java, there is **only one thing you can do with a lambda expression**: _put it in a variable whose type is a functional interface, so that it is converted to an instance of that interface._
- Functions (or anonymous block of code) are expressed as _objects, instances of classes that implement a particular interface_

  - _Example 1:_

    ```
    Arrays.sort(words, (first, second) -> first.length() - second.length());
    ```

    Behind the scenes, the second parameter variable of Arrays.sort method (which is expecting `@Nullable java.util.Comparator<? super T> c`) receives a dynamically created (by the JVM) object of some class automagically defined in the background. What's happening in this class? It implements the expected functional interface (in this case, `Comparator<String>`) by using the body of the lambda expression as the body of the SAM (single abstract method) of the functional interface (in this case, `compare` method). So, invoking the `compare` method on this behind-the-scenes dynamically generated object will execute the body of the lambda expression.

  - _Example 2:_

    The lambda expression assigned to an object of `ToIntFunction` type is used to define its `applyAsInt()` which eventually applies the given operation on its only argument.

- Defining Lambda expressions

  - `(String first, String second) -> first.length() - second.length()`
  - If a lambda expression cannot fit in a single line, write it like you would any method:

    ```
    (String first, String second) -> {
            ...
            ...
            return <a-string>
    }
    ```

  - If a lambda expression has no parameters, write it like `() -> {...}`
  - If the paramter types of a lambda expression can be inferred, you can omit them:

    ```
    Comparator<String> comp = (first, second) -> first.length() - second.length();
    ```

  - If a lambda expression a single parameter with inferred type, you can remove the brackets:

    ```
    EventHandler<ActionEvent> listener = event -> System.out.println("Oh no!");
    // Instead of (event) or (ActionEvent event)
    ```

- You never specify the return type of a Lambda expression
- The Java API provides a large number of functional interfaces (see below)
- If there is already a method that does what your lambda expression was going to do, you can use a _Method Reference_ which provides an even shorter version than defining your own Lambda expression. A similar shortcut exists for constructors.
- Method References:
  - `Class::instanceMethod`: The first parameter becomes the receiver of the method, and any other parameters are passed to the method
  - `Class::staticMethod`: All parameters are passed to the static method
  - `object::instanceMethod`: The method is invoked on the given object and the parameters are passed to the instance method. For example, `System.out::println` or `this::equals`
- Constructor References:
  - Constructor references are just like method references, except that the name of the method is new. For example, `Employee::new`
- Bottom line, the point of using Lambdas is _deferred execution_. After all, if you wanted to execute some code right now, you would do that without wrapping it in a Lambda. Use cases like:
  - Running code in a separate thread
  - Running code multiple times
  - Running code at a specific point in an algorithm
  - Running code only when necessary
- In most functional programming languages, function types are _structural_. To specify a function that maps two Strings to an integer, you use a type that looks something like `Function2<String, String, Integer>` or `(string, string) -> int`. In Java, you instead declare the intent of the function using a functional interface.
- There are a number of generic function types that can be used (see below)
- The body of a lambda expression has the same scope as a nested block
- The `this` keyword inside a lambda expression denotes the `this` parameter of the method that **creates** the lambda expression, not the one where it is run!
- Functions that process or return functions are called higher-order functions.

## Generics

## Collections

## Streams

## Annotations

- The @Override annotation prevents you from accidentally overloading.

## Date and Time API

## New I/O

## Optional

## Concurrent Programming

## Java Modules

## Java Libraries

#### Comparing Objects

- `Comparable<T>` interface method
  - `compareTo<T>(T other)`
- `Comparator<T>` interface method: Classes that implement this interface gives you more flexibility to implement a comparison of your choosing. Why? Because the `compare` method is called on the `Comparator` object, not the instance of `T`
  - `compare<T>(T first, T second)`
  - `Comparator.comparing()`
  - `Comparator.thenComparing()`

#### Common Functional Interfaces

- `java.lang.Runnable` (`run()`): Function that runs an action without arguments or return value
- `java.util.function.Supplier<T>` (`T get()`): Function that runs an action without arguments and returns a value of type T
  - `java.util.function.PSupplier<T>` (`p getAsP()`) where P is `Int`, `Long` or `Double` and p is `int`, `long` or `double` respectively
  - `java.util.function.BooleanSupplier<T>` (`boolean getAsBoolean()`)
- `java.util.function.Consumer<T>` (`void accept(T t)`): Function that takes type T as a parameter, runs an action that returns void
  - `java.util.function.PConsumer` (`void accept(p)`): Function that takes a primitive `p` type as a parameter, runs an action that returns void where P is Int, Long or Double and p is int, long or double respectively
  - `java.util.function.ObjPConsumer<T>` (`void accept(T t, p)`): Function that takes type T and a primitive `p` type as parameters, runs an action that returns void where P is Int, Long or Double and p is int, long or double respectively
  - `java.util.function.BiConsumer<T, U>` (`void accept(T t, U u)`): Function that takes type T and U as parameters, runs an action that returns void
- `java.util.function.Function<T, R>` (`R apply(T t)`): Function that takes type T, runs an action that returns R
  - `java.util.function.PFunction<T>` (`T apply(p)`): Function that takes a primitive `p` type as parameter, runs an action that returns type T where P is Int, Long or Double and p is int, long or double respectively
  - `java.util.function.ToPFunction<T>` (`p applyAsP(T t)`): Function that takes type T as a parameter, runs an action that returns a primitive `p` type where P is Int, Long or Double and p is int, long or double respectively
  - `java.util.function.PToQFunction<T>` (`q applyAsQ(p)`): Function that takes primitive type `p` as a parameter, runs an action that returns a primitive type `q` where P, Q is Int, Long or Double and p, q is int, long or double respectively
  - `java.util.function.BiFunction<T, U, R>` (`R apply(T t, U u)`): Function that takes type T and type U as parameters, runs an action that returns R
- `java.util.function.Predicate<T>` (`test(T t)`): Function that takes type T as a parameter, runs an action that returns a boolean
  - `java.util.function.PPredicate` (`test(p)`): Function that takes type a primitive type `p` as a parameter, runs an action that returns a boolean where P is Int, Long or Double and p is int, long or double respectively
  - `java.util.function.BiPredicate<T, U>` (`test(T t, U u)`): Function that takes type T and type U as parameters, runs an action that returns a boolean
- `java.util.function.UnaryOperator<T>` (`T apply(T t)`): Function that takes type T as a parameter, runs an action that returns a type T
  - `java.util.function.PUnaryOperator<T>` (`p applyAsP(p)`): Function that takes a primitive type `p` as a parameter, runs an action that returns the primitive type `p` where P is Int, Long or Double and p is int, long or double respectively
- `java.util.function.BinaryOperator<T>` (`T apply(T t, T t1)`): Function that takes two paramters each of type T, runs an action that returns a type T
  - `java.util.function.PBinaryOperator` (`p applyAsP(p, p)`): Function that takes two parameters of primitive type `p`, runs an action that returns the primitive type `p` where P is Int, Long or Double and p is int, long or double respectively

#### Objects

- `Objects.isNull`

#### Math

- `Math.abs`
- `Math.pow`
- `Math.Random`

#### Collections

- `List.of`
- `Collections.fill`, `Collections.sort`
- `Arrays.copyOf`, `Arrays.stream.boxed.toArray`, `Arrays.sort`, `Arrays.toString`, `Arrays.deepToString`, `Arrays.sort`

#### Date/Time

- `LocalDate.of`

#### Files

- `Path.of`

#### Streams

- `Stream.of`
- `..stream().map`
- `Collectors.toList`

#### Open source Java libraries

- Lombok
  - `@SneakyThrows`
- JavaFaker
