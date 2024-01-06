# Assignment 1
## Part 1
```java=
public class MyInitials {

	public static void main(String[] args) {
		System.out.println("Y   Y  H   H   CCC  ");
		System.out.println(" Y Y   H   H  C   C ");
		System.out.println("  Y    H   H  C     ");
		System.out.println("  Y    HHHHH  C     ");
		System.out.println("  Y    H   H  C     ");
		System.out.println("  Y    H   H  C   C ");
		System.out.println("  Y    H   H   CCC  ");
	}
}
```
```shell=
Y   Y  H   H   CCC  
 Y Y   H   H  C   C 
  Y    H   H  C     
  Y    HHHHH  C     
  Y    H   H  C     
  Y    H   H  C   C 
  Y    H   H   CCC  

Process finished with exit code 0
```
```java=
public class PrintResults {

	public static void main(String[] args) {
		
		System.out.println("The value of 1+1 is " + (1+1));
		int a = 10 + 5;
		System.out.println("The value of a is " + a);
		int b = 50 - 23;
		System.out.println("The value of b is " + b);
		int c = 12 * 13;
		System.out.println("The value of c is " + c);
		double d = 20.0 / 3.0;
		System.out.println("The value of d is " + d);
		int e = 100 % 7;
		System.out.println("The value of e is " + e);
		double f = Math.pow(4, 3);
		System.out.println("The value of f is " + f);
	}
}

```
```shell=
The value of 1+1 is 2
The value of a is 15
The value of b is 27
The value of c is 156
The value of d is 6.666666666666667
The value of e is 2
The value of f is 64.0

Process finished with exit code 0
```
## Part 2
![](https://s3-ap-northeast-1.amazonaws.com/g0v-hackmd-images/uploads/upload_4081aa55b651e842b354333f86af4d94.png)

```java=
import java.util.Scanner;

public class GetNameConsole {

	public static void main(String[] args) {
		System.out.print("Enter your name: ");
		Scanner in = new Scanner(System.in);
		String name = in.nextLine();
		System.out.println("Hello " + name + "!");
	}
}
```
```shell=
args is [Yi-Hsiang]
Hello Yi-Hsiang!

Process finished with exit code 0
```
```java=
public class GetNameArgument {
	
	public static void main(String[] args) {
		// This will print out the contents of the args array.
		// Don't worry about the specifics of how this works. We
		// will get to that next week
		System.out.println("args is " + java.util.Arrays.toString(args));
		// if there are command line arguments, then the first will be in
		// args[0], the second in arg[1], and so on. If there are no command
		// line arguments, then args[0] will give an error
		System.out.println("Hello " + args[0] + "!");
	}
}
```
```shell=
Enter your name: Jonathan
Hello Jonathan!

Process finished with exit code 0
```
## Part 3
```java=
class WireCapacitance {

	public static double calCapacitance(double distance, double absolutePermittivity, double wireLength, double wireRadius) {
		double numerator = Math.PI * absolutePermittivity * wireLength;
		double denominator = Math.log((distance / 2 * wireRadius) + Math.sqrt(Math.pow(distance, 2) / (4 * Math.pow(wireRadius, 2)) - 1));
		return numerator / denominator;
	}
    
	public static void main(String[] arguments) {
		double absolutePermittivity = 8.85E-12;
		double initialDistance = .01;
		double finalDistance = .005;
		double wireLength = 0.5;
		double wireRadius = .002053;
		double capacitanceDifference = 0;
		capacitanceDifference = calCapacitance(finalDistance, absolutePermittivity, wireLength, wireRadius)
				- calCapacitance(initialDistance, absolutePermittivity, wireLength, wireRadius);
		 System.out.println("The wires' change in capacity when moved from a distance of " +  initialDistance +
		" m to " + finalDistance + "m is " + capacitanceDifference + " farads");
	}
}
```
```shell=
The wires' change in capacity when moved from a distance of 0.01 m to 0.005m is -5.56154266740741E-11 farads

Process finished with exit code 0
```