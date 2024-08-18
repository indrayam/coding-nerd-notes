# Rust in a Month of Lunches

### Ownership, Borrowing

- Borrow Checker capability of the Rust compiler. _Ownership_ and _Borrowing_ concepts are critical to understanding memory management in Rust.

#### Rust Compiler (or Borrow Checker's) Rules for "Ownership" during Compile Time

- **Rule 1:** Each value (for example, heap-allocated string or vector) in Rust has an "owner"
- **Rule 2:** Each value (for example, heap-allocated string or vector) can have "only one owner" at a time
  - Variables are **Copy** type or **Move** type. For example, primitive types with fixed size like `i8`, `i16`, `u8`, `u16`, `char`, etc. are all **Copy** type and any assignment involving variables of these types are copied. However, types like `String` are **Move** type and any assignment will lead to the disappearing of the original variable.
- **Rule 3:** When the "owner" of the value goes out of scope, the value (for example, heap-allocated string or vector) will be "dropped".

#### Rust Compiler (or Borrow Checker's) Rules for "Borrowing" during Compile Time

In Rust, creating a "reference" to a value is called "borrowing". And just like "ownership" comes with its own rules, borrowing values has rules too that are checked by the Borrow Checker at compile time to make sure our code is memory safe.

- **Rule 1:** At any given time, you can have _one_ mutable reference or _any_ number of immutable references
- **Rule 2:** A Reference in Rust must always be "valid", as in a reference (or borrow) should never get into a situation where the reference outlives the actual value that was borrowed. Bottom line, the lifetime of a reference should not outlive the lifetime of the owned value

#### Lifetime and interior mutability

- Annotating lifetimes is not a concept most other programming languages have.
- Lifetime refers to the span of the program during which a specific data (or value) is valid. There are two types of lifetimes: Concrete Lifetime vs Generic Lifetime.
  - A concrete lifetime is a span of code where a value is valid. However, when we define functions or structures that operate on references, we don't know the exact lifetime of those references at compile time.
  - Generic lifetime is a variety of generics that give the compiler (really, the borrowchecker) information about how reference lifetimes relate to each other. We use Generic Lifetime annotations to help the compiler understand the relationship between lifetimes when we are dealing with values (specifically references to values) inside functions or structs and the lifetime is not obvious to figure out at compile time for the compiler.
- Borrow Checker evaluates the lifetimes of values to make sure that the ownership and borrowing rules are being followed
- Bottom line, the lifetime of a reference does not outlive the lifetime of the owned value
- Lifetime annotations don’t change how long any of the references live. Rather, they describe the relationships of the lifetimes of multiple references to each other without affecting the lifetimes.
- Every reference has a lifetime and that you need to specify lifetime parameters for functions or structs that use references
- Lifetimes on function or method parameters are called input lifetimes, and lifetimes on return values are called output lifetimes.
- **Lifetime Elision Rules**: The patterns programmed into Rust’s analysis of references are called the lifetime elision rules. These aren’t rules for programmers to follow; they’re a set of particular cases that the compiler will consider, and if your code fits these cases, you don’t need to write the lifetimes explicitly.
- The compiler uses three rules to figure out the lifetimes of the references when there aren’t explicit annotations.
  - The first rule is that the compiler assigns a lifetime parameter to each parameter that’s a reference. In other words, a function with one parameter gets one lifetime parameter: `fn foo<'a>(x: &'a i32);` a function with two parameters gets two separate lifetime parameters: `fn foo<'a, 'b>(x: &'a i32, y: &'b i32);` and so on.
  - The second rule is that, if there is exactly one input lifetime parameter, that lifetime is assigned to all output lifetime parameters: `fn foo<'a>(x: &'a i32) -> &'a i32`.
  - The third rule is that, if there are multiple input lifetime parameters, but one of them is `&self` or `&mut self` because this is a method, the lifetime of `self` is assigned to all output lifetime parameters. This third rule makes methods much nicer to read and write because fewer symbols are necessary.

```rust
&'a i32     // a reference with an explicit lifetime
&'a mut i32 // a mutable reference with an explicit lifetime
```

### Variable definition

```rust
  let
  const
  static
```

### Primitive Types

```rust
  /*integer:*/ i8, i16, i32, i64, i128, isize, u8, u16, u32, u64, u128, usize
  /*float:*/ f32, f64
  /*bool:*/ true, false
  /*char:*/ ''
  /*unit type:*/ () //a function that returns nothing actually returns an empty tuple, also called "unit type"
```

### Operators

```rust
  // Addition:
  +

  // Subtraction:
  -

  // Multiplication:
  *

  // Division:
  /

  // Modulo (Remainder):
  %

```

### Basic Collections

```rust
  /*Array:*/
  let my_arr : [i32; 4] = [23, 4, 3, 12];

  /*Vec:*/
  let my_vec: Vec<(i32, i32)> = vec![(0, 0), (0, 1), (1, 0), (1, 1)];
  let my_vec = vec![0, 3, 2, 10];
  let my_vec: Vec<[i32; 4]> = vec![[0i32; 4]];

  /*Tuple:*/
  let my_tuple: (i32, char, &str) = (10, 'a', "Anand");

  /*Slice:*/
  let arr_slice = &my_arr[1..]; // array slice starting at 2nd element
  let vec_slice = &my_vec[..]; // vector slice with all elements
  let tuple_slice = &my_tuple[..2]; // vector slice with first and second element
```

### Conditional

Note that you do not need parentheses with `if` in Rust. Using `if` will work with parentheses but the compiler will tell you that you did not need to use them.

```rust
  /* if/else if/else */
  if cond {
    // execute this block if cond is true
  } else if cond1 {
    // execute this block if cond1 is true
  } else {
    // execute this block if neither cond or cond1 is true
  }

  /* for */
  for x in collection {
    // execute this block for every element within the collection
  }

  /* range */
  1..10 // from 1 to 10, excluding 10
  1..=10 // from 1 to 10, including 10

  /* match */
  match (a_num, b_char) {
    a => {},
    b => {},
    _ => {},
  }

  /* while */
  while cond {
    // execute this block if cond is true
  }


  /* loop */
  loop {
    // execute this block until...
    //  - `break` call is reached. Note: You can return a local variable at the time of calling of break
    // writing the value right after break followed by ;
    break counter;

    //  - the program is explicitly terminated using Ctrl+C
  }
```

### Custom Types

```rust
  enum
  struct
```

#### Enums

```rust
  enum Days {
    Monday,
    Tuesday,
    Wednesday,
    Thursday,
    Friday,
    Saturday,
    Sunday,
  }

  enum Clock {
    Sundial(u8),
    Digital(u8, u8),
    Analog(u8, u8, u8)
  }

  let x = Days::Sunday
```

#### Struct

```rust
  struct CricketPlayer {
    name: String,
    age: u8,
    score: u32,
    }
```

### Methods

```rust
    impl CricketPlayer {
    fn scores(&self, run; u8) {

         }

    }
```

### Associated Functions

```rust
    impl CricketPlayer {
    fn new(name: String, age: u8) -> CricketPlayer {
      CricketPlayer {
        name: name,
        age: age,
        score: 0
      }
     }
    }
    let cp = CricketPlayer::new("Virat Kohli", 30);
```

- Methods that read data vs methods that write data

```rust
    // Immutable reference
    fn scores(&self, run: u8) {}

    // Mutable reference
    fn scores(&mut self, run: u8)
```

#### Tuple Struct

```rust
    struct Triangle(u8, u8, u8);
    struct Meters(u8);
```

#### Unit Struct

```rust
    struct MyStruct;
```

- Derefencing a reference is only necessary if you want to get to the "literal value"

### Advanced Collections

- HashMap
- BTreeMap
- HashSet
- BTreeSet
- BinaryHeap (Priority Queue)
- VecDeque

### Generics

- Generic Structs

```rust
struct Point<T> {
  x: T,
  y: T,
}
```

- Generic Enums

```rust
enum Option<T> {
  Ok(T),
  None,
}
```

- Generic Methods

```rust
struct Point<T> {
    x: T,
    y: T,
}

impl<T> Point<T> {
    fn x(&self) -> &T {
        &self.x
    }
}
```

- Generic Functions

```rust
fn largest<T: std::cmp::PartialOrd>(list: &[T]) -> &T {
  // function body...
}
```

- Generic Traits

```rust
trait HasHealth<T>
where
  T: GameCharacter + Debug
{
  fn get_health<U>(&self) -> &U {
    self.health
  }
}
```

- Generic Lifetime
- Option (Some, None)
- Result (Ok, Err)

### Traits

- Think Behavior or Qualification (not Interface)
- Traits as Bounds. Basically, Marker Traits
- Inheritance and Polymorphism using Traits
  - A **trait object** is an opaque value of another type that implements a set of traits. Trait objects are written as the keyword dyn followed by a set of trait bounds. More [here](https://doc.rust-lang.org/reference/types/trait-object.html)
  - In Rust, the `dyn` keyword is used with traits to implement dynamic polymorphism at runtime. Dynamic polymorphism uses **trait objects** to indicate to runtime which type is required to satisfy a polymorphic interface. It can implemented in two ways:

```rust
// Create trait objects by boxing the trait implementation
Box<dyn Trait>
```

or

```rust
// Use references. Trait Name for the example below is 'TraitName'
fn function_name(o: &dyn TraitName)
// OR
fn function_name(o: &mut dyn Trait)
```

- Existing Traits of Interest
  - From
  - Display
  - Debug
  - Drop
  - Clone
  - Copy
- The "Orphan Rule"
  - You can implement your trait on someone else's type
  - You can implement someone else's trait on your type
  - You cannot implement someone else's trait on someone else's type

### Closures, Iterators

```rust
// Simplest example
let add_one = |x| x + 1;
println!("{}", add_one(10));

// Closures and Iterators are match made in heaven
(1..5).for_each(|x| print!("{}", x));
println!();
```

### Async/Concurrent Programming

Not started yet.

### Smart Pointers

Not started yet.
