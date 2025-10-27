# Version 1
```java
package Midterm;
import java.util.*;


public class Aisle1 {
    public void display(){
        System.out.println("Base class method error, no items to display!");
    }

    public void update(int index, String value){
        System.out.println("Base class method error, no items to update!");
    }

    public static void main(String[] args) {
        //Loop variables
        int sectionSelection = 4;
        //Arraylists for each sections items

        //Adding base objects
        Painkillers painkillers = new Painkillers("Tylenol", "Drug Company Inc", "10-2025", 15);
        Bandages bandages = new Bandages("Band-Aid", "BandAid Company Inc", "12-2027", 1, false);
        Equipment equipments = new Equipment("Splint", "Joes Splint Company Inc", 14);

        //Display current aisles and ask the user to select one.
        while(sectionSelection != 3){
            Scanner scnr = new Scanner(System.in);
            System.out.println("\nWelcome to Inventory Control System v1.0! Here are the current available Sections: ");
            System.out.println("\n0-Painkillers, \n1-Bandages, \n2-Equipment, \n\n3-Exit Program");
            System.out.print("\nWhich section would you like to view/update?: ");
            sectionSelection = scnr.nextInt();
            switch (sectionSelection) {
                case 0:
                    String selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-3, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            painkillers.display();
                        }
                        else if (selection.equalsIgnoreCase("0") || selection.equalsIgnoreCase("1") || selection.equalsIgnoreCase("2") || selection.equalsIgnoreCase("3")){
                            int index = Integer.parseInt(selection);
                            painkillers.display(index);
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            System.out.print("\nWhich index would you like to update?");
                            int index = scnr.nextInt();
                            System.out.print("\nWhat value do you want to put at that index?");
                            String value = scnr.next();
                            painkillers.update(index, value);
                        }
                    }
                    break;
                
                case 1:
                    selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-4, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            bandages.display();
                        }
                        else if (selection.equalsIgnoreCase("0") || selection.equalsIgnoreCase("1") || selection.equalsIgnoreCase("2") || selection.equalsIgnoreCase("3") || selection.equalsIgnoreCase("4")){
                            int index = Integer.parseInt(selection);
                            bandages.display(index);
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            System.out.print("\nWhich index would you like to update?");
                            int index = scnr.nextInt();
                            System.out.print("\nWhat value do you want to put at that index?");
                            String value = scnr.next();
                            bandages.update(index, value);
                        }
                    }
                    break;
                
                case 2:
                    selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-2, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            equipments.display();
                        }
                        else if (selection.equalsIgnoreCase("0") || selection.equalsIgnoreCase("1") || selection.equalsIgnoreCase("2")){
                            int index = Integer.parseInt(selection);
                            equipments.display(index);
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            System.out.print("\nWhich index would you like to update?");
                            int index = scnr.nextInt();
                            System.out.print("\nWhat value do you want to put at that index?");
                            String value = scnr.next();
                            equipments.update(index, value);
                        }
                    }
                    break;

            }
        }
        
    }
}

class Painkillers extends Aisle1 {
    private String itemName, drugCompanyName, expiryDate;
    private int ageGroup;
    Painkillers(String name, String companyName, String expiry, int age){
        itemName = name;
        drugCompanyName = companyName;
        expiryDate = expiry;
        ageGroup = age;
    }

    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Drug Company Name: " + drugCompanyName + "\n"+
            "2-Expiration Date: " + expiryDate + "\n"+
            "3-Age: " + ageGroup + "\n"+
            "*********************************\n");
    }

    public void display(int index){
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Drug Company Name: " + drugCompanyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Expiration Date: " + expiryDate + "\n"+
                "*********************************\n");
                break;
            case 3:
                System.out.print(
                "\n*********************************\n"+
                "Age: " + ageGroup + "\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                drugCompanyName = value;
                break;
            case 2:
                expiryDate = value;
                break;
            case 3:
                int parsedInt = Integer.parseInt(value);
                ageGroup = parsedInt;
                break;
        }
    }
}


class Bandages extends Aisle1 {
    private String itemName, companyName, expiryDate;
    private int ageGroup;
    private boolean waterProof;
    Bandages(String name, String compName, String expiry, int age, boolean proof){
        itemName = name;
        companyName = compName;
        expiryDate = expiry;
        ageGroup = age;
        waterProof = proof;
    }


    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Company Name: " + companyName + "\n"+
            "2-Expiration Date: " + expiryDate + "\n"+
            "3-Age: " + ageGroup + "\n"+
            "4-Water Proof: " + waterProof + "\n"+
            "*********************************\n");
    }

    public void display(int index){
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Company Name: " + companyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Expiration Date: " + expiryDate + "\n"+
                "*********************************\n");
                break;
            case 3:
                System.out.print(
                "\n*********************************\n"+
                "Age: " + ageGroup + "\n"+
                "*********************************\n");
                break;
            case 4:
                System.out.print(
                "\n*********************************\n"+
                "Water Proof: " + waterProof + "\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                companyName = value;
                break;
            case 2:
                expiryDate = value;
                break;
            case 3:
                int parsedInt = Integer.parseInt(value);
                ageGroup = parsedInt;
                break;
            case 4:
                boolean parsedBool = Boolean.parseBoolean(value);
                waterProof = parsedBool;
        }
    }
    
}

class Equipment extends Aisle1 {
    private String itemName, companyName;
    private int itemWeight;
    Equipment(String name, String compName, int weight){
        itemName = name;
        companyName = compName;
        itemWeight = weight;
    }


    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Company Name: " + companyName + "\n"+
            "2-Item Weight: " + itemWeight + "lbs\n"+
            "*********************************\n");
    }

    public void display(int index){
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Company Name: " + companyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Item Weight: " + itemWeight + "lbs\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                companyName = value;
                break;
            case 2:
                int parsedInt = Integer.parseInt(value);
                itemWeight = parsedInt;
                break;
        }
    }
    
    
}

```



# Version 2
```java
package Midterm;
import java.util.*;

public class Aisle2 {
    public void display(){
        System.out.println("Base class method error, no items to display!");
    }

    public void update(int index, String value){
        System.out.println("Base class method error, no items to update!");
    }

    public static void main(String[] args) {
        //Loop variables
        int sectionSelection = 4;
        //Arraylists for each sections items

        //Adding base objects
        Painkillers painkillers = new Painkillers("Tylenol", "Drug Company Inc", "10-2025", 15);
        Bandages bandages = new Bandages("Band-Aid", "BandAid Company Inc", "12-2027", 1, false);
        Equipment equipments = new Equipment("Splint", "Joes Splint Company Inc", 14);

        //Display current aisles and ask the user to select one.
        do{
            Scanner scnr = new Scanner(System.in);
            //EXCEPTION ADDED HERE
            try{
                System.out.println("\nWelcome to Inventory Control System v2.0! Here are the current available Sections: ");
                System.out.println("\n0-Painkillers, \n1-Bandages, \n2-Equipment, \n\n3-Exit Program");
                System.out.print("\nWhich section would you like to view/update?: ");
                sectionSelection = scnr.nextInt();
            } catch (InputMismatchException e){
                System.out.println("\nERROR\nInvalid Input. Try again.\nERROR\n");
                sectionSelection = 4;
            }

            switch (sectionSelection) {
                case 0:
                    String selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-3, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            painkillers.display();
                        }
                        else if (selection.equalsIgnoreCase("0") || selection.equalsIgnoreCase("1") || selection.equalsIgnoreCase("2") || selection.equalsIgnoreCase("3")){
                            int index = Integer.parseInt(selection);
                            painkillers.display(index);
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            //EXCEPTION ADDED HERE
                            try{
                                System.out.print("\nWhich index would you like to update?");
                                int index = scnr.nextInt();
                                System.out.print("\nWhat value do you want to put at that index?");
                                String value = scnr.next();
                                painkillers.update(index, value);
                            } catch (InputMismatchException e){
                                System.out.println("\nERROR\nEnter a Valid Index. Display section again if needed.\nERROR\n");
                            }
                        }
                    }
                    break;
                
                case 1:
                    selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-4, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            bandages.display();
                        }
                        else if (selection.equalsIgnoreCase("0") || selection.equalsIgnoreCase("1") || selection.equalsIgnoreCase("2") || selection.equalsIgnoreCase("3") || selection.equalsIgnoreCase("4")){
                            int index = Integer.parseInt(selection);
                            bandages.display(index);
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            System.out.print("\nWhich index would you like to update?");
                            int index = scnr.nextInt();
                            System.out.print("\nWhat value do you want to put at that index?");
                            String value = scnr.next();
                            bandages.update(index, value);
                        }
                    }
                    break;
                
                case 2:
                    selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-2, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            equipments.display();
                        }
                        else if (selection.equalsIgnoreCase("0") || selection.equalsIgnoreCase("1") || selection.equalsIgnoreCase("2")){
                            int index = Integer.parseInt(selection);
                            equipments.display(index);
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            System.out.print("\nWhich index would you like to update?");
                            int index = scnr.nextInt();
                            System.out.print("\nWhat value do you want to put at that index?");
                            String value = scnr.next();
                            equipments.update(index, value);
                        }
                    }
                    break;

            }
        } while(sectionSelection != 3);
        
    }
}

class Painkillers extends Aisle2 {
    private String itemName, drugCompanyName, expiryDate;
    private int ageGroup;
    Painkillers(String name, String companyName, String expiry, int age){
        itemName = name;
        drugCompanyName = companyName;
        expiryDate = expiry;
        ageGroup = age;
    }

    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Drug Company Name: " + drugCompanyName + "\n"+
            "2-Expiration Date: " + expiryDate + "\n"+
            "3-Age: " + ageGroup + "\n"+
            "*********************************\n");
    }

    public void display(int index){
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Drug Company Name: " + drugCompanyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Expiration Date: " + expiryDate + "\n"+
                "*********************************\n");
                break;
            case 3:
                System.out.print(
                "\n*********************************\n"+
                "Age: " + ageGroup + "\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                drugCompanyName = value;
                break;
            case 2:
                expiryDate = value;
                break;
            case 3:
                int parsedInt = Integer.parseInt(value);
                ageGroup = parsedInt;
                break;
        }
    }
}


class Bandages extends Aisle2 {
    private String itemName, companyName, expiryDate;
    private int ageGroup;
    private boolean waterProof;
    Bandages(String name, String compName, String expiry, int age, boolean proof){
        itemName = name;
        companyName = compName;
        expiryDate = expiry;
        ageGroup = age;
        waterProof = proof;
    }


    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Company Name: " + companyName + "\n"+
            "2-Expiration Date: " + expiryDate + "\n"+
            "3-Age: " + ageGroup + "\n"+
            "4-Water Proof: " + waterProof + "\n"+
            "*********************************\n");
    }

    public void display(int index){
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Company Name: " + companyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Expiration Date: " + expiryDate + "\n"+
                "*********************************\n");
                break;
            case 3:
                System.out.print(
                "\n*********************************\n"+
                "Age: " + ageGroup + "\n"+
                "*********************************\n");
                break;
            case 4:
                System.out.print(
                "\n*********************************\n"+
                "Water Proof: " + waterProof + "\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                companyName = value;
                break;
            case 2:
                expiryDate = value;
                break;
            case 3:
                int parsedInt = Integer.parseInt(value);
                ageGroup = parsedInt;
                break;
            case 4:
                boolean parsedBool = Boolean.parseBoolean(value);
                waterProof = parsedBool;
        }
    }
    
}

class Equipment extends Aisle2 {
    private String itemName, companyName;
    private int itemWeight;
    Equipment(String name, String compName, int weight){
        itemName = name;
        companyName = compName;
        itemWeight = weight;
    }


    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Company Name: " + companyName + "\n"+
            "2-Item Weight: " + itemWeight + "lbs\n"+
            "*********************************\n");
    }

    public void display(int index){
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Company Name: " + companyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Item Weight: " + itemWeight + "lbs\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                companyName = value;
                break;
            case 2:
                int parsedInt = Integer.parseInt(value);
                itemWeight = parsedInt;
                break;
        }
    }
    
    
}


```


# Version 3
```java
package Midterm;
import java.util.*;

public class Aisle3 {
    public void display(){
        System.out.println("Base class method error, no items to display!");
    }

    public void update(int index, String value){
        System.out.println("Base class method error, no items to update!");
    }

    public static void main(String[] args) {
        //Loop variables
        int sectionSelection = 4;
        //Arraylists for each sections items

        //Adding base objects
        Painkillers painkillers = new Painkillers("Tylenol", "Drug Company Inc", "10-2025", 15);
        Bandages bandages = new Bandages("Band-Aid", "BandAid Company Inc", "12-2027", 1, false);
        Equipment equipments = new Equipment("Splint", "Joes Splint Company Inc", 14);

        //Display current aisles and ask the user to select one.
        do{
            Scanner scnr = new Scanner(System.in);
            try{
                System.out.println("\nWelcome to Inventory Control System v2.0! Here are the current available Sections: ");
                System.out.println("\n0-Painkillers, \n1-Bandages, \n2-Equipment, \n\n3-Exit Program");
                System.out.print("\nWhich section would you like to view/update?: ");
                sectionSelection = scnr.nextInt();
            } catch (InputMismatchException e){
                System.out.println("\nERROR\nInvalid Input. Try again.\nERROR\n");
                sectionSelection = 4;
            }

            switch (sectionSelection) {
                case 0:
                    String selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-3, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            painkillers.display();
                        }
                        else if (selection.equalsIgnoreCase("0") || selection.equalsIgnoreCase("1") || selection.equalsIgnoreCase("2") || selection.equalsIgnoreCase("3")){
                            int index = Integer.parseInt(selection);
                            painkillers.display(index);
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            try{
                                System.out.print("\nWhich index would you like to update?");
                                int index = scnr.nextInt();
                                System.out.print("\nWhat value do you want to put at that index?");
                                String value = scnr.next();
                                painkillers.update(index, value);
                            } catch (InputMismatchException e){
                                System.out.println("\nERROR\nEnter a Valid Index. Display section again if needed.\nERROR\n");
                            }
                        }
                    }
                    break;
                
                case 1:
                    selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-4, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            bandages.display();
                        }
                        else if (selection.equalsIgnoreCase("0") || selection.equalsIgnoreCase("1") || selection.equalsIgnoreCase("2") || selection.equalsIgnoreCase("3") || selection.equalsIgnoreCase("4")){
                            int index = Integer.parseInt(selection);
                            bandages.display(index);
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            System.out.print("\nWhich index would you like to update?");
                            int index = scnr.nextInt();
                            System.out.print("\nWhat value do you want to put at that index?");
                            String value = scnr.next();
                            bandages.update(index, value);
                        }
                    }
                    break;
                
                case 2:
                    selection = " ";
                    while(!selection.equalsIgnoreCase("exit")){
                        System.out.print("\nWould you like to display, 0-2, update, or exit this section?: ");
                        selection = scnr.next();
                        if (selection.equalsIgnoreCase("display")){
                            equipments.display();
                        }
                        else if (selection.equalsIgnoreCase("update")){
                            System.out.print("\nWhich index would you like to update?");
                            int index = scnr.nextInt();
                            System.out.print("\nWhat value do you want to put at that index?");
                            String value = scnr.next();
                            equipments.update(index, value);
                        }
                        else if (selection.equalsIgnoreCase("exit")){
                            break;
                        }
                        else{
                            //CUSTOMIZED DERIVED EXCEPTION HANDLING
                            try{
                                int index = Integer.parseInt(selection);
                                equipments.display(index);
                            } catch(InvalidIndexException e){
                                System.out.println(e);
                            }
                        }
                    }
                    break;

            }
        } while(sectionSelection != 3);
        
    }
}

class Painkillers extends Aisle3 {
    private String itemName, drugCompanyName, expiryDate;
    private int ageGroup;
    Painkillers(String name, String companyName, String expiry, int age){
        itemName = name;
        drugCompanyName = companyName;
        expiryDate = expiry;
        ageGroup = age;
    }

    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Drug Company Name: " + drugCompanyName + "\n"+
            "2-Expiration Date: " + expiryDate + "\n"+
            "3-Age: " + ageGroup + "\n"+
            "*********************************\n");
    }

    public void display(int index){
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Drug Company Name: " + drugCompanyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Expiration Date: " + expiryDate + "\n"+
                "*********************************\n");
                break;
            case 3:
                System.out.print(
                "\n*********************************\n"+
                "Age: " + ageGroup + "\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                drugCompanyName = value;
                break;
            case 2:
                expiryDate = value;
                break;
            case 3:
                int parsedInt = Integer.parseInt(value);
                ageGroup = parsedInt;
                break;
        }
    }
}


class Bandages extends Aisle3 {
    private String itemName, companyName, expiryDate;
    private int ageGroup;
    private boolean waterProof;
    Bandages(String name, String compName, String expiry, int age, boolean proof){
        itemName = name;
        companyName = compName;
        expiryDate = expiry;
        ageGroup = age;
        waterProof = proof;
    }


    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Company Name: " + companyName + "\n"+
            "2-Expiration Date: " + expiryDate + "\n"+
            "3-Age: " + ageGroup + "\n"+
            "4-Water Proof: " + waterProof + "\n"+
            "*********************************\n");
    }

    public void display(int index){
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Company Name: " + companyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Expiration Date: " + expiryDate + "\n"+
                "*********************************\n");
                break;
            case 3:
                System.out.print(
                "\n*********************************\n"+
                "Age: " + ageGroup + "\n"+
                "*********************************\n");
                break;
            case 4:
                System.out.print(
                "\n*********************************\n"+
                "Water Proof: " + waterProof + "\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                companyName = value;
                break;
            case 2:
                expiryDate = value;
                break;
            case 3:
                int parsedInt = Integer.parseInt(value);
                ageGroup = parsedInt;
                break;
            case 4:
                boolean parsedBool = Boolean.parseBoolean(value);
                waterProof = parsedBool;
        }
    }
    
}

class Equipment extends Aisle3 {
    private String itemName, companyName;
    private int itemWeight;
    Equipment(String name, String compName, int weight){
        itemName = name;
        companyName = compName;
        itemWeight = weight;
    }


    public void display(){
        System.out.print(
            "\n*********************************\n"+
            "0-Name: " + itemName +"\n"+
            "1-Company Name: " + companyName + "\n"+
            "2-Item Weight: " + itemWeight + "lbs\n"+
            "*********************************\n");
    }

    public void display(int index) throws InvalidIndexException{
        if (index > 2){
            throw new InvalidIndexException(index);
        }
        switch (index){
            case 0:
                System.out.print(
                "\n*********************************\n"+
                "Name: " + itemName +"\n"+
                "*********************************\n");
                break;
            case 1:
                System.out.print(
                "\n*********************************\n"+
                "Company Name: " + companyName + "\n"+
                "*********************************\n");
                break;
            case 2:
                System.out.print(
                "\n*********************************\n"+
                "Item Weight: " + itemWeight + "lbs\n"+
                "*********************************\n");
                break;
        }
    }

    @Override public void update(int index, String value){
        switch (index){
            case 0:
                itemName = value;
                break;
            case 1:
                companyName = value;
                break;
            case 2:
                int parsedInt = Integer.parseInt(value);
                itemWeight = parsedInt;
                break;
        }
    }
    
    
}



public class InvalidIndexException extends Exception{
    public InvalidIndexException(int index) {
        super("Index: " + index + " is invalid");
    }
}

```
