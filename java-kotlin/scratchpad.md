# Scratchpad to build Muscle Memory

#### Kotlin DSL questions
- How do you read a property from gradle.properties inside the plugins block?


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
