# Stack and its Applications

## Stack implementation

We implement a Stack as an extension of LinkedList. One can implement Stack from the scratch too.

``` java
// Stack.java

class Stack extends LinkedList {

    void push(int key) {
        insertFirst(key); // Merely calls LinkedList's method to achieve it
    }
    
    int pop() throws RuntimeException {
        if ( isEmpty() ) // i.e. stack is empty
            throw new RuntimeException("Stack is empty");
            
        int top = head.data;
        deleteFirst();
        return top;
    }
    
    int peek() throws RuntimeException {
        if ( isEmpty() ) // i.e. stack is empty
            throw new RuntimeException("Stack is empty");

        return head.data;
    }
    
    boolean isEmpty() {
        if (head == null)
            return true;
        else
            return false;
    }
}
```

``` java
// StackTest.java

class StackTest {
    public static void main(String[] args) {
        Stack s = new Stack();
        s.push(45);
        s.push(30);
        s.push(17);
        s.push(56);
        s.push(84);
        s.push(23);
        System.out.println( s.peek() );  // prints 23
        s.pop();
        System.out.println( s.peek() );  // prints 84
        s.pop();
        System.out.println( s.isEmpty() );  // prints false
        
        s.print();  // What does this print? 
                    // Note: print is defined in LinkedList and hence accessible to Stack
    }
}
```

## Stack Application 1: Reversing the input

Problem: Given a series of integers as input, the problem is to output the integers in reverse order.

Solution idea: As you read the input, push them onto the stack. Now, pop them out one-by-one and print them. Since stack holds LIFO property, popping the elements amounts to reverse.

``` java
import java.util.Scanner;

public class Reverse {
    public static void main(String[] args) {
        // Read the integer series from the terminal
        // As you read push them onto the stack
        Scanner sc = new Scanner(System.in);
        Stack s = new Stack();
        
        while ( sc.hasNext() )  // As long as input exists
            s.push( sc.nextInt() ); // read and push onto the stack
        
        // Now pop the elements and print them
        while ( !s.isEmpty() )  // As long as stack in not empty
            System.out.println( s.pop() );  // pop them out and print them  
    }
}
```

## Execution:
CMD> javac Reverse.java

CMD> java Reverse

25 38 67 93 46 18 75 (CTRL+D)

75 18 46 93 67 38 25

**Note**: CTRL+D is pressed to signify the end of input.
