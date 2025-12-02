# Ex2(C) Deque
## DATE:06-09-2025
## AIM:
To write a **Java program** to implement a **Double-Ended Queue (Deque)** using an array and demonstrate how to count the number of elements currently present in the queue.

## Algorithm:
1.  Start.
2.  Define a class, `ArrayDequeImplementation`, with a fixed size `MAX_SIZE`, an integer array `dequeArray`, and integer variables **front**, **rear**, and **size**.
3.  Define insertion methods, `insertFront()` and `insertRear()`, and deletion methods, `deleteFront()` and `deleteRear()`, ensuring the **size** variable is updated correctly with each operation (incremented on insert, decremented on delete).
4.  Define the **`count()`** method to determine the number of elements:
    a. The method simply **returns the value of the `size` variable**.
    b. *(Alternatively, if size is not tracked explicitly, calculate count as: $$(rear - front + 1) \pmod{MAX\_SIZE}$$ but tracking size is simpler for an array-based Deque).*
5.  In the `main` method, perform various insertion and deletion operations.
6.  Call the `count()` method after the operations to display the number of elements present.
7.  End.


## Program:
/*
Program to implement a Deque and count the number of elements
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/
import java.util.Scanner;

public class ArrayDequeImplementation {
    private static final int MAX_SIZE = 10;
    private int[] dequeArray;
    private int front;
    private int rear;
    private int size; // Explicit size tracker for accurate counting

    public ArrayDequeImplementation() {
        dequeArray = new int[MAX_SIZE];
        front = -1;
        rear = -1;
        size = 0;
    }

    public boolean isEmpty() {
        return size == 0;
    }

    public boolean isFull() {
        return size == MAX_SIZE;
    }

    // Deque operations (Simplified array-based implementation without circular wrapping)
    
    // Insertion at the rear
    public void insertRear(int data) {
        if (isFull()) {
            System.out.println("Deque Overflow: Cannot insert " + data);
            return;
        }
        if (isEmpty()) {
            front = 0;
            rear = 0;
        } else {
            rear++;
        }
        dequeArray[rear] = data;
        size++;
        System.out.println("Inserted at Rear: " + data);
    }
    
    // Insertion at the front (Requires shifting for simplicity in a non-circular array)
    public void insertFront(int data) {
        if (isFull()) {
            System.out.println("Deque Overflow: Cannot insert " + data);
            return;
        }
        if (isEmpty()) {
            front = 0;
            rear = 0;
        } else {
             // Shift all elements one position to the rear
            for (int i = rear; i >= front; i--) {
                dequeArray[i + 1] = dequeArray[i];
            }
            rear++; // Update rear pointer
        }
        dequeArray[front] = data;
        size++;
        System.out.println("Inserted at Front: " + data);
    }

    // Deletion from the front
    public int deleteFront() {
        if (isEmpty()) {
            System.out.println("Deque Underflow");
            return -1;
        }
        int element = dequeArray[front];
        // Shift remaining elements one position to the front
        for (int i = front; i < rear; i++) {
            dequeArray[i] = dequeArray[i + 1];
        }
        dequeArray[rear] = 0; // Clear the last slot
        rear--;
        size--;
        if (isEmpty()) {
            front = -1; 
            rear = -1;
        }
        return element;
    }

    // Deletion from the rear
    public int deleteRear() {
        if (isEmpty()) {
            System.out.println("Deque Underflow");
            return -1;
        }
        int element = dequeArray[rear];
        dequeArray[rear] = 0; // Clear element
        rear--;
        size--;
        if (isEmpty()) {
            front = -1; 
            rear = -1;
        }
        return element;
    }

    // Function to count the number of elements
    public int count() {
        return size;
    }

    public static void main(String[] args) {
        ArrayDequeImplementation deque = new ArrayDequeImplementation();

        System.out.println("--- Deque Operations ---");
        deque.insertRear(10); // [10]
        deque.insertFront(5); // [5, 10]
        deque.insertRear(20); // [5, 10, 20]
        deque.insertFront(1); // [1, 5, 10, 20]
        
        System.out.println("\n--- Counting Elements ---");
        System.out.println("Current number of elements: " + deque.count()); // Output: 4
        
        System.out.println("\n--- Deleting Elements ---");
        System.out.println("Deleted from Front: " + deque.deleteFront()); // [5, 10, 20]
        System.out.println("Deleted from Rear: " + deque.deleteRear());   // [5, 10]
        
        System.out.println("\n--- Final Count ---");
        System.out.println("Current number of elements: " + deque.count()); // Output: 2
    }
}

## Output:
![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to implement a Deque and successfully count the number of elements present in it is implemented successfully.
