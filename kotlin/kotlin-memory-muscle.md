# Kotlin Memory Muscle

## Arrays
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


## Collections

### List
- Create: listOf(), mutableListOf()
- Copy/Transform: toList(), toMutableList(), toSet(), toMutableSet()
- Size: .size
- Read: .get()
- Add: .add(), add(N, val)
- Edit/Change (only for Mutable version): .set()
- Delete: .removeAt()
- Find/Search: contains(), indexOf(), .minOrNull(), .maxOrNull()
- Moving things around: sort()/sorted(), reverse()/reversed(), shuffle()/shuffled()
- Math: .sum(), .average()

### Set
- Create: setOf(), mutableSetOf()
- Copy/Transform: toList(), toMutableList(), toSet(), toMutableSet()
- Size: .size
- Read: .get()
- Add: .add()
- Edit/Change (only for Mutable version): .set()
- Delete: .remove(), .removeAt()
- Find/Search: contains(), indexOf(), .minOrNull(), .maxOrNull()
- Moving things around: sort()/sorted(), reverse()/reversed(), shuffle()/shuffled()
- Math: .sum(), .average()

