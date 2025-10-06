# 1

* Flowchart is in current directory

# 2

* My main challenge on this project was getting started. I always feel like I have a block when i first get started. Once I wrote the first class and started getting my brain moving more the project became very easy, it was essentially classes with getters and setters with printall funcitons.

# 3
* https://youtu.be/Oo7oMxLd2o4?si=oKDsaNdZkxHHWPPq&t=147

# 4

```java
public class Course {
    private String courseNum, courseTitle;

    public void setCourseNumber(String num){
        courseNum = num;
    }

    public void setCourseTitle(String title){
        courseTitle = title;
    }

    public String getCourseNumber(){
        return courseNum;
    }

    public String getCourseTitle(){
        return courseTitle;
    }

    public void PrintInfo(){
        System.out.println("Course Information:");
        System.out.println("    Course Number: " + getCourseNumber());
        System.out.println("    Course Title: " + getCourseTitle());
    }

    public static void main(String[] args) {
        //creating our objects
        Course course = new Course();
        OfferedCourse courseOffered = new OfferedCourse();
        //Course class setters
        course.setCourseNumber("ECE287");
        course.setCourseTitle("Digital Systems Design");
        //OfferedCourse class setters
        courseOffered.setCourseNumber("ECE387");
        courseOffered.setCourseTitle("Embedded Systems Design");
        courseOffered.setInstructorName("Mark Patterson");
        courseOffered.setCourseLocation("Wilson Hall 231");
        courseOffered.setClassTime("WF: 2-3:30 pm");
        //Print info from both created objects
        course.PrintInfo();
        courseOffered.PrintInfo();
    }
}


class OfferedCourse extends Course {
    private String instructorName, courseLocation, classTime;

    public void setInstructorName(String name){
        instructorName = name;
    }
    public String getInstructorName(){
        return instructorName;
    }

    public void setCourseLocation(String location){
        courseLocation = location;
    }
    public String getCourseLocation(){
        return courseLocation;
    }

    public void setClassTime(String time){
        classTime = time;
    }
    public String getClassTime(){
        return classTime;
    }

    public void PrintInfo(){
        System.out.println("Course Information:");
        System.out.println("    Course Number: " + getCourseNumber());
        System.out.println("    Course Title: " + getCourseTitle());
        System.out.println("    Instructor Name: " + getInstructorName());
        System.out.println("    Location: " + getCourseLocation());
        System.out.println("    Class Time: " + getClassTime());
    }
}
```
