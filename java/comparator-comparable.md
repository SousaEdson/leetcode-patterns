# Java Data Structures CheatSheet - Comparator/Comparable

`Comparable` is an interface that defines a strategy to compare objects through the method `int compareTo(Object other)`. This is called the natural ordering.This is based on `Integer.compare(x, y)`, which returns -1 if x is less than y, 0 if they’re equal, and 1 otherwise. For example, `String` implements `Comparable`, so the following applies:
  - `"first".compareTo("second")` returns a value $<0$
  - `"first".compareTo("first")` returns $0$
  - `"second".compareTo("first")` returns a value $>0$

`Comparator`, on the other hand, is an interface that declares a single method `int compare(Object obj1, Object obj2)`, which is used to compare two arguments of the same type. It works the same way as `Comparable.compareTo()`. Since  `Comparator` interface contains a single method, it is a FunctionalInterface and can be instantiated via a lambda expression.

## Useful methods
`Comparator Comparator.comparingInt(Function keyExtractor)`   
Creates an integer comparator that uses the `keyExtractor` receveid as parameter to extract the integer value that will be used for comparison. For example: `Comparator<Integer> comparator = Comparator.comparingInt(number -> number % 2);` creates an `Integer` comparator that compares the numbers mod 2.

Lambda expressions can also be used to create comparators even more customized, for example:
```
Comparator<Integer> comparator = (Integer a, Integer b) -> {
  if(a % 2 == b % 2) return Integer.compare(a, b);
  return Integer.compare(a % 2, b % 2);
}
``` 
This way both parity and values are being compared.

`comparator = comparator.reversed()`   
Useful for reversing the logic of a comparator. All criterias implmented by the comparator will be reversed.