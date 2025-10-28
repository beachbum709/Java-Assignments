# 1
* Flowchart is in current directory

# 2
* I honestly didnt have much challenge with this lab. As soon as I read the Deque class functions i knew exactly what to do. Actually implementing took some time but I was able to wrap my head around it fairly quickly. I think this lab could benefit from giving the student the option to choose which collection class theyd like to use. 

# 3
* https://www.youtube.com/watch?v=htakfj0FIjE

# 4

``` java
import java.util.Deque;
import java.util.LinkedList;
import java.util.Scanner;

public class Collections {
    
    public static boolean palindrome(String text) {
        //making text all lowercase so it can detect if characters match
        String lowerText = text.toLowerCase();
        
        //take each character from characterarray of inputted string and feed it into a deque
        Deque<Character> deque = new LinkedList<>();
        for (char c : lowerText.toCharArray()) {
            deque.addLast(c);
        }
        
        //checking each first and last character, if they match remove them and move to next
        while (deque.size() > 1) {
            char first = deque.removeFirst();
            char last = deque.removeLast();
            
            if (first != last) {
                return false;
            }
        }
        
        return true;
    }
    
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        System.out.println("Enter a word: ");
        String input = scanner.nextLine();
        
        if (palindrome(input)) {
            System.out.println("\"" + input + "\" is a palindrome");
        } else {
            System.out.println("\"" + input + "\" is not a palindrome");
        }
        
        scanner.close();
    }
}


```
