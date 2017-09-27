
public class CallingMethodsInSameClass
{
	public static void main(String[] args) {
		printOne();
		printOne();
		printTwo();
	}

	public static void printOne() {
		System.out.println("Hello World");
	}

	public static void printTwo() {
		printOne();
		printOne();}
    }


      

public class HelloWorld {
   public static void main(String[] args) {
      // Prints "Hello, World" in the terminal window.
      System.out.println("Hello, World");
   }
}






