# 1
Flowchart has been uploaded as a png in the folder containing this file.

# 2
While I had a good amount of ideas of how I wanted to approach this project, I chose the bubble sorting algorithm you mentioned in the assignment text. I was unfamiliar with it so it gave me a new challenge.

# 3
My main challenge was understanding how the sorting algorithm worked. Everything else was just a refresher from the previous java class I had just taken. Also getting the whole github setup was a process on its own that i had never done.

# 4
ADD LINK HERE



# 5
## Sorting Code:

```java
import java.util.Scanner;


class Sorting {

    public static void sortArray(int[] myArr, int arrSize){

        for (int i = 0; i < arrSize - 1; i++){
            for (int j = 0; j < arrSize - i - 1; j++){
                if (myArr[j] < myArr[j + 1]) {
                    int temp = myArr[j];
                    myArr[j] = myArr[j + 1];
                    myArr[j + 1] = temp;
                }
            }
        }
    }

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.print("Please Enter Amount: ");
        int amount = scanner.nextInt();
        int[] unsortedArr = new int[amount];
        int i = 0;
        do{
            unsortedArr[i] = scanner.nextInt();
            i++;
        }while(i<amount);

        sortArray(unsortedArr, unsortedArr.length);

        for (int j : unsortedArr){
            System.out.print(j + " ");
        }

        scanner.close();
    }
}
```
