# Ex2(D) Applications of Queue - SJF
## DATE:06-09-2025
## AIM:
To write a **Java program** to calculate the **Total Waiting Time** and **Average Waiting Time**, along with **Turnaround Time**, for processes using the non-preemptive **Shortest Job First (SJF)** CPU scheduling algorithm.

## Algorithm:
1.  Start.
2.  Define a class to hold the process data (ID, Burst Time, Waiting Time, Turnaround Time).
3.  Read the number of processes $n$ and their burst times into an array/list of process objects.
4.  **Sort** the processes based on their **Burst Time** in ascending order. This is the core of the SJF algorithm.
5.  Initialize the waiting time ($wt$) and turnaround time ($tat$) for the first process (at index 0):
    a. $wt[0] = 0$.
    b. $tat[0] = burst\_time[0]$.
6.  Loop through the remaining processes ($i=1$ to $n-1$):
    a. Calculate $wt[i]$ by summing the burst times of all processes scheduled before it (i.e., $wt[i] = wt[i-1] + burst\_time[i-1]$).
    b. Calculate $tat[i] = burst\_time[i] + wt[i]$.
7.  Calculate the **Total Waiting Time** and **Total Turnaround Time** by summing the respective arrays.
8.  Compute the **Average Waiting Time** and **Average Turnaround Time** by dividing the totals by $n$.
9.  Display the results, including the sorted order of execution.
10. End.


## Program:
/*
Program to find the Total Waiting Time and Average Waiting Time in Shortest Job First scheduling algorithm.
Developed by: Dharani dharan K
RegisterNumber: 212223040036
*/
import java.util.Arrays;
import java.util.Comparator;
import java.util.Scanner;

class Process {
    int id;
    int bt; // Burst Time
    int wt; // Waiting Time
    int tat; // Turnaround Time
    
    public Process(int id, int bt) {
        this.id = id;
        this.bt = bt;
    }
}

public class SJFScheduling {
    
    static void findTimes(Process[] processes, int n) {
        float total_wt = 0;
        float total_tat = 0;

        // 1. Sort processes by Burst Time (SJF)
        // Java's Arrays.sort is used here
        Arrays.sort(processes, Comparator.comparingInt(p -> p.bt));

        // 2. Initialize the first process's times
        processes[0].wt = 0;
        processes[0].tat = processes[0].bt;
        total_tat += processes[0].tat;

        // 3. Calculate waiting time and turnaround time for remaining processes
        for (int i = 1; i < n; i++) {
            // Waiting Time = Waiting Time of previous process + Burst Time of previous process
            processes[i].wt = processes[i - 1].wt + processes[i - 1].bt;
            total_wt += processes[i].wt;

            // Turnaround Time = Burst Time + Waiting Time
            processes[i].tat = processes[i].bt + processes[i].wt;
            total_tat += processes[i].tat;
        }

        // 4. Print results
        System.out.println("SJF Scheduling Results:");
        System.out.println("--------------------------------------------------");
        System.out.println("Process\t\tBurst Time\tWaiting Time\tTurnaround Time");
        System.out.println("--------------------------------------------------");
        
        for (int i = 0; i < n; i++) {
            System.out.println(" P" + processes[i].id + "\t\t" + processes[i].bt + "ms\t\t" +
                                processes[i].wt + "ms\t\t" + processes[i].tat + "ms");
        }
        System.out.println("--------------------------------------------------");

        // 5. Compute and print averages
        float avg_wt = total_wt / n;
        float avg_tat = total_tat / n;

        System.out.printf("Average Waiting Time = %.2f ms\n", avg_wt);
        System.out.printf("Average Turnaround Time = %.2f ms\n", avg_tat);
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        // Hardcoded example for consistency with typical experiments
        int n = 4;
        Process[] processes = new Process[n];
        
        // Example Burst Times: P1=6, P2=8, P3=7, P4=3
        processes[0] = new Process(1, 6);
        processes[1] = new Process(2, 8);
        processes[2] = new Process(3, 7);
        processes[3] = new Process(4, 3);
        
        System.out.println("Number of Processes: " + n);
        System.out.println("Input Burst Times: P1=6, P2=8, P3=7, P4=3");
        
        findTimes(processes, n);
    }
}

## Output:
![image](https://github.com/user-attachments/assets/23cf1270-fdba-4c49-ae95-3c2c5f339d3a)
## Result:
Thus, the **Java program** to calculate the Total Waiting Time and Average Waiting Time in the Shortest Job First scheduling algorithm is implemented successfully.
