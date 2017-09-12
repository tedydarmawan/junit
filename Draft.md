# Introduction to Unit Testing
## What is Unit Testing?
Testing untuk spesifik method pada suatu kelas
class Class1{
  method1
  method2
  method3
  method4
  ...
}

## What is JUnit?
JUnit merupakan framework yang digunakan untuk melakukan unit testing pada program Java.
- square(3) == 8
- square(12) == 144

JUnit Test merupakan Automated Test
JUnit dapat dijalankan pada Continuous Integration

Testing setelah deployment disebut system testing

# First Junit Project - Green Bar
Buat projek baru
- File > New > Java Project
  - Projec name: junit-example
  - Finish
Buat kelas baru MyMath.java
``` java
package com.example.junit;

public class MyMath {
	
	int sum(int[] numbers) {
		int sum = 0;
		for(int i : numbers) {
			sum += i;
		}
		return sum;
	}	
}
```

Untuk melakukan unit testing sebaiknya dilakukan di source folder yang berbeda dengan main folder
Buat src folder baru dengan nama test
Klik kanan projek > New > Source Folder
- Folder name: test
- Finish

Buat JUnit Test Case
Klik kanan source folder test > New > Junit Test Case
- Package: MyMathTest
- Name: MyMathTest.java
- Finish
- Secara otomatis, "Add Junit 4 Library to the build path"
- Ok
``` java
package com.example.junit;

import static org.junit.Assert.*;

import org.junit.Test;

public class MyMathTest {

	@Test
	public void test() {
		fail("Not yet implemented");
	}

}
```

# First Unit Test with Junit
``` java
package com.example.junit;

import static org.junit.Assert.*;

import org.junit.Test;

public class MyMathTest {
	MyMath myMath = new MyMath();
	
	@Test
	public void sum_with3numbers() {
		assertEquals(6, myMath.sum(new int[] {1,2,3}));
	}
	
	@Test
	public void sum_with1numbers() {
		assertEquals(3, myMath.sum(new int[] {3}));
	}

}
```

# Assert Methods
Buat Junit Test Case Baru dengan nama AssertTest.java
``` java
package com.example.junit;

import static org.junit.Assert.*;

import org.junit.Test;

public class AssertTest {

	@Test
	public void test() {
//		boolean b = true;
//		assertEquals(true, b);
//		assertTrue(b);
//		assertFalse(b);
//		assertNotNull(null);
//		assertNull(null);
//		assertArrayEquals(new int[] {1,2}, new int[] {1});
	}

}
```

# @Before, @After, @BeforeClass
``` java
package com.example.junit;

import static org.junit.Assert.*;

import org.junit.After;
import org.junit.AfterClass;
import org.junit.Before;
import org.junit.BeforeClass;
import org.junit.Test;

public class MyMathTest {
	MyMath myMath = new MyMath();
	
	@Before
	public void before() {
		System.out.println("Before");
	}
	
	@After
	public void after() {
		System.out.println("After");
	}
	
	@BeforeClass
	public static void beforeClass() {
		System.out.println("Before Class");
	}
	
	@AfterClass
	public static void afterClass() {
		System.out.println("After Class");
	}
	
	@Test
	public void sum_with3numbers() {
		System.out.println("Test1");
		assertEquals(6, myMath.sum(new int[] {1,2,3}));
	}
	
	@Test
	public void sum_with1numbers() {
		System.out.println("Test2");
		assertEquals(3, myMath.sum(new int[] {3}));
	}

}
```
