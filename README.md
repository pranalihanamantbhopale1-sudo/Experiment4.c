# Experiment No. 04

## Title
**Greedy method to solve problems of Optimal Merge Pattern.**

### Analyse Time and Space Complexity

### Student Details
- **Email:** pranalihanamantbhopale1@gmail.com
- **GitHub:** https://github.com/pranalihanamantbhopale1-sudo/Experiment4.c

---

## Aim

To implement the **Greedy Method to solve problems of Optimal Merge Pattern** and analyze its time and space complexity.

---

## Program

```c
#include <stdio.h> 

void optimalMerge(int files[], int n){ 
    int totalCost = 0; 
    for (int i = 0; i < n - 1; i++){ 
        int firstMin = 9999, secondMin = 9999; 
        int firstIndex = -1, secondIndex = -1; 
 
        for (int j = 0; j < n; j++){ 
            if (files[j] != -1 && files[j] < firstMin) { 
                secondMin = firstMin; 
                secondIndex = firstIndex; 
                firstMin = files[j]; 
                firstIndex = j; 
            } 
            else if (files[j] != -1 && files[j] < secondMin) { 
                secondMin = files[j]; 
                secondIndex = j; 
            } 
        } 
 
        int newFile = firstMin + secondMin; 
        totalCost += newFile; 
        files[firstIndex] = newFile; 
        files[secondIndex] = -1; 
    } 

    printf("Minimum total cost of merging files: %d\n", totalCost); 
} 

int main(){ 
    int n; 
    printf("Enter number of files: "); 
    scanf("%d", &n); 

    int files[n]; 

    printf("Enter sizes of files: "); 
    for (int i = 0; i < n; i++) 
        scanf("%d", &files[i]); 

    optimalMerge(files, n); 

    return 0; 
}
