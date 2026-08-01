# Java Data Structures CheatSheet - List

Interface that extends behavior from SequencedCollection, which extends from Collection.

## Useful methods
`List.of(e1, e2, e3...)`   
Initialize an empty immutable list

`new ArrayList<>(List.of(e1, e2, e3...))`   
Initialize a mutable list     

`list.getFirst() / list.getLast()`   
Get first or last element for SequencedCollections (List, OrderedSet, ...)

`list.removeFirst() / list.removeLast()`   
Get first or last element for SequencedCollections (List, OrderedSet, ...)

`list.reversed()`   
returns a reversed view of this list in $O(1)$ (available for all SequencedCollections). The view is the same list with its operations reversed (`removeFirst()` on the view results in a call to `removeLast()` on this list).

`Collections.sort(list)`   
Sort the list in ascending order. This is a stable sort, equal elements will preserve its ordering. Immutable lists (such as created from List.of() cannot be ordered). A comparator can be also passed as a second parameter: `Collections.sort(list, Comparator.reverseOrder())`. 

`list.sort(Comparator.reverseOrder())`   
Sort the list using the mandatory comparator received as parameter. This is a stable sort, equal elements will preserve its ordering. Immutable lists (such as created from List.of() cannot be ordered).
