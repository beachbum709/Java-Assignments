# 1
* Flowchart is in current directory

# 2
* I have not done much SQL before so learning a new language with no commands proved to be quite time consuming. I also had a challenge when using executeQuery and not realizing I had to use executeUpdate.

# 3
* https://www.youtube.com/watch?v=NuxYq9oM5IY

# 4
``` java
package sql;
import java.sql.*;

public class SimpleJdbc {

  public static void main(String[] args)

    throws SQLException, ClassNotFoundException {

    // Load the JDBC driver
    Class.forName("com.mysql.cj.jdbc.Driver");
    System.out.println("Driver loaded");

    

    // Establish a connection
    Connection connection = DriverManager.getConnection("jdbc:mysql://localhost/Miramar","testuser","");
    System.out.println("Database connected");

    

    // Create a statement

    Statement statement = connection.createStatement();

    

    // Execute a statement
    statement.executeUpdate("delete from Student where firstName ='Phillip';");
    statement.executeUpdate("insert into Student (ssn,firstname,mi,lastname,birthDate,deptId) values ('111222333', 'Phillip', 'D', 'Collins', '1950-01-30', '1234');");
    statement.executeUpdate("update Student set zipCode ='92126' where firstName ='Phillip';");
    ResultSet resultSet = statement.executeQuery("select * from Student;");

      

      // Iterate through the result and print the student names
    while (resultSet.next())
      System.out.println(resultSet.getString(1) + "\t" +
        resultSet.getString(2) + "\t" + 
        resultSet.getString(3) + "\t" +
        resultSet.getString(4) + "\t" + 
        resultSet.getString(5) + "\t" +
        resultSet.getString(6) + "\t" +
        resultSet.getString(7) + "\t" +
        resultSet.getString(8) + "\t" +
        resultSet.getString(9) + "\t");

    
    // Close the connection
    connection.close();

  }

}


```
