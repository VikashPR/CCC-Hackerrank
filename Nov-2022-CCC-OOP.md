### OO 01 - Basics of Inheritance
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

class HumanBeing{
	void eat(){
		System.out.println("I am eating");
	}
}

//BODY OF THE CODE BEGINS HERE
class Teenager extends HumanBeing{
	void beArrogant(){
		System.out.println("I am being arrogant");
	}
    void reasonlessRebel(){
        System.out.println("I am a rebel");
    }
}
//BODY OF THE CODE ENDS HERE


public class Solution{

   public static void main(String args[]){
	  Teenager teen = new Teenager();
	  teen.eat();
	  teen.beArrogant();
      teen.reasonlessRebel();
   }
}
```

### OO 02 - Basics of Inheritance - II
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

//BODY BEGINS HERE
class Arithmetic{
   public String getName()
   {
       return "Arithmetic";
       
   }
}
class Multiplier extends Arithmetic
{
    public int multiply(int a, int b)
    {
        return a*b;
        
    }   
}
//BODY ENDS HERE

public class Solution{
    public static void main(String []args){
        // Create a new Multiplier object
        Multiplier a = new Multiplier();
        
        // Print the name of the superclass on a new line
        System.out.println("My superclass is: " + a.getClass().getSuperclass().getName());	
        
        // Print the result of 3 calls to Multiplier's `multiply(int,int)` method as 3 space-separated integers:
        System.out.print(a.multiply(5,10) + " " + a.multiply(10,10) + " " + a.multiply(20,10) + "\n");
     }
}
```

### OO 03 - Abstract Classes
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)

```java
import java.io.*;
import java.util.*;
import java.text.*;
import java.math.*;
import java.util.regex.*;

abstract class Arithmetic
{
  abstract int add(int a, int b);
  abstract int subtract(int a, int b);
  abstract int multiply(int a, int b);
  abstract int divide(int a, int b);
}

//BODY STARTS HERE
 class Calculator extends Arithmetic
{
    public int add(int a, int b)
    {
        return a+b;
        
    }
    public int subtract(int a, int b)
    {
        return a-b;
        
    }
    public int multiply(int a, int b)
    {
        return a*b;
        
    }
    public int divide(int a, int b)
    {
        return a/b;
        
    }   
    
}
//BODY ENDS HERE

public class Solution
{
  public static void main(String args[])
  {
    Calculator cal = new Calculator();
   	int A = 10, B = 5;
   	System.out.println("Addition Result : " + cal.add(A, B));
    System.out.println("Subtraction Result : " + cal.subtract(A, B));
    System.out.println("Multiplication Result : " + cal.multiply(A, B));
    System.out.println("Division Result : " + cal.divide(A, B));
  }
}
```
