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

### OO 04 - Interface
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
```java
import java.util.*;
import java.math.*;
interface AdvancedArithmetic{
  int divisor_sum(int n);
}

//BODY STARTS HERE
class MyCalculator implements AdvancedArithmetic{
    public int divisor_sum(int n){
        int cnt = 0;
        for (int i = 1; i <= Math.sqrt(n); i++)
        {
            if (n % i == 0) {
                // If divisors are equal,
                // count only one
                if (n / i == i)
                    cnt++;
 
                else // Otherwise count both
                    cnt = cnt + 2;
            }
        }
        return cnt;
    }
}

//BODY ENDS HERE

class Solution{
    public static void main(String []args){
        MyCalculator my_calculator = new MyCalculator();
        System.out.print("I implemented: ");
        ImplementedInterfaceNames(my_calculator);
        Scanner sc = new Scanner(System.in);
        int n = sc.nextInt();
        System.out.print(my_calculator.divisor_sum(n) + "\n");
      	sc.close();
    }
    /*
     *  ImplementedInterfaceNames method takes an object and prints the name of the interfaces it implemented
     */
    static void ImplementedInterfaceNames(Object o){
        Class[] theInterfaces = o.getClass().getInterfaces();
        for (int i = 0; i < theInterfaces.length; i++){
            String interfaceName = theInterfaces[i].getName();
            System.out.println(interfaceName);
        }
    }
}
```

### OO 05 - Comparator Interface
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
```java
import java.util.*;
import java.lang.*;
import java.io.*;

class Point
{
	public int x;
	public int y;
	public Point(int _x, int _y)
	{
		x = _x;
		y = _y;
	}
}

//BODY STARTS HERE

class sortByX implements Comparator<Point>
{
	public int compare(Point a,Point b){
        if(a.y==b.y){
        return a.x-b.x;
        }
        else{
        return a.y-b.y;
        }
}
}

//BODY ENDS HERE

public class Solution
{
	public static void main (String[] args)
	{
		// your code goes here
		ArrayList<Point> ar = new ArrayList<Point>();
		ar.add(new Point(1,1));
		ar.add(new Point(1,2));
		ar.add(new Point(2,2));
		ar.add(new Point(2,1));
		
		Collections.sort(ar, new sortByX());
		
		for (int i = 0; i < 4; i++)
		{
			System.out.println(ar.get(i).x + " " + ar.get(i).y);
		}
	}
}
```

### OO 06 - Method Overriding in Java
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
```java
import java.util.*;
class DisneyCharacter{
    String getName(){
        return "Anonymous Disney Character";
    }
    String getPantsState(){
        return  "I may or may not be wearing pants";
    }
}
class DonaldDuck extends DisneyCharacter
{
   String getName()
   {
      return "DonaldDuck";
   }
    String getPantsState()
   {
      return "I do not wear pants";
   }
}
class MickeyMouse extends DisneyCharacter
{
   String getName()
   {
      return "MickeyMouse";
   }
    String getPantsState()
   {
      return "I wear pants";
   }
}
public class Solution{
	
    public static void main(String []args){
      	DisneyCharacter c0 = new DisneyCharacter();
        DonaldDuck c1 = new DonaldDuck();
        MickeyMouse c2 = new MickeyMouse();
	    System.out.println(c0.getName());
        System.out.println(c0.getPantsState());
        System.out.println(c1.getName());
        System.out.println(c1.getPantsState());
        System.out.println(c2.getName());
        System.out.println(c2.getPantsState());
	}
}
```

### OO 07 - The Super Keyword
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
```java
import java.util.*;
import java.io.*;

class BiCycle{
    String define_me(){
        return "a vehicle with pedals.";
    }
}

class MotorCycle extends BiCycle{
    String define_me(){
        return "a cycle with an engine.";
    }
    
    MotorCycle(){
        System.out.println("Hello I am a motorcycle, I am "+ define_me());

        // String temp=define_me(); //Fix this line
        String temp=super.define_me(); //Fixed

        System.out.println("My ancestor is a cycle who is "+ temp );
    }
    
}
class Solution{
    public static void main(String []args){
        MotorCycle M=new MotorCycle();
    }
}
```

### OO 08 - InstanceOf Keyword
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
```java
import java.util.*;


class Student{}
class Rockstar{}
class Hacker{}


public class InstanceOFTutorial{
   
   static String count(ArrayList mylist){
      int a = 0,b = 0,c = 0;
      for(int i = 0; i < mylist.size(); i++){
         Object element=mylist.get(i);
         if(element instanceof Student)
            a++;
         if(element instanceof Rockstar)
            b++;
         if(element instanceof Hacker)
            c++;
      }
      String ret = Integer.toString(a)+" "+ Integer.toString(b)+" "+ Integer.toString(c);
      return ret;
   }

   public static void main(String []args){
      ArrayList mylist = new ArrayList();
      Scanner sc = new Scanner(System.in);
      int t = sc.nextInt();
      for(int i=0; i<t; i++){
         String s=sc.next();
         if(s.equals("Student"))mylist.add(new Student());
         if(s.equals("Rockstar"))mylist.add(new Rockstar());
         if(s.equals("Hacker"))mylist.add(new Hacker());
      }
      System.out.println(count(mylist));
   }
}
```

### OO 09 - Iterator in Java
![java](https://img.shields.io/badge/Java-ED8B00?style=for-the-badge&logo=java&logoColor=white)
```java
import java.util.*;
public class Main{
   
   static Iterator func(ArrayList mylist){
      Iterator it=mylist.iterator();
      while(it.hasNext()){
         Object element = it.next();
         if(element instanceof String)//Hints: use instanceof operator
            break;
      }
      return it;
      
   }
   @SuppressWarnings({ "unchecked" })
   public static void main(String []args){
      ArrayList mylist = new ArrayList();
      Scanner sc = new Scanner(System.in);
      int n = sc.nextInt();
      int m = sc.nextInt();
      for(int i = 0;i<n;i++){
         mylist.add(sc.nextInt());
      }
      
      mylist.add("###");
      for(int i=0;i<m;i++){
         mylist.add(sc.next());
      }
      
      Iterator it=func(mylist);
      while(it.hasNext()){
         Object element = it.next();
         System.out.println((String)element);
      }
   }
}
```
