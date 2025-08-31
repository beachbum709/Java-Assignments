# 1

# 2

# 3

# 4

# 5
## Code:
```java
import java.util.Scanner;


public class WordFrequency {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        System.out.println("Enter your words: ");
        String input = scanner.nextLine();
        String[] words = input.split("\\s+");
        for (int i = 0; i < words.length; i++) {
            words[i] = words[i].replaceAll("[^\\w]", "");
        }
        int[] count = new int[words.length];
        getWordFrequency(words, count);
        System.out.println("\n");
        for (int i = 0; i < count.length; i++){
            if (count[i] != 0)
                System.out.println(words[i] + " " + count[i]);
        }

        scanner.close();
    }

    public static void getWordFrequency(String[] wordArr, int[] countArr){
        countArr[0] = 1;
        for (int i = 1, j = 0; i < wordArr.length; i++) {
            if (wordArr[j].equals(wordArr[i])) {
                countArr[j]++;
            } else {
                j++;
                wordArr[j] = wordArr[i];
                countArr[j] = 1;
            }
        }
    }
}


```
