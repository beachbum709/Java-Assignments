# 1
* Flowchart is provided in the current directory.

# 2
* My main challenge was understanding the difference between primitives and Objects and where they were stored on the stack and the heap. More specifically the String object. I was under the impression coming into this project that the String object was treated as a primitive but through research discovered otherwise. This helped underestand that mostly object values are stored in the heap while primitive values can be stored in the stack.

# 3
* https://www.youtube.com/watch?v=-LbwsRg1kAs

# 4
```java
public class DogCreator {
    private static Dog createDog(int legs, String name){
        return new Dog(legs, name);
    }


    public static void main(String[] args) {
       int legs = 4;
       String name = "Oliver";
       Dog dog = createDog(legs, name);

       System.out.println(dog.name + " " + dog.legs);

       name = "Jack";

       System.out.println(name + " " + dog.legs);
    }
}

class Dog {

    int legs;
    String name;
    
    public Dog(int legs, String name){
        this.legs = legs;
        this.name = name;
    }

}
```
