# 1
flowchart is in the current directory.

# 2
I would scrape the html code. Using regex and a similar algorithm I would filter out all the boilerplate code and count word frequencies. While i feel my current code isnt the best at performance I feel it could do the job. 

# 3
I had issues with the end of the program and printing out the frequency values. I couldnt just simply loop through the word array and print out corresponding frequency values. I had to print out the values then replace all remaining duplicates with a space. That way I could filter out the duplicates that existed in the array after they had been counted.

# 4
https://youtu.be/7MqR-3-ACbs

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
