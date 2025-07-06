## QUESTION THREE

```java
package enrollment;

public class Course {
	private String name;
	private String code;
	
	public Course(String name, String code) {
		try {
			setName(name);
			setCode(code);
		} catch (Exception error) {
			String message = error.getMessage();
			System.out.println("Course error: " + message);
		}
	}
	
	public void setName(String name) throws Exception{
		if(name.length() > 0) {
			this.name = name;
		}else {
			throw new Exception("Name is empty");
		}
	}
	
	public void setCode(String code) throws Exception{
		if(code.length() == 7) {
			this.code = code;
		}else {
			throw new Exception("Invalid course code");
		}
	}
	
	public String getName() {
		return name;
	}
	
	public String getCode() {
		return code;
	}
}
```

```java
package enrollment;

public abstract class Person {
	private String name;
	private int age;
	private String idNumber;
	
	public Person(String name, int age, String idNumber) {
		try {
			setName(name);
			setAge(age);
			setIdNumber(idNumber);
		} catch (Exception error) {
			String message  = error.getMessage();
			System.out.println("Error: " + message);
		}
	}
	
	
	public String getName() {
		return name;
	}
	
	public int getAge() {
		return age;
	}
	
	public String getIdNumber() {
		return idNumber;
	}
	
	public void setName(String name) throws Exception {
		if(name.length() > 1) {
			this.name = name;
		}else {
			throw new Exception("Name is too short.");
		}
	}
	
	public void setAge(int age) throws Exception{
		if(age > 0) {
			this.age = age;
		}else {
			throw new Exception("Age must be possitve.");
		}
	}
	
	public void setIdNumber(String idNumber) throws Exception {
		if(idNumber.length() == 13) {
			this.idNumber = idNumber;	
		}else {
			throw new Exception("ID Number must be 13 digits.");
		}
	}

	abstract void displayInfo();
}
```

```java
package enrollment;

import java.util.ArrayList;
 //  i     =    0        1      2
 // course =  ["C++", "JAVA", "Dart"]
 // Size = 3

public class Student extends Person{
	private String studentNumber;
	private ArrayList<Course> courses;
	
	public Student(String name, int age, String IdNumber) {
		super(name, age, IdNumber);
	}
	
	public void setStudentNumber(String studentNumber)throws Exception {
		if(studentNumber.length() == 9) {
			this.studentNumber = studentNumber;
		}else {
			throw new Exception("Invalid student number");
		}
	}
	
	public void setCourses(ArrayList<Course> courses) {
		this.courses = courses;
	}
	
	public void addCourse(Course course) throws Exception{
		Boolean exist = courses.contains(course);
		if(exist) {
			throw new Exception(course.getName() +  " already exist.");
		}else {
			courses.add(course);
		}
	}
	
	

	@Override
	void displayInfo() {
		System.out.println("Student ID: " + studentNumber);
		System.out.println("Courses enrolled:");
		for(int i = 0; i < courses.size(); i++) {
			Course course = courses.get(i);
			String courseInfo = course.getName() + "(" + course.getCode() + ")";
			System.out.println(courseInfo);
		}
	}

}
```

```java
package enrollment;

import java.util.Scanner;

public class UniversitySystem {
	
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);
		
		/// Student detail input
		System.out.println("Enter student name: ");
		String studentName = scanner.nextLine();
		System.out.println("Enter student age: ");
		int studentAge = scanner.nextInt();
		System.out.println("Enter student national ID(13 digits): ");
		String studentIdNumber = scanner.nextLine();
		
		Student student = new Student(studentName, studentAge, studentIdNumber);
		
		/// Courses details input
		System.out.println("Enter student Number(9 digits): ");
		String studentNumber = scanner.nextLine();
		System.out.println("Add course? (yes/no): ");
		Boolean isAdding = scanner.nextLine().toLowerCase() == "yes";		
		while(isAdding) {
			
		}
	}

}
```