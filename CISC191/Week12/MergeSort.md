
# 1
* Flowchart is in current directory

# 2
* My biggest challenge was implementing the algorithm itself. Keeping track of partitions and merging values proved to be very complicated.

# 3
* https://www.youtube.com/watch?v=NGpMpih7GtU

# 4
``` java
public class MergeSort {
    public static int merge(int [] numbers, int i, int j, int k) {
        int mergedSize = k - i + 1;       // Size of merged partition
        int mergedNumbers [] = new int[mergedSize]; // Temporary array for merged numbers
        int mergePos;                     // Position to insert merged number
        int leftPos;                      // Position of elements in left partition
        int rightPos;                     // Position of elements in right partition
        int comparisons = 2;

        mergePos = 0;
        leftPos = i;                      // Initialize left partition position
        rightPos = j + 1;                 // Initialize right partition position

        // Add smallest element from left or right partition to merged numbers
        while (leftPos <= j && rightPos <= k) {
            if (numbers[leftPos] < numbers[rightPos]) {
                mergedNumbers[mergePos] = numbers[leftPos];
                ++leftPos;
            }
            else {
                mergedNumbers[mergePos] = numbers[rightPos];
                ++rightPos;
            }
            ++mergePos;
        }

        // If left partition is not empty, add remaining elements to merged numbers
        while (leftPos <= j) {
            mergedNumbers[mergePos] = numbers[leftPos];
            ++leftPos;
            ++mergePos;
        }

        // If right partition is not empty, add remaining elements to merged numbers
        while (rightPos <= k) {
            mergedNumbers[mergePos] = numbers[rightPos];
            ++rightPos;
            ++mergePos;
        }

        // Copy merge number back to numbers
        for (mergePos = 0; mergePos < mergedSize; ++mergePos) {
            numbers[i + mergePos] = mergedNumbers[mergePos];
            comparisons++;
        }
        return comparisons;
    }

    public static int mergeSort(int [] numbers, int i, int k) {
        int j;
        int comparisons = 0 ;

        if (i < k) {
            j = (i + k) / 2;  // Find the midpoint in the partition
            
            // Recursively sort left and right partitions
            mergeSort(numbers, i, j);
            mergeSort(numbers, j + 1, k);

            // Merge left and right partition in sorted order
            comparisons = merge(numbers, i, j, k);
        }
        return comparisons;
    }

    public static void main(String [] args) {
        int [] numbers = {3, 2, 1, 5, 9, 8};
        int i;

        System.out.print("UNSORTED: ");
        for (i = 0; i < numbers.length; ++i) {
            System.out.print(numbers[i] + " ");
        }
        System.out.println();

        /* initial call to merge sort with index */

        mergeSort(numbers, 0, numbers.length - 1);

        System.out.print("SORTED: ");
        for (i = 0; i < numbers.length; ++i) {
            System.out.print(numbers[i] + " ");
        }
        System.out.println();

        System.out.println("comparisons: " + Integer.toString(mergeSort(numbers, 0, numbers.length - 1)));
    }
}


```
