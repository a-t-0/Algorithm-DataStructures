### Remove last occurrence in ArrayList

Write a Java method removeLastOccurrence(int x, ArrayList<Integer> list), which removes the last occurrence of an integer x from the arrayList arrList.

Write another Java method removeAll, which should use removeLastOccurrence to remove the entries, until the array list holds no more entries.

The code on the right shows you a code framework in which the implementation of two static methods is still missing. Provide this implementation and check that it is correct by either writing more tests yourself or using the provided tests and specification tests.

```java
import java.util.*;

class Solution {
  /**
   * Removes all elements from the ArrayList, using the removeLastOccurrence method.
   *
   * @param list
   *     to remove the elements from.
   */
  public static void removeAll(ArrayList<Integer> list) {
    for(int i = list.size() - 1; i > -1; i--)
      removeLastOccurrence(list.get(i), list);
  }
  

  /**
   * Takes an ArrayList and removes last occurrence of x,
   * shifting the rest of the elements left.
   * I.e. [5, 1, 5, 9, 8], with x = 5
   * would result in: [5, 1, 9, 8].
   * Note that this method does not return a new list.
   * Instead, the list that is passed as a parameter is changed.
   *
   * @param list
   *     to remove an element from.
   * @param x
   *     element value to look for
   */
  public static void removeLastOccurrence(int x, ArrayList<Integer> list) {
    for(int i =list.size() -1; i >=0; i--)
      if(list.get(i) == x) {
        list.remove(i);
        break;
      }
  }
}
```
