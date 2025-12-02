# Ex2(B) Priority Queue
## DATE:06-09-2025
## AIM:
To write a **Java program** to implement a **Priority Queue** and display its elements after performing insertion (enqueue) and deletion (dequeue) operations, where the highest priority item is removed first.

## Algorithm:
1.  Start.
2.  Define a class, `PriorityQueueImplementation`, to manage the queue operations, including the queue array and size.
3.  Define the **`insert(int data)`** method (Enqueue):
    a. Check for overflow.
    b. Insert the new element at the **rear** of the array.
    c. **Sort** the array (or use insertion sort logic) to place the highest priority element at the front (index 0).
4.  Define the **`delete()`** method (Dequeue):
    a. Check for underflow.
    b. Since the highest priority element is always at the front (index 0) due to sorting, return and remove the element at index 0.
    c. Shift all remaining elements one position up to fill the gap.
5.  Define the **`display()`** method:
    a. Loop through the array from index 0 up to `size-1`.
    b. Print each element in the array to show the current state of the priority queue.
6.  In the `main` method, demonstrate insertion and deletion operations, followed by calling the `display()` method to show the state of the queue.
7.  End.

## Program:
/*
Program to display the elements of the priority queue after insertion and deletion operation
Developed by:Dharani dharan K
RegisterNumber: 212223040036
*/
import java.util.Arrays;

public class PriorityQueueImplementation {
    private static final int MAX_SIZE = 5;
    private int[] queueArray;
    private int size;

    public PriorityQueueImplementation() {
        queueArray = new int[MAX_SIZE];
        size = 0;
    }

    // Insertion operation (maintains priority by sorting or re-ordering)
    public void insert(int data) {
        if (size == MAX_SIZE) {
            System.out.println("Queue Overflow: Cannot insert " + data);
            return;
        }
        
        // Insert element at the end
        queueArray[size] = data;
        size++;

        // Maintain Priority: Simple method (sorting the active part of the array).
        // Assuming higher number means higher priority.
        // This ensures the highest priority item is always at queueArray[0]
        Arrays.sort(queueArray, 0, size);
        
        // Optional: Reverse the sorted array if ascending order is used for priority
        // For simplicity, we assume sorting places the highest priority item at one end.
        // A standard PriorityQueue is typically implemented with a Heap for O(log n) complexity.
        
        System.out.println("Inserted: " + data);
    }

    // Deletion operation (removes the highest priority element, which is at the end after Arrays.sort)
    public int delete() {
        if (size == 0) {
            System.out.println("Queue Underflow");
            return -1;
        }

        // Get the element at the high priority end (index size-1 after Arrays.sort)
        int element = queueArray[size - 1]; 
        size--;

        return element;
    }

    // Function to display the elements
    public void display() {
        if (size == 0) {
            System.out.println("Priority Queue is Empty.");
            return;
        }
        System.out.print("Priority Queue (Highest Priority on the right): ");
        // Print array from the lowest priority to the highest priority
        for (int i = 0; i < size; i++) {
            System.out.print(queueArray[i] + " ");
        }
        System.out.println();
    }

    public static void main(String[] args) {
        PriorityQueueImplementation pq = new PriorityQueueImplementation();

        // 1. Insertion Operations
        System.out.println("--- Insertion ---");
        pq.insert(10); // Priority 10
        pq.insert(50); // Priority 50 (Highest)
        pq.insert(20); // Priority 20
        pq.insert(40); // Priority 40
        pq.display();
        
        // 2. Deletion Operation (removes 50 - highest priority)
        System.out.println("\n--- Deletion ---");
        int deletedElement = pq.delete();
        if (deletedElement != -1) {
            System.out.println("Deleted (Highest Priority): " + deletedElement);
        }
        
        // 3. Display after deletion
        pq.display();

        // 4. Further Insertion
        System.out.println("\n--- Further Insertion ---");
        pq.insert(30); // Priority 30
        pq.display();

        // 5. Final Deletion (removes 40 - new highest priority)
        System.out.println("\n--- Final Deletion ---");
        deletedElement = pq.delete();
        if (deletedElement != -1) {
            System.out.println("Deleted (New Highest Priority): " + deletedElement);
        }
        pq.display();
    }
}

## Output:


![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to implement a Priority Queue and display its elements after insertion and deletion operation is implemented successfully.
