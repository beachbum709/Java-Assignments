# 1

# 2

# 3

# 4

# 5
## Code:
```java
import java.util.Scanner;

public class WordFrequency{
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        String[] wordArray = new String[20];
        int i = 0;
        do{
            System.out.print("Please enter a word (type 'stop' to finish): ");
            String nextword = scanner.nextLine().trim();
            if (nextword.equalsIgnoreCase("stop")){
                break;
            }else{
                wordArray[i] = nextword;
            }
            i++;
        }while(i<20);

        for (String word : wordArray){
            if (word != null && word != " "){
                int frequency = getWordFrequency(wordArray, 0, word);
                System.out.println(word + " " + frequency);
            }
        }

        scanner.close();
    }
    
    
    public static int getWordFrequency(String[] wordsList, int listSize, String currWord){
        int frequency = 0;

        int i = 0;
        for (String word : wordsList){
            if (currWord.equals(wordsList[i])){
                frequency++;
                wordsList[i] = " ";
            }
            i++;
        }
        return frequency;
    }
}

```
