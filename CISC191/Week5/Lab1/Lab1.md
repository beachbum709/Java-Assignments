# 1
* Flowchart is in current directory

# 2 
* I didnt have any challenges on this project. I think the extends keyword is self explanatory when it comes to inheriting public methods and variables.

# 3

* https://www.youtube.com/watch?v=Oo7oMxLd2o4

# 4 

```java
// for simplicity I made each class not public except for main class, that way code can stay in one file.

// ===== Code from file Person.java =====
class Person {
   private int ageYears;
   private String lastName;

   public void setName(String userName) {
      lastName  = userName;
   }

   public void setAge(int numYears) {
      ageYears = numYears;
   }

   // Other parts omitted

   public void printAll() {
      System.out.print("Name: " + lastName);
      System.out.print(", Age: "  + ageYears);
   }
}
// ===== end =====

// ===== Code from file Student.java =====
class Student extends Person {
   private int idNum;

   public void setID(int studentId) {
      idNum = studentId;
   }

   public int getID() {
      return idNum;
   }
}
// ===== end =====

// ===== Code from file StudentDerivationFromPerson.java =====
public class StudentDerivationFromPerson {
   public static void main(String[] args) {
      Student courseStudent = new Student();

      /* Your solution goes here  */
      courseStudent.setName("Smith");
      courseStudent.setAge(20);
      courseStudent.setID(7743);

      courseStudent.printAll();
      System.out.println(", ID: " + courseStudent.getID());

   }
}
// ===== end =====
```
