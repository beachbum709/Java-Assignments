
# 1
* Flowchart is in current directory

# 2
* I found finding the right place to iterate for the comparison to be hard. Including adding an initial value because of the sorting algorithm having to start past the first number.

# 3
* https://www.youtube.com/watch?v=5MamtbYXxMk

# 4
``` java
public class InsertionSort {
    public static void insertionSort(int [] numbers) {
        int i,j,temp;
        int comparisons = 2;
        int swaps = 0;

        for (i = 1; i < numbers.length; ++i) {
            j = i;

            while (j > 0 && numbers[j] < numbers[j - 1]) {

                temp = numbers[j];
                numbers[j] = numbers[j - 1];
                numbers[j - 1] = temp;
                --j;
                swaps++;
                
                
            }
            for (int k = 0; k < numbers.length; ++k) {
                System.out.print(numbers[k] + " ");
            }
            System.out.println();
            comparisons++;
        }
        System.out.println();
        System.out.println("comparisons: " + Integer.toString(comparisons));
        System.out.println("swaps: " + Integer.toString(swaps));
    }

    public static void main(String [] args) {
        int [] numbers = {6, 3, 2, 1, 5, 9, 8};
        int i;

        for (i = 0; i < numbers.length; ++i) {
            System.out.print(numbers[i] + " ");
        }
        System.out.println();
        System.out.println();

        insertionSort(numbers);

    }
}


```
