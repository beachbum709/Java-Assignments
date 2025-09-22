# 1
* flowchart is in the current directory of this file.

# 2
* This is going to sound funny but my main challenge was figuring out how to go to next line in the while(hasnextline) function. I spent a good amount of time wondering why my loop wasnt closing as i thought it naturally went to the next line. I didnt realize that i needed the inFile.nextLine() function at the end of the block.

# 3

* https://youtu.be/YXuydwIipt4

# 4
## Java Code
```java
import java.util.*;
import java.io.*;

public class PhotoParcer {
    public static void main(String[] args) throws IOException {
        //Array to add lines to
        ArrayList<String> photos = new ArrayList<String>();
        //Input
        System.out.println("Reading file");
        FileInputStream fileInStream = new FileInputStream("ParkPhotos.txt");
        Scanner inFile = new Scanner(fileInStream);
        //read every line up to _ and put it into an array with info.txt at the end
        while (inFile.hasNextLine()){
            photos.add(inFile.findInLine("[a-zA-Z0-9]+_") + "info.txt");
            inFile.nextLine();
        }
        System.out.println("File read and contents gathered");
        //Output
        FileOutputStream fileOutStream = new FileOutputStream("ParkPhotos.txt");
        PrintWriter outFile = new PrintWriter(fileOutStream);
        //printing out every element of photo array to file
        for(int i = 0; i < photos.size(); i++){
            outFile.println(photos.get(i));
        }
        System.out.println("Contents printed to txt file");

        inFile.close();
        outFile.close();
    }
}

```

## Text File

Acadia2003_photo.jpg
AmericanSamoa1989_photo.jpg
BlackCanyonoftheGunnison1983_photo.jpg
CarlsbadCaverns2010_photo.jpg
CraterLake1996_photo.jpg
GrandCanyon1996_photo.jpg
IndianaDunes1987_photo.jpg
LakeClark2009_photo.jpg
Redwood1980_photo.jpg
VirginIslands2007_photo.jpg
Voyageurs2006_photo.jpg
WrangellStElias1987_photo.jpg
