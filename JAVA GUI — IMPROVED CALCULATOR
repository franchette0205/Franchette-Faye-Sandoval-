import javax.swing.*;
import java.awt.*;
import java.awt.event.*;

public class ImprovedCalculator extends JFrame implements ActionListener {
    private JTextField textField;
    private double num1 = 0;
    private double num2 = 0;
    private double result = 0;
    private String operator = "";

    public ImprovedCalculator() {
        setTitle("Improved Calculator");
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout());

        textField = new JTextField();
        textField.setEditable(false); // Make the text field non-editable
        add(textField, BorderLayout.NORTH);


        JPanel buttonPanel = new JPanel(new GridLayout(5, 4)); // Use GridLayout for better layout management

        String[] buttonLabels = {
                "7", "8", "9", "/",
                "4", "5", "6", "*",
                "1", "2", "3", "-",
                "0", ".", "=", "+",
                "C"
        };

        for (String label : buttonLabels) {
            JButton button = new JButton(label);
            button.addActionListener(this);
            buttonPanel.add(button);
        }

        add(buttonPanel, BorderLayout.CENTER);
        pack(); // Automatically size the frame to fit its components
        setLocationRelativeTo(null); // Center the frame on the screen
        setVisible(true);
    }

    public void actionPerformed(ActionEvent e) {
        String cmd = e.getActionCommand();

        try {
            if (cmd.matches("\\d+(\\.\\d+)?")) { //Check for numbers and decimals.
                textField.setText(textField.getText() + cmd);
            } else if ("+-*/".contains(cmd)) {
                num1 = Double.parseDouble(textField.getText());
                operator = cmd;
                textField.setText("");
            } else if (cmd.equals("=")) {
                num2 = Double.parseDouble(textField.getText());
                switch (operator) {
                    case "+": result = num1 + num2; break;
                    case "-": result = num1 - num2; break;
                    case "*": result = num1 * num2; break;
                    case "/":
                        if (num2 == 0) {
                            textField.setText("Error: Division by zero");
                            return; //Exit the function to prevent further processing
                        }
                        result = num1 / num2;
                        break;
                    default: textField.setText("Error: Invalid operation"); return;
                }
                textField.setText(String.valueOf(result));
                num1 = result; // Prepare for chained operations
                num2 = 0;
                operator = "";

            } else if (cmd.equals("C")) {
                textField.setText("");
                num1 = 0;
                num2 = 0;
                result = 0;
                operator = "";
            }
        } catch (NumberFormatException ex) {
            textField.setText("Error: Invalid input");
        }
    }

    public static void main(String[] args) {
        new ImprovedCalculator();
    }
}
