# Ex2(A) Dequeue Elements from Circular Queue
## DATE:06-09-2025
## AIM:
To write a **Java program** to implement a Circular Queue and demonstrate the deletion (dequeue) of multiple elements from a filled queue.

## Algorithm:
1.  Start.
2.  Define a class, `CircularQueue`, with a fixed size `MAX_SIZE` and initialize the queue array, **front**, and **rear** pointers to -1.
3.  Define the `isEmpty()` method to check if **front** is -1.
4.  Define the `enQueue()` method to add elements until the queue is full (for demonstration purposes).
5.  Define the **`deQueue()`** method to remove an element from the **front** of the queue:
    a. If `isEmpty()` is true, print an error message (Underflow).
    b. Otherwise, store the element at the **front** index.
    c. If **front** equals **rear**, reset both to -1 (last element removed).
    d. If the queue has more than one element, update **front** using the modulo operation: `front = (front + 1) % MAX_SIZE`.
    e. Return the removed element.
6.  In the `main` method, enqueue enough elements to fill the queue.
7.  Call `deQueue()` multiple times (e.g., three times) to demonstrate deletion from a filled circular queue.
8.  End.


## Program:
/*
Program to delete three elements from the filled circular queue
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/
import java.util.Scanner;

public class CircularQueue {
    private static final int MAX_SIZE = 5; // Fixed size for the queue
    private int[] items;
    private int front;
    private int rear;

    public CircularQueue() {
        items = new int[MAX_SIZE];
        front = -1;
        rear = -1;
    }

    // Function to check if the queue is empty
    public boolean isEmpty() {
        return front == -1;
    }

    // Function to check if the queue is full
    public boolean isFull() {
        return (front == 0 && rear == MAX_SIZE - 1) || (front == rear + 1);
    }

    // Function to add an element
    public void enQueue(int element) {
        if (isFull()) {
            System.out.println("Queue is Full! Cannot Enqueue " + element);
        } else {
            if (front == -1)
                front = 0;
            rear = (rear + 1) % MAX_SIZE;
            items[rear] = element;
            System.out.println("Enqueued: " + element);
        }
    }

    // Function to delete an element (Dequeue)
    public int deQueue() {
        if (isEmpty()) {
            System.out.println("Queue is Empty!! (Underflow)");
            return -1; // Indicate failure
        } else {
            int element = items[front];
            
            // Case 1: Only one element in the queue
            if (front == rear) {
                front = -1;
                rear = -1;
            } 
            // Case 2: More than one element
            else {
                front = (front + 1) % MAX_SIZE;
            }
            return element;
        }
    }

    public static void main(String[] args) {
        CircularQueue queue = new CircularQueue();

        // Fill the queue (5 elements)
        System.out.println("--- Filling the Queue (MAX_SIZE=5) ---");
        queue.enQueue(10);
        queue.enQueue(20);
        queue.enQueue(30);
        queue.enQueue(40);
        queue.enQueue(50); 
        System.out.println("--------------------------------------");

        // Dequeue three elements as required by the AIM
        System.out.println("--- Dequeuing Three Elements ---");
        
        int dequeued1 = queue.deQueue();
        if (dequeued1 != -1) System.out.println("Dequeued element 1: " + dequeued1);

        int dequeued2 = queue.deQueue();
        if (dequeued2 != -1) System.out.println("Dequeued element 2: " + dequeued2);

        int dequeued3 = queue.deQueue();
        if (dequeued3 != -1) System.out.println("Dequeued element 3: " + dequeued3);
        
        System.out.println("--------------------------------------");

        // Show remaining state
        System.out.println("Queue is Empty: " + queue.isEmpty());
    }
}

## Output:


![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)

## Result:
Thus, the **Java program** to implement a Circular Queue and demonstrate the deletion of three elements from the filled circular queue is implemented successfully.
