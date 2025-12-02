# Ex2(E) Applications of Queue – FCFS
## DATE:06-09-2025
## AIM:
To write a **Java program** to calculate the turnaround time and waiting time of each process in the **First-Come, First-Served (FCFS)** CPU scheduling algorithm.

## Algorithm:
1.  Start the program.
2.  Define a method, `findTimes()`, that accepts the number of processes ($n$), and arrays for process ID ($proc[]$) and burst time ($burst\_time[]$).
3.  Initialize arrays for waiting time ($wait\_time[]$) and turnaround time ($tat[]$).
4.  **Waiting Time Calculation (FCFS):**
    a. The waiting time for the first process ($wait\_time[0]$) is 0.
    b. For every subsequent process $i$ from 1 to $n-1$, $wait\_time[i]$ is calculated as $wait\_time[i-1] + burst\_time[i-1]$.
5.  **Turnaround Time Calculation:**
    a. For every process $i$ from 0 to $n-1$, $tat[i]$ is computed as $burst\_time[i] + wait\_time[i]$.
6.  Display the results in a table format showing Process ID, Burst Time, Waiting Time, and Turnaround Time.
7.  End the algorithm.

## Program:
/*
Program to calculate Waiting Time and Turnaround Time for FCFS Scheduling (Queue Application)
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/
import java.util.Arrays;

public class FCFSScheduling {

    // Method to calculate waiting time and turnaround time
    static void findTimes(int proc[], int n, int burst_time[]) {
        int wait_time[] = new int[n];
        int tat[] = new int[n];
        int total_wt = 0;
        int total_tat = 0;

        // 1. Calculate Waiting Time
        wait_time[0] = 0; // First process has 0 waiting time

        for (int i = 1; i < n; i++) {
            // Waiting time = sum of burst times of previous processes
            wait_time[i] = wait_time[i - 1] + burst_time[i - 1];
        }

        // 2. Calculate Turnaround Time and Total Times
        System.out.println("\nFCFS Scheduling Results:");
        System.out.println("--------------------------------------------------");
        System.out.println("Process\t\tBurst Time\tWaiting Time\tTurnaround Time");
        System.out.println("--------------------------------------------------");

        for (int i = 0; i < n; i++) {
            // Turnaround Time = Burst Time + Waiting Time
            tat[i] = burst_time[i] + wait_time[i];

            total_wt += wait_time[i];
            total_tat += tat[i];

            System.out.println(" P" + proc[i] + "\t\t" + burst_time[i] + "ms\t\t" +
                                wait_time[i] + "ms\t\t" + tat[i] + "ms");
        }
        System.out.println("--------------------------------------------------");

        // 3. Display Average Times
        System.out.printf("Average Waiting Time = %.2f ms\n", (float) total_wt / n);
        System.out.printf("Average Turnaround Time = %.2f ms\n", (float) total_tat / n);
    }

    public static void main(String[] args) {
        // Sample data for processes:
        int proc[] = {1, 2, 3}; // Process IDs
        int burst_time[] = {10, 5, 8}; // Burst times for P1, P2, P3
        int n = proc.length;

        findTimes(proc, n, burst_time);
    }
}

## Output:


[![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)]

## Result:
Thus, the **Java program** to calculate the turnaround time and waiting time of each process in the First-Come, First-Served (FCFS) CPU scheduling algorithm is implemented successfully.
