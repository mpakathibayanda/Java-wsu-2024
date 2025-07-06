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