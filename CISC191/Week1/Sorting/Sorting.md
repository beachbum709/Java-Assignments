# Sorting Code:

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
