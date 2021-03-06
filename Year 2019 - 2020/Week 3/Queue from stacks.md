### Queue from stacks

Implement a queue with two stacks.

In this question we have provided you with skeleton code of the class Queue. You are expected to complete the implementation of this class using only two stacks by completing the following methods:

    isEmpty()
    size()
    enqueue(T i)
    dequeue()
    first()

You can check the comments in the code to see what each method is expected to implement.

Below the skeleton code (after DO NOT MODIFY), you can find the code describing the Stack interface, which has a full implementation in the library code.

Hint: It is a good idea to work out this assignment with pen and paper by drawing the operations for the queue and two stacks.

```java
import java.util.*;

class Queue<T> {
  private Stack<T> s1 = new LibraryStack<>();
  private Stack<T> s2 = new LibraryStack<>();

  /**
   * @return true iff there are no elements left.
   */
  public boolean isEmpty() {
    return s1.isEmpty() && s2.isEmpty();
  }

  /**
   * @return the number of elements in the queue.
   */
  public int size() {
    return s1.size() + s2.size();
  }

  /**
   * Adds an element to the queue.
   *
   * @param i
   *     element to enqueue.
   */
  public void enqueue(T i) {
    s1.push(i);
  }

  /**
   * Removes the first element from the queue.
   *
   * @return the first element from the queue.
   * @throws NoSuchElementException
   *     iff the queue is empty.
   */
  public T dequeue() throws NoSuchElementException {
    if(this.isEmpty()) throw new NoSuchElementException();
    T x;  
    if (s2.isEmpty()) { 
      while (!s1.isEmpty()) { 
        x = s1.pop(); 
        s2.push(x); 
      } 
    } 
    return s2.pop();
  }

  /**
   * Only returns (i.e. does not remove) the first element from the queue.
   *
   * @return the first element from the queue.
   * @throws NoSuchElementException
   *     iff the queue is empty.
   */
  public T first() throws NoSuchElementException {
    if(this.isEmpty()) throw new NoSuchElementException();
    T x;  
    if (s2.isEmpty()) { 
      while (!s1.isEmpty()) { 
        x = s1.pop(); 
        s2.push(x); 
      } 
    } 
    return s2.peek();
  }
}

/**
 * DO NOT MODIFY
 * Interface for a Stack.
 *
 * @param <T>
 *     Type of elements the Stack can hold
 */
interface Stack<T> {
  /**
   * @return true iff it contains no elements.
   */
  public boolean isEmpty();

  /**
   * @return the number of elements in the stack.
   */
  public int size();

  /**
   * Add an element to the top of the stack
   *
   * @param e
   *     element to push.
   */
  public void push(T e);

  /**
   * Removes the top element from the stack.
   *
   * @return the first element.
   * @throws NoSuchElementException
   *     iff the stack is empty
   */
  public T pop() throws NoSuchElementException;

  /**
   * @return the top element (does not pop it).
   * @throws NoSuchElementException
   *     iff the stack is empty
   */
  public T peek() throws NoSuchElementException;
}
```

