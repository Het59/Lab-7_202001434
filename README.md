# IT-314 SOFTWARE ENGINEERING
### Student_ID: 202001434 
### Name: Het Patel
---

## Topic : black and white-box (or structural) testing

## **Section A:**
---
#### Consider a program for determining the previous date. Its input is triple of day, month and year with the following ranges 1 <= month <= 12, 1 <= day <= 31, 1900 <= year <= 2015.The possible output dates would be previous date or invalid date. Design the equivalence class test cases?
---
* Equivalence classes for this program:
  * For Day:
  
  | `Equivalence class` | `Range` | `Status` |
  | :---: | :---: | :---: |
  | E1    | Between 1 and 31 | Valid |
  | E2 | Less than 1 | Invalid |
  | E3 | Greater than 31 | Invalid |
  
  * For Month:
  
  | `Equivalence class` | `Range` | `Status` |
  | :---: | :---: | :---: |
  | E4 |    Between 1 and 12 | Valid |
  | E5 | Less than 1 | Invalid |
  | E6 |    Greater than 12 |    Invalid |
  
  * For Year:
  
   | `Equivalence class` | `Range` | `Status` |
   | :---: | :---: | :---: |
   | E7 |    Between 1900 and 2015 |    Valid | 
   | E8 | Less than 1900 | Invalid |
   | E9 | Greater than 2015 | Invalid |
   
 * Test-cases based on Equivalence Partition:
 
| `Input Data` | `Expected Output` |
| :---: | :---: |
|Valid Input: Day=3,Month=5,Year=2012|    02/05/2012|
|Invalid Input: Day=-1,Month=5,Year=2012|    Error Message|
|Invalid Input: Day=32,Month=5,Year=2012|    Error Message|
|Invalid Input: Day=3,Month=-1,Year=2012|    Error Message|
|Invalid Input: Day=3,Month=13,Year=2012|    Error Message|
|Invalid Input: Day=3,Month=5,Year=1898|    Error Message|
|Invalid Input: Day=3,Month=5,Year=2017|    Error Message|

* Test-cases based on Boundary Analysis:

| `Input Data` | `Expected Output` |
|:---:|:---:|
|01/01/1900|    31/12/1899|
|31/12/2015|    30/12/2015|
|29/2/1900|    Error Message|
|31/6/2010|    Error Message|
|28/2/1900|    27/2/1900|
|29/2/1904|    28/2/1904|

---
#### P1. The function linearSearch searches for a value v in an array of integers a. If v appears in the array a, then the function returns the first index i, such that a[i] == v; otherwise, -1 is returned.

Program 1 that we are testing : <br>
<br>
```
package tests;

public class allPrograms {
	
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
	
}
```
<br>

JUnit Testing for Program 1: 
<br>

```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P1_linearSearch_tests {

	@Test
	public void test1() {
		int arr[] = { 5, 4, 3, 6, 2 };
		
		allPrograms program = new allPrograms();
		int result = program.linearSearch(6, arr);
		
		System.out.println(result);
		assertEquals(3, result);
	}
	
	@Test
	public void test2() {
		int arr[] = { };
		
		allPrograms program = new allPrograms();
		int result = program.linearSearch(10, arr);
		
		System.out.println(result);
		assertEquals(-1, result);
	}
	
	@Test
	public void test3() {
		int arr[] = { 0 };
		
		allPrograms program = new allPrograms();
		int result = program.linearSearch(0, arr);
		
		System.out.println(result);
		assertEquals(0, result);
	}
	
	@Test
	public void test4() {
		int arr[] = { 10 };
		allPrograms program = new allPrograms();
		int result = program.linearSearch(7, arr);
		
		System.out.println(result);
		assertEquals(-1, result);
	}
	
	@Test
	public void test5() {
		int arr[] = { 5, 6, 3, 1, 8 };
		
		allPrograms program = new allPrograms();
		int result = program.linearSearch(7, arr);
		
		System.out.println(result);
		assertEquals(-1, result);
	}

}
```
 
![WhatsApp Image 2023-04-18 at 5 34 37 PM](https://user-images.githubusercontent.com/124347145/232777529-80d20cfc-991f-4074-80dc-07985c45afe1.jpeg)

**Equivalence Partitioning:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists</td>
      <td>the index of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v does not exist</td>
      <td>-1</td>
    </tr>
  </tbody>
</table>

**Boundary Value Analysis:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 0</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v exists</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v does not exist</td>
      <td>-1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the beginning of the array</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the end of the array</td>
      <td>the last index where v is found</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists in the middle of the array</td>
      <td>the index where v is found</td>
    </tr>
  </tbody>
</table>
</br>

---
#### P2. The function countItem returns the number of times a value v appears in an array of integers a.

```
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
```
JUnit Testing for Program 2: 
<br>

```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P2_countItem_tests {

	@Test
	public void test1() {
		int arr[] = {  };
		allPrograms program = new allPrograms();
		int result = program.countItem(8, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test2() {
		int arr[] = { 5, 15, 5, 30, 15 };
		allPrograms program = new allPrograms();
		int result = program.countItem(10, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test3() {
		int arr[] = { 7, 7, 20, 30, 7 };
		allPrograms program = new allPrograms();
		int result = program.countItem(7, arr);
		
		assertEquals(result, 3);
	}
	
	@Test
	public void test4() {
		int arr[] = { 10, 10, 5, 30, 10 };
		allPrograms program = new allPrograms();
		int result = program.countItem(5, arr);
		
		assertEquals(result, 1);
	}
	
	@Test
	public void test5() {
		int arr[] = { 0 };
		allPrograms program = new allPrograms();
		int result = program.countItem(0, arr);
		
		assertEquals(result, 1);
	}
	
	@Test
	public void test6() {
		int arr[] = { 10 };
		allPrograms program = new allPrograms();
		int result = program.countItem(50, arr);
		
		assertEquals(result, 0);
	}
	
	@Test
	public void test7() {
		int arr[] = { 1, 1, 2, 3, 1, 1, 1 };
		allPrograms program = new allPrograms();
		int result = program.countItem(1, arr);
		
		assertEquals(result, 5);
	}
}
	
```
<br>

![WhatsApp Image 2023-04-18 at 5 52 49 PM](https://user-images.githubusercontent.com/124347145/232777632-78534c0f-2650-417a-b6f0-1141175a73be.jpeg)

**Equivalence Partitioning:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists multiple times</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and a non-empty array a[] where v exists only once</td>
      <td>1</td>
    </tr>
  </tbody>
</table>

**Boundary Value Analysis:**

<table>
  <thead>
    <tr>
      <th>Tester Action and Input Data</th>
      <th>Expected Outcome</th>
    </tr>
  </thead>
  <tbody>
    <tr>
      <td>Test with v as a non-existent value and an empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as a non-existent value and a non-empty array a[]</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 0</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v exists</td>
      <td>1</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length 1, where v does not exist</td>
      <td>0</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the beginning of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists at the end of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
    <tr>
      <td>Test with v as an existent value and an array a[] of length greater than 1, where v exists in the middle of the array</td>
      <td>the number of occurrences of v in a[]</td>
    </tr>
  </tbody>
</table>
</br>
 
---
#### P3. The function binarySearch searches for a value v in an ordered array of integers a. If v appears in the array a, then the function returns an index i, such that a[i] == v; otherwise, -1 is returned.

```
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
   ```
JUnit Testing for Program 3:
<br>
   ```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P3_binarySearch_tests {

	@Test
	public void test1() {
		int arr[] = { 1,2,4,5,6 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(4, arr);
		
		assertEquals(2, result);
	}
	
	@Test
	public void test2() {
		int arr[] = { 1,2,3,4,5 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(1, arr);
		
		assertEquals(0, result);
	}
	
	@Test
	public void test3() {
		int arr[] = { 1,2,3,4,5 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(5, arr);
		
		assertEquals(4, result);
	}
	
	@Test
	public void test4() {
		int arr[] = { 1,2,3,4,5 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(8, arr);
		
		assertEquals(-1, result);
	}
	
	@Test
	public void test5() {
		int arr[] = { 1 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(1, arr);
		
		assertEquals(0, result);
	}
	
	@Test
	public void test6() {
		int arr[] = {  };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(1, arr);
		assertEquals(-1, result);
	}
				
	@Test
	public void test7() {
		int arr[] = { 1, 2, 3 };
		allPrograms program = new allPrograms();
		int result = program.binarySearch(3, arr);
			
		assertEquals(2, result);
	}

}

```
![WhatsApp Image 2023-04-18 at 6 12 43 PM](https://user-images.githubusercontent.com/124347145/232781450-2629fe8b-4458-4280-b326-80de4b50089e.jpeg)

**Equivalence Partitioning:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>v=4, a=[1 , 2 , 4 , 5 , 6]</td>
    <td>2</td>
  </tr>
  <tr>
    <td>v=1, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=5, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>4</td>
  </tr>
  <tr>
    <td>v=8, a=[1 , 2 , 3 , 4 , 5]</td>
    <td>-1</td>
  </tr>
  <tr>
    <td>v=1, a=[1]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=1, a=[]</td>
    <td>-1</td>
  </tr>
	<tr>
    <td>v=3, a=[1 , 2 , 3]</td>
    <td>2</td>
  </tr>
	
</table>

**Boundary Value Analysis:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>v=1, a=[1]</td>
    <td>0</td>
  </tr>
  <tr>
    <td>v=6, a=[]</td>
    <td>-1</td>
  </tr>
  <tr>
    <td>v=1, a=[1, 2, 3]</td>
    <td>0 (smallest element in the array)</td>
  </tr>
  <tr>
    <td>v=3, a=[1, 2, 3]</td>
    <td>2 (largest element in the array)</td>
  </tr>
</table>
</br>

---
#### P4. The following problem has been adapted from The Art of Software Testing, by G. Myers (1979). The function triangle takes three integer parameters that are interpreted as the lengths of the sides of a triangle. It returns whether the triangle is equilateral (three lengths equal), isosceles (two lengths equal), scalene (no lengths equal), or invalid (impossible lengths).

```
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
```
JUnit Testing for Program 4: 
<br>

```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P4_triangle_tests {

	@Test
	public void test1() {
		int a = 2, b = 2, c = 2;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 0);
	}
	@Test
	public void test2() {
		int a = 3, b = 3, c = 4;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test3() {
		int a = 6, b = 5, c = 4;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 2);
	}
	@Test
	public void test4() {
		int a = 0, b = 0, c = 0;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test5() {
		int a =-1, b =-1, c = 5;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test6() {
		int a = 2, b = 2, c = 1;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test7() {
		int a = 0, b = 1, c = 1;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test8() {
		int a = 1, b = 0, c = 1;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test9() {
		int a = 1, b = 1, c = 0;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test10() {
		int a = 1, b = 2, c = 3;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
	@Test
	public void test11() {
		int a = 3, b = 1, c = 3;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 1);
	}
	@Test
	public void test12() {
		int a = 5, b = 4, c = 2;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 2);
	}
	@Test
	public void test13() {
		int a = Integer.MAX_VALUE, b = Integer.MAX_VALUE, c = Integer.MAX_VALUE;
		allPrograms program = new allPrograms();
		int result = program.triangle(a, b, c);
		
		assertEquals(result, 3);
	}
}
``` 

![WhatsApp Image 2023-04-18 at 6 18 38 PM](https://user-images.githubusercontent.com/124347145/232782802-f9f91a9a-3911-4a4e-b55a-ce39ea3bc9fe.jpeg)

 **Equivalence Partitioning:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Valid input: a=2, b=2, c=2</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Valid input: a=3, b=3, c=4</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Valid input: a=6, b=5, c=4</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Invalid input: a=0, b=0, c=0</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=-1, b=-1, c=5</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Valid input: a=1, b=1, c=1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Valid input: a=2, b=2, c=1</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Valid input: a=3, b=4, c=5</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Invalid input: a=0, b=1, c=1</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=1, b=0, c=1</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid input: a=1, b=1, c=0</td>
    <td>3</td>
  </tr>
</table>
</br>

**Boundary Value Analysis:**
<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Invalid inputs: a = 0, b = 0, c = 0</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Invalid inputs: a + b = c or b + c = a or c + a = b (a=3, b=4, c=8)</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Equilateral triangles: a = b = c = 1</td>
    <td>0</td>
  </tr>
  <tr>
    <td>Isosceles triangles: a = b ≠ c = 10</td>
    <td>1</td>
  </tr>
  <tr>
    <td>Scalene triangles: a = b + c - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Scalene triangles: b = a + c - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Scalene triangles: c = a + b - 1</td>
    <td>2</td>
  </tr>
  <tr>
    <td>Maximum values: a, b, c = Integer.MAX_VALUE</td>
    <td>3</td>
  </tr>
  <tr>
    <td>Minimum values: a, b, c = Integer.MIN_VALUE</td>
    <td>3</td>
  </tr>
</table>
<br>

---
#### P5. The function prefix (String s1, String s2) returns whether or not the string s1 is a prefix of string s2 (you may assume that neither s1 nor s2 is null).

 ```
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
```

JUnit Testing for Program 5: 
<br>

```
package tests;

import static org.junit.Assert.*;

import org.junit.Test;

public class P5_prefix_tests {

	@Test
	public void test1() {
		String str1 = "good", str2 = "good morning";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test2() {
		String str1 = "a", str2 = "abc";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test3() {
		String str1 = "", str2 = "good morning";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test4() {
		String str1 = "morning", str2 = "good morning";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, false);
	}
	@Test
	public void test5() {
		String str1 = "soft", str2 = "software";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test6() {
		String str1 = "software", str2 = "soft";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, false);
	}
	@Test
	public void test7() {
		String str1 = "a", str2 = "ab";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test8() {
		String str1 = "software", str2 = "softwareee";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test9() {
		String str1 = "abc", str2 = "abc";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test10() {
		String str1 = "a", str2 = "b";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, false);
	}
	@Test
	public void test11() {
		String str1 = "a", str2 = "a";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
	@Test
	public void test12() {
		String str1 = "", str2 = "";
		
		allPrograms program = new allPrograms();
		boolean result = program.prefix(str1, str2);
		
		assertEquals(result, true);
	}
}
```
![WhatsApp Image 2023-04-18 at 6 28 43 PM](https://user-images.githubusercontent.com/124347145/232785153-aebe34ee-5fa3-4701-bab4-8738a9eabcbe.jpeg)

**Equivalence Partitioning:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>Valid Inputs: s1 = "good", s2 = "good morning"</td>
    <td>true</td>
  </tr>
  <tr>
    <td>Valid Inputs: s1 = "a", s2 = "abc"</td>
    <td>true</td>
  </tr>
  <tr>
    <td>Invalid Inputs: s1 = "", s2 = "good morning"</td>
    <td>false</td>
  </tr>
  <tr>
    <td>Invalid Inputs: s1 = "morning", s2 = "good morning"</td>
    <td>false</td>
  </tr>
</table>

<br>

**Boundary Value Analysis:**

<table>
  <tr>
    <th>Tester Action and Input Data</th>
    <th>Expected Outcome</th>
  </tr>
  <tr>
    <td>s1 = "", s2 = "software"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "soft", s2 = "software"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "software", s2 = "soft"</td>
    <td>False</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = "ab"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "software", s2 = "softwareefdfeee"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "abc", s2 = "abc"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = "b"</td>
    <td>False</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = "a"</td>
    <td>True</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = "b"</td>
    <td>False</td>
  </tr>
  <tr>
    <td>s1 = "a", s2 = " "</td>
    <td>False</td>
  </tr>

  <tr>
    <td>s1 = "", s2 = ""</td>
    <td>True</td>
  </tr>
</table>
</br>
<br>

---
#### P6: Consider again the triangle classification program (P4) with a slightly different specification: The program reads floating values from the standard input. The three values A, B, and C are interpreted as representing the lengths of the sides of a triangle. The program then prints a message to the standard output that states whether the triangle, if it can be formed, is scalene, isosceles, equilateral, or right angled. 

Determine the following for the above program:
* Identify the equivalence classes for the system
Equivalence Classes:<br>
EC1: Invalid inputs (negative or zero values)<br>
EC2: Non-triangle (sum of the two shorter sides is not greater than the longest side)<br>
EC3: Scalene triangle (no sides are equal)<br>
EC4: Isosceles triangle (two sides are equal)<br>
EC5: Equilateral triangle (all sides are equal)<br>
EC6: Right-angled triangle (satisfies the Pythagorean theorem)<br>

* Identify test cases to cover the identified equivalence classes. Also, explicitly mention which test case would cover which equivalence class. (Hint: you must need  to be ensure that the identified set of test cases cover all identified equivalence classes)
Test cases:<br>
TC1: -1, 0 <br>
TC2: 1, 2, 5<br>
TC3: 3, 4, 5<br>
TC4: 5, 5, 7<br>
TC5: 6, 6, 6<br>
TC6: 3, 4, 5<br>

Test case 1 covers class 1, test case 2 covers class 2, test case 3 covers class 3, test case 4 covers class 4, test case 5 covers class 5, and test case 6 covers class 6

* For the boundary condition A + B > C case (scalene triangle), identify test cases to verify the boundary.<br>
2, 3, 6<br>
3, 4, 8<br>
Both test cases have two sides that are shorter than the third side, and should not form a triangle
<br>

* For the boundary condition A = C case (isosceles triangle), identify test cases to verify the boundary.<br>
1, 2, 1<br>
0, 2, 0<br>
5, 6, 5<br>
Both test cases have two sides that are equal, but only test case 2 should form an isosceles triangle, other input are invalid.
<br>

* For the boundary condition A = B = C case (equilateral triangle), identify test cases to verify the boundary.<br>
5, 5, 5<br>
0, 0, 0<br>
Both test cases have all sides equal, but only test case 1 should form an equilateral triangle, other input are invalid.

<br>

* For the boundary condition A2 + B2 = C2 case (right-angle triangle), identify test cases to verify the boundary.<br>
3, 4, 5<br>
0, 0, 0<br>
-3, -4, -5<br>
Both test cases satisfy the Pythagorean theorem, but only test case 1 should form right-angled triangle, other input are invalid
triangle.

<br>

* For the non-triangle case, identify test cases to explore the boundary.<br>
Test cases for the non-triangle case:<br>
TC11 (EC3): A=2, B=2, C=4 (sum of A and B is less than C)<br>

<br>

* For non-positive input, identify test points.<br>
Test points for non-positive input:<br>
TP1 (EC2): A=0, B=4, C=5 (invalid input)<br>
TP2 (EC2): A=-2, B=4, C=5 (invalid input)<br>
Note: Test cases TC1 to TC10 covers all identified equivalence classes.<br>
<br>

---
 ## **Section B**
  
#### The code below is part of a method in the ConvexHull class in the VMAP system. The following is a small fragment of a method in the ConvexHull class. For the purposes of this exercise you do not need to know the intended function of the method. The parameter p is a Vector of Point objects, p.size() is the size of the vector p, (p.get(i)).x is the x component of the ith point appearing in p, similarly for (p.get(i)).y. This exercise is concerned with structural testing of code and so the focus is on creating test sets that satisfy some particular coverage criterion.

1. Convert the Java code comprising the beginning of the doGraham method into a control flow graph(CFG).
    
    ![l](https://user-images.githubusercontent.com/124347145/232831029-453aeae4-eaf8-4ffb-8fcf-31fade881ea7.jpg)


2. Construct test sets for your flow graph that are adequate for the following criteria:<br>
a. Statement Coverage.<br>
b. Branch Coverage.<br>
c. Basic Condition Coverage.<br>

a. Statement Coverage:
    
| `Test Case` | `Condition` |
| --------- | ------ | 
| 1 | p is an empty vectorr |
| 2 | p is a vector with one point | 
| 3 | p is a vector with two points having same y componente | 
| 4 | p is a vector with two points having different y components | 
| 5 | p is a vector with three or more different points with different points with same y components |  
| 6 | P is a vector with three or more different points with different points with different y components|

b. Branch Coverage:
    
| `Test Case` | `Condition` |
| --------- | ------ | 
| 1 | p is an empty vectorr |
| 2 | p is a vector with one point | 
| 3 | p is a vector with two points having same y componente | 
| 4 | p is a vector with two points having different y components | 
| 5 | p is a vector with three or more different points with different points with same y components and with same x components |  
| 6 | p is a vector with three or more different points with different points with different y components and with same x components|
| 7 | P is a vector with three or more points with the same x and y components |

c. Basic condition Coverage:
    
| `Test Case` | `Condition` |
| --------- | ------ | 
| 1 | p is an empty vectorr |
| 2 | p is a vector with one point | 
| 3 | p is a vector with two points having same y componente | 
| 4 | p is a vector with two points having different y components | 
| 5 | p is a vector with three or more different points with different points with same y components and with same x components |  
| 6 | p is a vector with three or more different points with different points with different y components and with same x components|
| 7 | P is a vector with three or more points with the same x and y components |
