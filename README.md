# WSU PROGRANNING IN JAVA 2024 MAIN EXAMS

## Question 1.1

```java

package gui;

import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;


public class SumCalculator{
	private JFrame frame;
    private JLabel resultLabel;
    private JTextField num1Field;
    private JTextField num2Field;
    private JButton sumButton;

    public SumCalculator() {
        // JFrame setup
    	frame.setDefaultCloseOperation(JFrame.DO_NOTHING_ON_CLOSE);
    	frame.setSize(300, 400); // Adjusted size for better layout
    	frame.setLocationRelativeTo(null); // Center the window

        // Use FlowLayout as required
    	frame.setLayout(new FlowLayout());

        // Create components
        JLabel label1 = new JLabel("Number 1:"); // First JLabel
        num1Field = new JTextField(10); // First JTextField
        JLabel label2 = new JLabel("Number 2:"); // Second JLabel
        num2Field = new JTextField(10); // Second JTextField
        sumButton = new JButton("Calculate Sum"); // JButton
        resultLabel = new JLabel("Sum: "); // JLabel to display the sum

        // Add components to the frame
        frame.add(label1);
        frame.add(num1Field);
        frame.add(label2);
        frame.add(num2Field);
        frame.add(sumButton);
        frame.add(resultLabel);

        // Add ActionListener to the JButton using an anonymous class
        sumButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
            	calculateSum();
            }
        });
    }

	private void calculateSum() {
		try {
	        // Get numbers from JTextFields
	        double num1 = Double.parseDouble(num1Field.getText());
	        double num2 = Double.parseDouble(num2Field.getText());
	
	        // Calculate sum
	        double sum = num1 + num2;
	
	        // Display sum in the resultLabel
	        resultLabel.setText("Sum: " + sum);
	    } catch (NumberFormatException ex) {
	        // Handle case where input is not a valid number
	        resultLabel.setText("Error: Invalid number input!");
	    }
	}
    public static void main(String[] args) {
		// Run the GUI on the Event Dispatch Thread
        SwingUtilities.invokeLater(
                new Runnable() {
                    @Override
                    public void run() {
                        new SumCalculator().frame.setVisible(true);
                    }
                }
            );
    }
}
```

## QUESTION 1.2

```java
package gui;

import java.awt.GridLayout;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;

import javax.swing.*;

public class CostCalculator {
	private JFrame frame;
	private JLabel storeLabel;
	private JLabel totalCostLabel;
	private JTextField costAmountField;
	private JComboBox<String> paymentOptions;
	private JButton calculateBtn;

	public CostCalculator() {
		// 1 Initialize
		frame = new JFrame();
		storeLabel = new JLabel("SuperSpar");
		totalCostLabel = new JLabel("Total Cost:");
		costAmountField = new JTextField(10);
		paymentOptions = new JComboBox<String>();
		calculateBtn = new JButton("Calculate Total");
		
		
		// 2. Setup.
		frame.setDefaultCloseOperation(3);
		frame.setSize(300, 200);
		frame.setLocationRelativeTo(null);
		frame.setTitle("SuperSpar");
		
		// 3 Set Layout.
		frame.setLayout(new GridLayout(4,0,20,0));
		
		// 4 Add Components to the Frame.
		frame.add(storeLabel);
		frame.add(costAmountField);
		frame.add(totalCostLabel);
		frame.add(paymentOptions);
		frame.add(calculateBtn);
		
		// Adding payment options.
		paymentOptions.addItem("Cash"); // 0
		paymentOptions.addItem("Credit Card");// 1
		paymentOptions.addItem("Debit Card"); // 2
		
		// Add Action listener
		calculateBtn.addActionListener(new ActionListener() {
			
			@Override
			public void actionPerformed(ActionEvent e) {
				calculateTotalCost();				
			}
		});
		
	}
	
	void calculateTotalCost() {
		try {
			int index = paymentOptions.getSelectedIndex();
			double totalCost = Double.parseDouble(costAmountField.getText());
			if(index == 0) {
				totalCost = totalCost - (totalCost*0.05);
			}
			if(index == 1) {
			    totalCost = totalCost + (totalCost*0.03);
			}
			
			totalCostLabel.setText("Total Cost: R"+totalCost);
			
		} catch (Exception e) {
			e.getMessage();
		}
	}

	public static void main(String[] args) {
		// Run the GUI on the Event Dispatch Thread
        SwingUtilities.invokeLater(
                new Runnable() {
                    @Override
                    public void run() {
                        new CostCalculator().frame.setVisible(true);
                    }
                }
            );
	}

}

```

## QUESTION TWO


```java
package banking;

public class BankAccount {
	// 2.2.1
	private int accountNumber;
	private double balance;

	// 2.2.2
	public BankAccount(int accountNumber) {
		accountNumber = this.accountNumber;
		balance = 0;
	}
	
	public void deposit(double amount) {
		balance = balance +amount;
	}
	
	public void withdraw(double amount) {
		if(amount > balance) {
			System.out.println("Exceed balance.");
			return;
		}else {
			balance = balance - amount;
		}		
	}
	
	double getBalance() {
		return this.balance;
	}

}
```

```java
import java.util.Scanner;

public class BankAccountApp {
	
	public static void main(String[] args) {
		Scanner scanner = new Scanner(System.in);		
		System.out.println("Enter the account number: ");		
		try {
			int accountNumber = scanner.nextInt();
			BankAccount bankAccount = new BankAccount(accountNumber);
			System.out.println("Account created\nBalance: " + bankAccount.getBalance());
			
		} catch (NumberFormatException e) {
			System.out.println("Invalid account number!!");
		}finally{
			scanner.close();
		}
		
		
		
	}

}
```

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
