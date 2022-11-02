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
