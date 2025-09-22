# 1
* flowchart is in the current directory of this file.

# 2
* This is going to sound funny but my main challenge was figuring out how to go to next line in the while(hasnextline) function. I spent a good amount of time wondering why my loop wasnt closing as i thought it naturally went to the next line. I didnt realize that i needed the inFile.nextLine() function at the end of the block.

# 3

* video link

# 4
java
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

***
