# Lab-7_202001180

# **Section A**

Consider a program for determining the previous date. Its input is triple of day, month and year with the
following ranges 1 <= month <= 12, 1 <= day <= 31, 1900 <= year <= 2015.The possible output dates would be
previous date or invalid date. Design the equivalence class test cases?<br>

    EQC1: 
    Valid dates (1, 1, 1900) to (31, 12, 2015) such that day, month and year are in the given ranges. 
    ex: (20, 11, 2002), (5, 7, 2019)  
    
    EQC2: 
    Invalid dates (1, 1, 1900) to (31, 12, 2015) such that day, month and year are in the given ranges but the input is invalid. 
    ex: (29, 2, 2011), (31, 6, 2010)   
    
    EQC3: 
    Invalid range (1, 1, 1900) to (31, 12, 2015) such that day, month and year are not in the given ranges. 
    ex: (30, 2, 2022), (32,14,2003)
    
    EQC4: 
    Invalid input (1, 1, 1900) to (31, 12, 2015) such that day, month and year are in the given ranges but the input is invalid. 
    ex: (2.2, 2, 2022), (2, b, 2010)  
 

**Tester Action and Input Data Expected Outcome**<br>

<br>
Valid dates:<br>
    <br>

    Test Case 1: 
        Input: (11,09,2010) 
        Output: (10,09,2010)
    Test Case 2: 
        Input: (1,1,2000) 
        Output: (31,12,1999)

<br>


Invalid dates:<br>
    <br>

    Test Case 1: 
        Input: (30,2,2012) 
        Output: Invalid date
    Test Case 2: 
        Input: (31,4,2010) 
        Output: Invalid date

Invalid range:<br>
    <br>

    Test Case 1: 
        Input: (32,22,2022) 
        Output: Invalid date
    Test Case 2: 
        Input: (33,11,2003) 
        Output: Invalid date

## **Boundary Value Analysis:**<br>

    Test Case 1: 
        Input: (1,1,1900) Valid First possible date 
        Output: (31,12,1899) Not in range
    Test Case 2: 
        Input: (31,12,2015) Valid Last possible date 
        Output: (30,12,2015) 
    Test Case 3: 
        Input: (31,1,1899) One day before first possible date 
        Output: Invalid input 
    Test Case 4: 
        Input: (1,1,2016) One day after last possible date 
        Output: Invalid input 
    Test Case 5: 
        Input: (29,2,2000) Valid leap year date 
        Output: (28,2,2000) 
    Test Case 6: 
        Input: (29,2,1900) Invalid leap year date 
        Output: Invalid input 
    Test Case 7: 
        Input: (1,3,2000) Valid date after leap year date 
        Output: (29,2,2000) 
    Test Case 8: 
        Input: (1,3,2019) Valid date after non leap year date 
        Output: (28,2,2019) 
    Test Case 9: 
        Input: (1,1,2000) Valid first day of month 
        Output: (31,12,1999) 
    Test Case 10: 
        Input: (1,1,2000) Valid first day of year 
        Output: (31,12,1999) 
    

Based on these boundary test cases, we can design the following test cases:<br>
<!-- table with 2 column Tester Action and Input Data Expected Outcome -->
<br>

<h4> Equivalence Class Testing

<br>

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| Valid partition              |                  |
| (1,1,1900)                   | (31,12,1899)     |
| (31,12,2015)                 | (30,12,2015)     |
| Invalid partition            |                  |
| (32,2,2022)                  | Invalid date     |
| (13,14,2003)                 | Invalid date     |
| (20,11,2020)                 | Invalid date     |
| (31,4,2010)                  | Invalid date     |
| (2.2, 2, 2022)               | Invalid input    |
| (a, 4, 2010)                 | Invalid input    |
| (31,1,1899)                  | Invalid input    |


<h4> Boundary Value Analysis

<br>

| Tester Action and Input Data | Expected Outcome |
|------------------------------|------------------|
| (1,1,1900)                   | (31,12,1899)     |
| (31,12,2015)                 | (30,12,2015)     |
| (31,1,1899)                  | Invalid input    |
| (1,1,2016)                   | Invalid input    |
| (29,2,2000)                  | (28,2,2000)      |
| (29,2,1900)                  | Invalid input    |
| (1,3,2000)                   | (29,2,2000)      |
| (1,3,2019)                   | (28,2,2019)      |
| (1,3,2000)                   | (31,12,1999)     |


2. Modify your programs such that it runs on eclipse IDE, and then execute your test suites on the
program. While executing your input data in a program, check whether the identified expected
outcome (mentioned by you) is correct or not.

<!-- write java code -->
    
        import java.util.Scanner;
        
        public class Date {
        
        	public static void main(String[] args) {
        		Scanner sc = new Scanner(System.in);
        		System.out.println("Enter the date in dd mm yyyy format");
        		int day = sc.nextInt();
        		int month = sc.nextInt();
        		int year = sc.nextInt();
        		Date date = new Date();
        		date.setDate(day, month, year);
        		date.printDate();
        		date.previousDate();
        		date.printDate();
        	}
        
        	private int day;
        	private int month;
        	private int year;
        
        	public void setDate(int day, int month, int year) {
        		this.day = day;
        		this.month = month;
        		this.year = year;
        	}
        
        	public void printDate() {
        		System.out.println("Date is " + day + "/" + month + "/" + year);
        	}
        
        	public void previousDate() {
        		if (day == 1) {
        			if (month == 1) {
        				day = 31;
        				month = 12;
        				year--;
        			} else if (month == 3) {
        				if (year % 4 == 0) {
        					day = 29;
        					month--;
        				} else {
        					day = 28;
        					month--;
        				}
        			} else if (month == 5 || month == 7 || month == 10 || month == 12) {
        				day = 30;
        				month--;
        			} else {
        				day = 31;
        				month--;
        			}
        		} else {
        			day--;
        		}
        	}
        }



## P1

#### Linear search program
The function linearSearch searches for a value v in an array of integers a. If v appears in the array  a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.  

    int linearSearch(int v, int a[])  
    {  
        int i = 0;  
            while (i < a.length)  
            {  
                if (a[i] == v)  
                    return(i);  
                i++;  
            }  
        return (-1);  
    }  
<br>

Test File

```java
import static org.junit.Assert.assertEquals;
    import org.junit.Test;
    
    public class LinearSearchTest {
    
    	@Test
    	public void testLinearSearch() {
    		int[] a = {-3, 4, -1, 1, 0 ,13 ,5};
    		int v = 1;
    		int expected = 3;
    		int actual = LinearSearch.linearSearch(v, a);
    		assertEquals(expected, actual);
    	}
    }
```

**Equivalence Partitioning:**

| Tester Action and Input Data | Value to be found | Expected Outcome |
|------------------------------|-------------------|------------------|
| Valid partition              |                   |                  |
| [-3, 4, -1, 1, 0, 13, 5]              | 1              | 3                |
| [1, 2, 3, 4, 5]          | 1                 | 0                |
| Invalid partition            |                   |                  |
| [2, 4, 6, 8]   <br> (v is not present in a)              | 5                 | -1     

<br>

**Boundary Value Analysis:**

| Tester Action and Input Data | Value to be found | Expected Outcome |
|------------------------------|-------------------|------------------|
| Empty array a        | any         |0|
| [5, 10, 15, 20, 25]    <br> (v is at first position in a)         | 5                 | 0                |
| [5, 10, 15, 20, 25] <br> (v is at last position in a)         | 25                | 4                |
|  <h6> Invalid input partition     |                   |                  |
| v is a non-integer            | 2.2           | Invalid input    |
| v is a non-number            | a           | Invalid input    |


## P2:
The function countItem returns the number of times a value v appears in an array of integers a.<br>

    int countItem(int v, int a[])
    {
        int count = 0;
        for (int i = 0; i < a.length; i++)
            {
                if (a[i] == v)
                    count++;
            }
        return (count);
    }
<br>

Test File

    import static org.junit.Assert.assertEquals;
    import org.junit.Test;
    
    public class CountItemTest {
    
    	@Test
    	public void testCountItem() {
    		int[] a = {1, 2, 1, 4, 5};
    		int v = 1;
    		int expected = 2;
    		int actual = CountItem.countItem(v, a);
    		assertEquals(expected, actual);

            assertEquals(2, obj.countItem(1, arr1));
            assertEquals(0, obj.countItem(6, arr1));
            assertEquals(0, obj.countItem(0, arr1));
    
    	}
    }

**Equivalence Partitioning:**

| Tester Action and Input Data | element to Count | Expected Outcome |
|------------------------------|-------------------|------------------|
| Valid partition           |                   |                  |
| [1, 2, 1, 4, 5]              | 1                 | 2                |
| Invalid partition          |                   |                  |
| [1, 2, 1, 4, 5] <br>(v is not present in a)        | 6         |0|    

<br>

**Boundary Value Analysis:**

| Tester Action and Input Data | element to Count | Expected Outcome |
|------------------------------|-------------------|------------------|
| Empty array a        | any         |0|
| [1, 2, 1, 4, 5]  <br>(v is present 1 time in array )        | 2        |1|
| [1, 1, 1, 1, 1] <br>(v is present at every index of a )               |1|5|
| [5, 10, 15, 20, 25] <br>(v is present at the first index of a)        | 5                 | 1                |
| [5, 10, 15, 20, 25]   <br> (v is present at the last index of a )      | 25                | 1               |
| [1, 2, 3, 4, 5] v is present at the first index of a         | 1 |1|        |
|[1, 2, 1, 4, 5]  v is present at the last index of a        | 5        |1|

## P3:
The function binarySearch searches for a value v in an ordered array of integers a. If v appears in
the array a, then the function returns an index i, such that a[i] == v; otherwise, -1 is returned.<br>

Assumption: the elements in the array a are sorted in non-decreasing order.<br>

    int binarySearch(int v, int a[])
    {
        int lo,mid,hi;
        lo = 0;
        hi = a.length-1;
        while (lo <= hi)
        {
            mid = (lo+hi)/2;
            if (v == a[mid])
                return (mid);
            else if (v < a[mid])
                hi = mid-1;
            else
                lo = mid+1;
        }
        return(-1);
    }
<br>

Test File

    import static org.junit.Assert.assertEquals;
    import org.junit.Test;
    
    public class BinarySearchTest {
    
    	@Test
    	public void testBinarySearch() {
    		int[] a = {1, 2, 3, 4, 5};
    		int v = 3;
    		int expected = 2;
    		int actual = BinarySearch.binarySearch(v, a);
    		assertEquals(expected, actual);

            assertEquals(0, obj.binarySearch(2, arr1));
            assertEquals(1, obj.binarySearch(4, arr1));
            assertEquals(-1, obj.binarySearch(6, arr1));
            assertEquals(-1, obj.binarySearch(0, arr1));
    
    	}
    }

**Equivalence Partitioning:**

| Tester Action and Input Data | element to Count | Expected Outcome |
|------------------------------|-------------------|------------------|
| Valid partition           |                   |                  |
| [1, 2, 3, 4, 5]              | 3                 | 2                |
| [5, 10, 15, 20, 25]          | 5                 | 0   
| Invalid partition          |                   |                  |
| [2, 4, 6, 8]                 | 5                 | -1               |
| [1, 3, 5, 7]                 | 4                 | -1     

<br>

**Boundary Value Analysis:**

| Tester Action and Input Data | element to Count | Expected Outcome | 
|------------------------------|-------------------|------------------| 
| empty array a          | any                 | 0              
| [1, 1, 2 ,2 ,3] <br>(v is present at more than 1 index of a )               |1|5| |         
| [5, 10, 15, 20, 25]<br> (v is present at the first index of a)         | 5                 | 0              |
| [5, 10, 15, 20, 25] <br>(v is present at the last index of a)         | 25           | 4 |           
| <h6>Invalid input    |              
| [2, 4, 6, 2]<br>(not in sorted order) | any   | Invalid input    |   
| [2, 4, 6, 8]<br>(non integer)   | 2.2               | Invalid input    |  
| [2, 4, 6, 8]  <br> (non-number  )        | a                 | Invalid input    | 


<br>

## P4:
The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). The
function triangle takes three integer parameters that are interpreted as the lengths of the sides of a
triangle. It returns whether the triangle is equilateral (three lengths equal), isosceles (two lengths equal),
scalene (no lengths equal), or invalid (impossible lengths).<br>


    final int EQUILATERAL = 0;
    final int ISOSCELES = 1;
    final int SCALENE = 2;
    final int INVALID = 3;
    int triangle(int a, int b, int c)
    {
        if (a >= b+c || b >= a+c || c >= a+b)
            return(INVALID);
        if (a == b && b == c)
            return(EQUILATERAL);
        if (a == b || a == c || b == c)
            return(ISOSCELES);
            
        return(SCALENE);
    }
<br>

Test File

    import static org.junit.Assert.assertEquals;
    import org.junit.Test;
    
    public class TriangleTest {
    
    	@Test
    	public void testTriangle() {
    		int a = 5;
    		int b = 5;
    		int c = 5;
    		int expected = 0;
    		int actual = Triangle.triangle(a, b, c);
    		assertEquals(expected, actual);
    
    		a = 5;
    		b = 5;
    		c = 6;
    		expected = 1;
    		actual = Triangle.triangle(a, b, c);
    		assertEquals(expected, actual);
    
    		a = 4;
    		b = 5;
    		c = 6;
    		expected = 2;
    		actual = Triangle.triangle(a, b, c);
    		assertEquals(expected, actual);
    
    		a = 4;
    		b = 5;
    		c = 11;
    		expected = 3;
    		actual = Triangle.triangle(a, b, c);
    		assertEquals(expected, actual);
    
    		a = 0;
    		b = 5;
    		c = 6;
    		expected = 3;
    		actual = Triangle.triangle(a, b, c);
    		assertEquals(expected, actual);
    	}
    }

**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      | 
| ------------- | :---: | 
| Valid equilateral triangle (a=b=c) <br> a=5, b=5, c=5        | EQUILATERAL         | 
| Valid isosceles triangle (a=b<c)   <br> a=5, b=5, c=6      | ISOSCELES         | 
| Valid scalene triangle (a<b<c)   <br> a=4, b=5, c=6      | SCALENE        | 
| Invalid partition          |                   |                  |
| Invalid triangle (a+b<=c) <br> a=4, b=5, c=11         | INVALID       |  
| Invalid triangle (a=0 or b=0 or c=0)  <br> a=0, b=5, c=6      | INVALID         | 
 

<br>

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      | 
| ------------- | :---: | 
| Invalid triangle (a+b<=c)  <br> a=4, b=5, c=11        | INVALID         | 
| Invalid triangle (a+c<=b)    <br> a=4, b=11, c=4       | INVALID         | 
| Invalid triangle (b+c<=a)   <br> a=14, b=5, c=1       | INVALID         | 
| Valid equilateral triangle (a=b=c) <br> a=1, b=1, c=1          | EQUILATERAL         | 
| Valid isosceles triangle (a=b<c)   <br> a=4, b=4, c=6       | ISOSCELES         | 
| Valid isosceles triangle (a=c<b)    <br> a=4, b=5, c=4    | ISOSCELES         | 
| Valid isosceles triangle (b=c<a)  <br> a=8, b=6, c=6      | ISOSCELES         | 
| Valid scalene triangle (a<b<c) <br> a=2, b=3, c=4        | SCALENE         | 

<br>

## P5:
The function prefix (String s1, String s2) returns whether or not the string s1 is a prefix
of string s2 (you may assume that neither s1 nor s2 is null).<br>

    public static boolean prefix(String s1, String s2)
    {
        if (s1.length() > s2.length())
        {
            return false;
        }
        for (int i = 0; i < s1.length(); i++)
        {
            if (s1.charAt(i) != s2.charAt(i))
            {
            return false;
            }
        }
        return true;
    }
<br>

Test File

    import static org.junit.Assert.assertEquals;
    import org.junit.Test;

    public class PrefixTest {

    	@Test
    	public void testPrefix() {
    		String s1 = "";
    		String s2 = "";
    		boolean expected = true;
    		boolean actual = Prefix.prefix(s1, s2);
    		assertEquals(expected, actual);

    		s1 = "";
    		s2 = "hello";
    		expected = true;
    		actual = Prefix.prefix(s1, s2);
    		assertEquals(expected, actual);

    		s1 = "hello";
    		s2 = "helloall";
    		expected = true;
    		actual = Prefix.prefix(s1, s2);
    		assertEquals(expected, actual);

    		s1 = "hello";
    		s2 = "hiall";
    		expected = false;
    		actual = Prefix.prefix(s1, s2);
    		assertEquals(expected, actual);

    		s1 = "hello";
    		s2 = "hello";
    		expected = true;
    		actual = Prefix.prefix(s1, s2);
    		assertEquals(expected, actual);

**Equivalence Partitioning:**

| Tester Action and Input Data     | Expected Outcome      | 
| ------------- | :---: | 
| Empty string s1 and s2   <br> s1="" , s2=""     | True         | 
| Empty string s1 and non-empty s2   <br> s1="" , s2="hello"       | True         | 
| s1 is null <br> s1=NULL , s2="helloall" |NullPointerException         |
| s2 is null <br> s1="helloall" , s2=NULL |NullPointerException         |
| Non-empty s1 is a prefix of non-empty s2 <br> s1="hello" , s2="helloall"        | True         | 
| Non-empty s1 is not a prefix of s2  <br> s1="hello" , s2="hiall"        | False         | 
| Non-empty s1 is longer than s2   <br> s1="hello" , s2="hel"       | False         | 


<br>

**Boundary Value Analysis:**

| Tester Action and Input Data     | Expected Outcome      | 
| ------------- | :---: | 
| Empty string s1 and s2     <br> s1="" , s2=""     | True         | 
|  string s1 and s2  of single length <br> s1="a" , s2="a"      | True         | 
| Empty string s1 and non-empty s2  <br> s1="" , s2="hello"        | True         | 
|same string s1 and s2  of highest possible length <br> s1="a.." , s2="a.."          | True         | 
| Non-empty s1 is longer than s2 <br> s1="hello" , s2="hel"          | False         | 


<br>

## P6:
Consider again the triangle classification program (P4) with a slightly different specification: The program
reads floating values from the standard input. The three values A, B, and C are interpreted as
representing the lengths of the sides of a triangle. The program then prints a message to the standard output
that states whether the triangle, if it can be formed, is scalene, isosceles, equilateral, or right angled.
Determine the following for the above program:
<br>

a) Identify the equivalence classes for the system<br>

    Test case 1:  All sides are positive, real numbers.
    Test case 2:  Any side is negative or zero.
    Test case 3:  Summation rule is not satisfied.
    Test case 4:  Summation rule is satisfied.
<br>
b) Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case
would cover which equivalence class.<br>(Hint: you must need to be ensure that the identified set of test cases cover all identified equivalence
classes)

<br>

    Test case 1 : A=5, B=5, C=5 (equilateral triangle)
    Test case 2 : A=5, B=5, C=7 (isosceles triangle)
    Test case 3 : A=5, B=6, C=7 (scalene triangle)
    Test case 4 : A=5, B=6, C=0 (invalid input)
    Test case 5 : A=5, B=6, C=-1 (invalid input)
    Test case 6 : A=5, B=6, C=11 (invalid input)



c) For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the
boundary.<br>

    Test case 1 : A=5, B=6, C=10 (c=a+b-1) (valid scalene triangle)
    Test case 2 : A=5, B=6, C=11 (c=a+b) (invalid input)
    Test case 3 : A=5, B=6, C=12 (c=a+b+1) (invalid input)

<br>

d) For the boundary condition A = C 
case (isosceles triangle), identify test cases to verify the
boundary.<br>

    Test case 1 : A=5, B=6, C=5 (c=a) (valid isosceles triangle)
    Test case 2 : A=5, B=11, C=5 (c=a) (invlid input as b>a+c)
    Test case 3 : A=5, B=5, C=5 (c=a) (equilateral triangle)

<br>
e) For the boundary condition A = B = C 
case (equilateral triangle), identify test cases to verify the
boundary.<br>
<br>

    Test case 1 : A=5, B=5, C=5 (valid equilateral triangle)

f) For the boundary condition  A^2 + B^2 = C^2
case (right-angle triangle), identify test cases to verify
the boundary.<br>
<br>
    
    test case 1 : A=3, B=4, C=5 (valid right-angle triangle)
    Test case 2 : A=IntMax, B=IntMax, C=IntMax (overflow error)


g) For the non-triangle case, identify test cases to explore the boundary.<br>
<br>

    Test case 1 : A=5, B=6, C=11 (invalid input as a+b=c)
    Test case 2 : A=5, B=6, C=12 (invalid input as a+b+1=c)

h) For non-positive input, identify test points.
<br>

    Test case 1 : A=0, B=6, C=11 (invalid input as a=0)
    Test case 2 : A=-5, B=6, C=11 (invalid input as a<0)





# **Section B**

The code below is part of a method in the ConvexHull class in the VMAP system. The following is a small fragment of a method in the ConvexHull class. For the purposes of this exercise you do not need to know the intended function of the method. The parameter p is a Vector of Point objects, p.size() is the size of the vector p, (p.get(i)).x is the x component of the i th point appearing in p, similarly for (p.get(i)).y. This exercise is concerned with structural testing of code and so the focus is on creating test sets that satisfy some particular coverage criterion.
<br>

Vector doGraham (Vector p) { 
    int i,j,min,M;
    Point t;
    min = 0;
    
    // search for minimum:
    for(i=1; i < p.size(); ++i) 
    {
        if( ((Point) p.get(i)).y<((Point) p.get(min)).y)
        {
            min = i;
        }
    }

    // continue along the values with same y component 
    
    for(i=0; i<p.size(); ++i) 
    {
        if((((Point) p.get(i)).y == ((Point) p.get(min)). y ) 
            &&   
        (((Point) p.get(i)).x > ((Point) p.get(min)).x ))
        {
            mini;
        }
    }
}

<br>
1. Convert the Java code comprising the beginning of the doGraham method into a control flow graph
(CFG).
<br>
<br>

```
        +-----+
        | i = 1|
        +-----+
           |
           |
           v
+---------------+
| i < p.size()   |
+---------------+
     | true
     |
     v
+-----------------------+
| ((Point)p.get(i)).y < ((Point)p.get(min)).y |
+-----------------------+
    | true        | false
    |             |
    v             v
+---------------+    +---------------+
| min = i       |    | i++           |
+---------------+    +---------------+
     |                   |
     |                   |
     v                   v
+---------------+    +---------------+
| i < p.size()   |    | return doStack(p) |
+---------------+    +---------------+
     | false             |
     |                   |
     v                   v
+------------------------+
| ((Point)p.get(i)).y == ((Point)p.get(min)).y |
+------------------------+
        | true           | false
        |                |
        v                v
+------------------------+  +---------------+
| ((Point)p.get(i)).x > ((Point)p.get(min)).x|
+------------------------+  +---------------+
        | true           | false
        |                |
        v                v
+---------------+    +---------------+
| min = i       |    | i++           |
+---------------+    +---------------+
        |                |
        |                |
        v                v
+---------------+    +---------------+
| i < p.size()   |    | return doStack(p) |
+---------------+    +---------------+
        | false            |
        |                  |
        v                  v
+--------------------------+
| return doStack(p)         |
+--------------------------+
```
2. Construct test sets for your flow graph that are adequate for the following criteria:
a. Statement Coverage.
To achieve statement coverage, we need to make sure that every statement in the code is executed at least once.
<br>

        Test 1: p = empty vector
        Test 2: p = vector with one point
        Test 3: p = vector with two points with the same y component
        Test 4: p = vector with two points with different y components
        Test 5: p = vector with three or more points with different y components
        Test 6: p = vector with three or more points with the same y component

<br>
b. Branch Coverage.
To achieve branch coverage, we need to make sure that every possible branch in the code is taken at least once
<br>

        Test 1: p = empty vector
        Test 2: p = vector with one point
        Test 3: p = vector with two points with the same y component
        Test 4: p = vector with two points with different y components
        Test 5: p = vector with three or more points with different y components, and none of them have the same x component
        Test 6: p = vector with three or more points with the same y component, and some of them have the same x component
        Test 7: p = vector with three or more points with the same y component, and all of them have the same x component

c. Basic Condition Coverage.
To achieve basic condition coverage, we need to make sure that every basic condition in the code (i.e., every Boolean subexpression) is evaluated as both true and false at least once
<br>

        Test 1: p = empty vector
        Test 2: p = vector with one point
        Test 3: p = vector with two points with the same y component
        Test 4: p = vector with two points with different y components
        Test 5: p = vector with three or more points with different y components, and none of them have the same x component
        Test 6: p = vector with three or more points with the same y component, and some of them have the same x component
        Test 7: p = vector with three or more points with the same y component, and all of them have the same x component
        Test 8: p = vector with three or more points with the same y component, and some of them have the same x component, and the first point has a smaller x component
<br>
