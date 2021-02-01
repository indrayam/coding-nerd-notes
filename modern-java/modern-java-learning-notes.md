# Modern Java Learning Notes

## Basics

- Primitive Types:
  - `int` (`byte`, `short`, `long`)
  - `double` (`float`)
  - `char`
  - `boolean`
- `String`
- Literals
- Variables
- Arrays
  - `int[] x = new int[N]`
  - `double[] y = {1.1, 2.3, 4.5}`
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

## Object-Oriented Programming

- Defining a Class and creating objects from it
  - `<access-specifier> class Name`
  - `new ClassName(args list...)` to instantiate a class
  - `this`
    - When used, it is in the sense of "the current object". As a result, it can only be used in non-static methods
  - Constructors:
    - If you create a class that has no constructors, the compiler will automatically create a no-arg constructor for you
    - However, if you define any constructors (with or without arguments), the compiler will **NOT** synthesize one for you
    - Constructor looks like a Java method, except it does **NOT** have a return type
    - Also, the convention of having Java method names starting with a lowercase first letter does not apply in the case of Constructors
    - Inside a constructor, the `this` keyword takes on a different meaning when you give it an argument list. It makes an explicit call to the constructor that matches that argument list
      - `this(args list)` call must be the first thing you do inside the constructor
      - Cannot use `this(args list...)` more than once inside a constructor!
      - Cannot use `this(args list...)` inside a non-constructor Java method
  - Static Members (Fields and Methods)
    - Class level, as opposed to instance/object level member
    - Don't need an object reference to call "static" methods
    - You can call static methods from instance/object of that class (or another class, provided you have access), but cannot call non-static methods or fields from static methods
  - Instance Variables
  - Instance Methods
- Method Overloading
  - Each overloaded method MUST have the same name (duh) and must take a unique list of argument types
  - Return types does not matter in deciding whether a method is overloaded or not
- `final`
  - `final` class
  - `final` method
  - `final` variable
- Access Modifiers:
  - `public`
  - `private`
  - `protected`
  - `default` (or package-private)
- Classes can extend (`extends`) a single parent class at a time
- `super`
- An `abstract` class is a class which includes one or more method which is of type _abstract_. The method has no concrete implementation
- Interfaces
  - all interface methods are `public` by default
  - any variable in an interface is `public static final` (Constants)
  - Interface with non-abstract methods (with concrete implementations)
    - `static` Methods
    - `default` Methods
    - `private` Method
- classes can implement (`implements`) multiple interfaces
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
- Garbage Collection/Cleanup
  - Garbage collection is only about memory.That is, the sole reason for the existence of the garbage collector is to recover memory your program is no longer using.
  - Java's GC only knows how to release memory allocated with `new`
  - The need for `finalize()` is limited to special cases where your object can allocate storage in some way other than creating an object. But, you might observe, everything in Java is an object, so how can this be?
  - It would seem that `finalize()` is in place because you might do something C-like by allocating memory using a mechanism other than the normal one in Java. This can happen primarily through native methods, which are a way to call non-Java code from Java.
  - Bottom line, you won’t use `finalize()` much since you won't, in all likelihood, be interacting with non-Java code inside your Java code.

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
