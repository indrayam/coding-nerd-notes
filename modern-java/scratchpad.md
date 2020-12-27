# Scratchpad to build Muscle Memory

#### String API
- Types
  - String
  - StringBuilder
    + append
    + appendCodePoint
    + setCharAt, insert, delete
    + toString
- length
- Getting to a subset of a string...
  - substring
  - startsWith
  - endsWith
  - indexOf
  - lastIndexOf
- trim, strip
- isBlank, isEmpty
- toUpperCase, toLowerCase
- join
- repeat
- charAt, codePointAt, codePointCount, codePoints
- equals, equalsIgnoreCase, compareTo, compareToIgnoreCase
- format (static method)
- valueOf (static method)

#### Fundamental Programming Structures
- Types
  + byte (8 bits or 1 byte)
  + short (16 bits or 2 bytes)
  + int (32 bits or 4 bytes)
  + long (64 bits or 8 bytes)
  + double (32 bits or 4 bytes)
  + boolean
  + char (16 bits or 2 bytes)
    - Character.toChars
    - Character.isSupplementaryCodePoint
      - Character.isBmpCodePoint
      - Character.isHighSurrogate
      - Character.isLowSurrogate
    - Character.isJavaIdentifierStart
      - Character.isJavaIdentifierPart
      - Character.isDigit
      - Character.isLetterOrDigit
  + String
  + enum
  + class
  + interface
  + null
- Byte, Short, Integer, Long, Float, Double, Boolean are the classes that represent the primitive types in Java. Use `.valueOf` static method for each of these classes to get an instance from a primitive type
- Formatting
  + `%[argument_index$][flags][width][.precision]conversion`
  + `conversion`
    + int: `%d` (decimal), `%x` (hexadecimal)
    + double: `%m.n%f`, `%m.n%e`, `%m.n%g`
    + char: `%c`
    + String: `%s`
    + boolean: `%b`
    + Newline: `%n`
  + `flags`
    + '-' for left-justified
    + '+' will always include a sign
    + '0' the result will be zero-padded
    + ',' locale specific group separators
    + '(' negative numbers in parenthesis
  + You can use `<` in place of argument index. It causes the argument for the previous format specifier to be re-used
- Access Modifiers:
  + private
    - same class: **Y**
    - sub-class in same package: **N**
    - unrelated peer class in same package: **N**
    - sub-class in a peer package: **N**
    - unrelated peer class in a peer package: **N**
  + default (or package private)
    - same class: **Y**
    - sub-class in same package: **Y**
    - unrelated peer class in same package: **Y**
    - sub-class in a peer package: **N**
    - unrelated peer class in a peer package: **N**
  + protected
    - same class: **Y**
    - sub-class in same package: **Y**
    - unrelated peer class in same package: **Y**
    - sub-class in a peer package: **Y**
    - unrelated peer class in a peer package: **N**
  + public
    - same class: **Y**
    - sub-class in same package: **Y**
    - unrelated peer class in same package: **Y**
    - sub-class in a peer package: **Y**
    - unrelated peer class in a peer package: **Y**
- A single Java file can have one public class with the same name as the file name. However, you can have as many types (class or interface) as you want, as long as they have 'default' access modifier.
- A `.java` file is called a compilation unit. Each compilation unit may contain any number of top-level classes and interfaces. If there are no public top-level types then the compilation unit can be named anything. However, there can be only one public class/interface in a compilation unit and the compilation unit (the `.java` file) must be named exactly as this public top-level type.
- Common Java Operators:
  + `+`, `-`, `*`, `/`, `%`, `++`, `--`
  + `>`, `>=`, `<`, `<=`, `!`
  + `==`, `!=`
- Bitwise Operators
  - `&` (and): The binary AND operation has two inputs and one output. Always produce a 1 output if both of its inputs are 1 and will produce a 0 output if one or both of its inputs are 0.
    + 0, 0 => 0
    + 1, 0 => 0
    + 0, 1 => 0
    + 1, 1 => 1
  - `|` (or): The binary OR operation has two inputs and one output. Always produce a 1 output if either of its inputs are 1 and will produce a 0 output if both of its inputs are 0.
    + 0, 0 => 0
    + 1, 0 => 0
    + 0, 1 => 0
    + 1, 1 => 1
  - `^` (xor): The binary XOR (exclusive OR) operation has two inputs and one output. Always produce a 1 output if either of its inputs are 1 and will produce a 0 output if both of its inputs are 0 or 1.
    + 0, 0 => 0
    + 1, 0 => 0
    + 0, 1 => 0
    + 1, 1 => 1
  - `~` (not): The binary NOT operation has one input and one output. Always produce a 1 output if its input is 0 and will produce a 0 output if its input is 1.
    + 0 => 1
    + 1 => 0
  - To convert a positive number into a negative number using the **Two’s complement** representation, invert all of the bits of the number and ​add 11. Let's play with 23:

```
23    = 00000000 00000000 00000000 00010111
Inv   = 11111111 11111111 11111111 11101000
+ 1   = 00000000 00000000 00000000 00000001
Res   = 11111111 11111111 11111111 11101001
```

#### Floating Point Arithmetic Notes (IEEE 754)
- Significand == Mantissa == Coefficient

#### Unicode and Java (ISO 10646)

Bottom line, is this:
- UTF-8 saves space. It can use anywhere from 1 byte to 4 bytes
- **Code points** are numbers that represent Unicode characters. One or more code units encode a single code point.
- **Code units** are numbers that encode code points, to store or transmit Unicode text. As stated above, one or more code units encode a single code point. Each code unit has the same size, which depends on the encoding format that is used. The most popular format, UTF-8, has 8-bit code units.
- The first version of Unicode had 16-bit code points. Translation: Each UTF encoded character used two Code Units. Since then, the number of characters has grown considerably and the size of code points was extended to 21 bits. These 21 bits are partitioned in 17 planes, with 16 bits each:
  + Plane 0: **Basic Multilingual Plane (BMP)**, 0x0000–0xFFFF
Contains characters for almost all modern languages (Latin characters, Asian characters, etc.) and many symbols.
  + Plane 1: Supplementary Multilingual Plane (SMP), 0x10000–0x1FFFF
Supports historic writing systems (e.g., Egyptian hieroglyphs and cuneiform) and additional modern writing systems.
Supports emojis and many other symbols.
  + Plane 2: Supplementary Ideographic Plane (SIP), 0x20000–0x2FFFF
Contains additional CJK (Chinese, Japanese, Korean) ideographs.
  + Plane 3–13: Unassigned
  + Plane 14: Supplementary Special-Purpose Plane (SSP), 0xE0000–0xEFFFF
    - Contains non-graphical characters such as tag characters and glyph variation selectors.
  + Plane 15–16: Supplementary Private Use Area (S PUA A/B), 0x0F0000–0x10FFFF
    - Available for character assignment by parties outside the ISO and the Unicode Consortium. Not standardized.
Planes 1-16 are called supplementary planes or **astral planes.**
- Characters whose code points are greater than U+FFFF are called *Supplementary characters*. Those code points are called *Supplementary Code Points*
- The Java platform uses the UTF-16 representation in char arrays and in the String and StringBuffer classes. In this representation, supplementary characters are represented as a pair of char values, the first from the **high-surrogates** range, (\uD800-\uDBFF), the second from the **low-surrogates** range (\uDC00-\uDFFF). *Note: I have not been able to understand these high and low surrogate ranges...yet.*
A char value, therefore, represents Basic Multilingual Plane (BMP) code points, including the surrogate code points, or code units of the UTF-16 encoding.
- An int value represents all Unicode code points, including supplementary code points. The lower (least significant) 21 bits of int are used to represent Unicode code points and the upper (most significant) 11 bits must be zero. 

**Formal Documentation from JavaDoc documentation of Character class in JDK 11**
The Character class wraps a value of the primitive type `char` in an object. An object of class Character contains a single field whose type is char.
In addition, this class provides a large number of static methods for determining a character's category (lowercase letter, digit, etc.) and for converting characters from uppercase to lowercase and vice versa.

**Unicode Conformance**
The fields and methods of class Character are defined in terms of character information from the Unicode Standard, specifically the UnicodeData file that is part of the Unicode Character Database. This file specifies properties including name and category for every assigned Unicode code point or character range. The file is available from the Unicode Consortium at http://www.unicode.org .
The Java SE 11 Platform uses character information from version 10.0 of the Unicode Standard, with an extension. The Java SE 11 Platform allows an implementation of class Character to use the Japanese Era code point, U+32FF, from the first version of the Unicode Standard after 10.0 that assigns the code point. Consequently, the behavior of fields and methods of class Character may vary across implementations of the Java SE 11 Platform when processing the aforementioned code point ( outside of version 10.0 ), except for the following methods that define Java identifiers: isJavaIdentifierStart(int), isJavaIdentifierStart(char), isJavaIdentifierPart(int), and isJavaIdentifierPart(char). Code points in Java identifiers must be drawn from version 10.0 of the Unicode Standard.

**Unicode Character Representations**
The `char` data type (and therefore the value that a Character object encapsulates) are based on the original Unicode specification, which defined characters as fixed-width 16-bit entities. The Unicode Standard has since been changed to allow for characters whose representation requires more than 16 bits. The range of legal code points is now U+0000 to U+10FFFF, known as Unicode scalar value. (Refer to the definition of the U+n notation in the Unicode Standard.)
The set of characters from U+0000 to U+FFFF is sometimes referred to as the **Basic Multilingual Plane (BMP)**. Characters whose code points are greater than U+FFFF are called *supplementary characters*. The Java platform uses the UTF-16 representation in char arrays and in the String and StringBuffer classes. In this representation, supplementary characters are represented as a pair of char values, the first from the high-surrogates range, (\uD800-\uDBFF), the second from the low-surrogates range (\uDC00-\uDFFF).
A char value, therefore, represents Basic Multilingual Plane (BMP) code points, including the surrogate code points, or code units of the UTF-16 encoding. An int value represents all Unicode code points, including supplementary code points. The lower (least significant) 21 bits of int are used to represent Unicode code points and the upper (most significant) 11 bits must be zero. Unless otherwise specified, the behavior with respect to supplementary characters and surrogate char values is as follows:
The methods that only accept a char value cannot support supplementary characters. They treat char values from the surrogate ranges as undefined characters. For example, Character.isLetter('\uD840') returns false, even though this specific value if followed by any low-surrogate value in a string would represent a letter.
The methods that accept an int value support all Unicode characters, including supplementary characters. For example, Character.isLetter(0x2F81A) returns true because the code point value represents a letter (a CJK ideograph).
In the Java SE API documentation, Unicode code point is used for character values in the range between U+0000 and U+10FFFF, and Unicode code unit is used for 16-bit char values that are code units of the UTF-16 encoding. For more information on Unicode terminology, refer to the Unicode Glossary

#### Kotlin DSL questions
- How do you read a property from gradle.properties inside the plugins block? *Nope*

#### Lombok
- @Getter
- @Setter
- @ToString, @ToString(onlyExplicitlyIncluded = true), @ToString.Exclude, @ToString.Include, 
- @EqualsAndHashCode, @EqualsAndHashCode(onlyExplicitlyIncluded = true), @EqualsAndHashCode.Exclude, @EqualsAndHashCode.Include, 
- @NoArgsContructor
- @AllArgsConstructor
- @RequiredArgsConstructor
- @Sl4j
- @Data
  + Shortform for @ToString, @EqualsAndHashCode, @Getter on all fields, @Setter on all non-final fields and @RequiredArgsConstructor
- @Value
- @Builder

#### Java Proxies
1. Implement Decorator with Spring
2. InterfaceProxy.proxy (no Spring)
3. ClassProxy.proxy (no Spring)
4. Spring Cache support
5. Spring Aspect, @Facade and @Logged


#### Spring Boot Annotations
- @SpringBootApplication
- @Controller
- @RestController
- @Service
- @Repository
- @Bean
- @Component
- @Configuration
- @ConfigurationProperties
- @ConfigurationPropertiesScan

#### application.properties
- `logging.level.sql=DEBUG`
- Use classes under `org.springframework.boot.autoconfigure.condition` to setup AutoConfiguration conditionals

#### JUnit
- Format: `(expected, actual, string)` OR `(expected, actual, Supplier String)`
- Annotations
  - Test Annotations: @Test, @ParameterizedTest, @RepeatedTest, @Disabled (Method or Class Level), @DisplayName()
  - Lifecycle Annotations: @BeforeEach, @AfterEach, @BeforeAll (must be static), @AfterAll (must be static)
  - Conditional Execution Annotations: 
    + @EnabledOnOs, @DisabledOnOs
      - AIX, MAC, LINUX, WINDOWS, OTHER
    + @EnabledOnJre, @EnabledOnJreRange, @DisabledOnJre
      - JAVA_8, JAVA_9, JAVA_10, JAVA_11, JAVA_12, JAVA_13, JAVA_14, OTHER
    + @EnabledIfEnvironmentVariable, @DisabledIfEnvironmentVariable
    + @EnabledIfSystemProperty, @DisabledIfSystemProperty
  - Tagging/Filtering: @Tag
  - Test Instance Lifecycle: 
    + TestInstance.Lifecycle.PER_CLASS
    + TestInstance.Lifecycle.PER_METHOD
- Assertions
  - assertAll()
  - assertTrue()
  - assertFalse()
  - assertEquals()
  - assertNotEquals()
  - assertNull()
  - assertNotNull()
  - assertSame()
  - assertNotSame()
  - assertThrows()
  - assertTimeout()
  - assertTimeoutPreemptively()
  - fail()
  - *assertArrayEquals()*
  - *assertIterableEquals()*
  - *assertLinesMatch()*
- Assumptions
  - assumeTrue()
  - assumeFalse()
  - assumingThat()

#### Hamcrest Matchers
- assertThat()

#### Running Kotlin

```bash
alias kj=kotlinc-jvm
alias kt=kotlin
alias kc=kotlinc

# Kotlin Programs

## Compile using kj. Run using kt or java
code -n sample.kt
kj sample.kt
kt SampleKt
# OR
java -classpath . SampleKt

## Compile using kc. Run using kt or java
kc sample.kt -include-runtime -d sample.jar
kt sample.jar
# OR
java -jar sample.jar

# Kotlin Scripts
code -n sample.kts
kt sample.kts
```


#### Notes on Kotlin Collections
**Array:** Holds values in a sequence. Can be updated. Can't be resized.
**List:** Holds values in a sequence. Can't be updated. Can't be resized.
**Set:** Holds values in no particular order. Can't be updated. Can't be resized.
**Map:** Holds key/value pairs. Can't be updated. Can't be resized.
**MutableList:** Holds values in a sequence. Can be updated. Can be resized.
**MutableSet:** Holds values in no particular order. Can be updated. Can be resized.
**MutableMap:** Holds key/value pairs. Can be updated. Can be resized.


#### Kotlin Arrays
- Types: Array<>
- Create: arrayOf(with entries), arrayOfNulls(with size of the array)
- Copy and Add: .plus(with the additional entry)
  + Transform: toList(), toMutableList(), toSet(), toMutableSet()
- Size: .size
- Read: array[]
- Add: Not allowed. Cannot change size after creation
- Edit/Change: array[] = ...
- Delete: Not allowed. Cannot change size after creation
- Find/Search: contains(), indexOf(), .minOrNull(), .maxOrNull()
- Moving things around: sort()/sorted(), reverse()/reversed(), shuffle()/shuffled()
- Math: .sum(), .average()
- Iterate: .map {}

#### Kotlin List
- Types: List<>, MutableList<>
- Create: listOf(), mutableListOf()
- Copy/Transform: toList(), toMutableList(), toSet(), toMutableSet(), toTypedArray()
- Size: .size
- Read: .get()
- Add: .add(), add(N, val), .addAll()
- Edit/Change (only for Mutable version): .set()
- Delete: .remove(), .removeAt(), .removeAll(), .retainAll(), .clear()
- Find/Search: contains(), indexOf(), .minOrNull(), .maxOrNull()
- Moving things around: sorted(), reversed(), shuffled()
- Math: .sum(), .average()
- Iterate: .map {}

#### Kotlin Set
- Types: Set<>, MutableSet<>, SortedSet<>
- Create: setOf(), mutableSetOf()
- Copy/Transform: toList(), toMutableList(), toSet(), toMutableSet(), toTypedArray()
- Size: .size
- Read: .get()
- Add: .add(), add(N, val), .addAll()
- Edit/Change (only for Mutable version): .set()
- Delete: .remove(), .removeAt(), .removeAll(), .retainAll(), .clear()
- Find/Search: contains(), indexOf(), .minOrNull(), .maxOrNull()
- Moving things around: sorted(), reversed(), shuffled()
- Math: .sum(), .average()
- Iterate: .map {}

#### Kotlin Map
- Types: Map<>, MutableMap<>, SortedMap<>
- Create: mapOf(foo1 to bar1, foo2 to bar2)
- Copy/Transform: toMap(), toMutableMap(), toSortedMap()
- Size: .size
- Read: .get(), .getValue(), .getOrDefault()
- Add: .put(), .putAll(), .putIfAbsent()
- Edit/Change: .replace(), .replaceAll()
- Delete: .remove(), .clear()
- Find/Search: containsKey(), containsValue()
- Moving things around:
- Math:
- Iterate: .map {} .keys(), .values(), .entries()
