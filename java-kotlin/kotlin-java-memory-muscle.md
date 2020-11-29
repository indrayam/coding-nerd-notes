# Kotlin/Java Memory Muscle

## Running Kotlin

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


## Notes on Collections
**Array:** Holds values in a sequence. Can be updated. Can't be resized.
**List:** Holds values in a sequence. Can't be updated. Can't be resized.
**Set:** Holds values in no particular order. Can't be updated. Can't be resized.
**Map:** Holds key/value pairs. Can't be updated. Can't be resized.
**MutableList:** Holds values in a sequence. Can be updated. Can be resized.
**MutableSet:** Holds values in no particular order. Can be updated. Can be resized.
**MutableMap:** Holds key/value pairs. Can be updated. Can be resized.


## Arrays
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


## Collections

### List
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

### Set
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

### Map
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
