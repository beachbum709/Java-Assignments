# 1

* Flowchart is in current directory

# 2

* I had a hard time understanding on when to override vs overload. It seemed that when I didnt use override i was able to recreate the function without any issue and no different parameters. This is less of a challenge and more of an understanding issue. I'm currently looking into it more and hope to understand when to use each more clearly.

# 3
* https://youtu.be/Oo7oMxLd2o4?si=Jw82rLYLeBlx2270&t=341

# 4

```java
public class Book {
    private String title, author, publisher, publicationDate;

    public String getTitle(){
        return title;
    }
    public void setTitle(String bookTitle){
        title = bookTitle;
    }

    public String getAuthor(){
        return author;
    }
    public void setAuthor(String bookAuthor){
        author = bookAuthor;
    }

    public String getPublisher(){
        return publisher;
    }
    public void setPublisher(String bookPublisher){
        publisher = bookPublisher;
    }

    public String getDate(){
        return publicationDate;
    }
    public void setDate(String bookDate){
        publicationDate = bookDate;
    }
    

    public void printInfo(){
        System.out.println("Book Information: ");
        System.out.println("    Book Title: " + title);
        System.out.println("    Author: " + author);
        System.out.println("    Publisher: " + publisher);
        System.out.println("    Publication Date: " + publicationDate);
    }

    public static void main(String[] args) {
        Book newbook = new Book();
        Encyclopedia newEncyclopedia = new Encyclopedia();
        
        //setting book variables and printing out info
        newbook.setAuthor("J. R. R. Tolkien");
        newbook.setDate("21 September 1937");
        newbook.setTitle("The Hobbit");
        newbook.setPublisher("George Allen & Unwin");
        newbook.printInfo();

        //setting encyclopedia variables and printing info
        newEncyclopedia.setAuthor("Ian Ridpath");
        newEncyclopedia.setDate("2001");
        newEncyclopedia.setTitle("The Illustrated Encyclopedia of the Universe");
        newEncyclopedia.setPublisher("Watson-Guptill");
        newEncyclopedia.setEdition("2nd");
        newEncyclopedia.setPages(384);
        newEncyclopedia.printInfo();
        
    }
}


class Encyclopedia extends Book {
    private String edition;
    private int pages;

    //getters and setters
    public int getPages(){
        return pages;
    }
    public void setPages(int pageNum){
        pages = pageNum;
    }

    public String getEdition(){
        return edition;
    }
    public void setEdition(String estring){
        edition = estring;
    }

    //override of printinfo from book to include edition and pages
    @Override public void printInfo(){
        System.out.println("Book Information: ");
        System.out.println("    Book Title: " + getTitle());
        System.out.println("    Author: " + getAuthor());
        System.out.println("    Publisher: " + getPublisher());
        System.out.println("    Publication Date: " + getDate());
        System.out.println("    Edition: " + edition);
        System.out.println("    Number of pages: " + pages);
    }
}
```
