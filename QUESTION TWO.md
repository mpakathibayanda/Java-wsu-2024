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
