# 1
* Flowchart is in current directory

# 2
* This was very Similar to the first activity, So i had similar challenges. Something new that popped up while working on this was understanding providing the this input to the addActionListener. I always found using this in constructors to be confusing but i took this opportunity to learn about it. Finding out that its just a reference to the current instance of the class made sense. I felt that using it in this context also helped me understand how and when to use it.

# 3
* https://youtu.be/FNn_wViDHRs?si=LEeLCd--T7ZIFRtQ&t=546

# 4
``` java
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.text.NumberFormat;
import javax.swing.JButton;
import javax.swing.JFormattedTextField;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JOptionPane;
import javax.swing.JTextField;

public class MilestoKMandM extends JFrame implements ActionListener {
    private JButton calcButton;            
    private JLabel distLabel;             
    private JLabel kilometersLabel;            
    private JLabel metersLabel;         
    private JTextField kilometerField;        
    private JTextField meterField;      
    private JFormattedTextField distField;

    /* Constructor creates GUI components and adds GUI components
       using a GridBagLayout. */
    MilestoKMandM() {
        // Used to specify GUI component layout
        GridBagConstraints layoutConst = null;

        // Set frame's title
        setTitle("Miles to km and m");

        // Create labels
        distLabel = new JLabel("Distance (miles):");
        kilometersLabel = new JLabel("km:");
        metersLabel = new JLabel("m:");

        // Create button and add action listener
        calcButton = new JButton("Calculate");
        calcButton.addActionListener(this);

        //Create fields
        kilometerField = new JTextField(15);
        kilometerField.setEditable(false);

        
        meterField = new JTextField(15);
        meterField.setEditable(false);

        // Create and set-up an input field for numbers (not text)
        distField = new JFormattedTextField(NumberFormat.getNumberInstance());
        distField.setEditable(true);
        distField.setText("0");
        distField.setColumns(15); // Initial width of 10 units

        // Use a GridBagLayout
        setLayout(new GridBagLayout());

        // Specify component's grid location
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        add(distLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.gridx = 1;
        layoutConst.gridy = 0;
        add(distField, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 5, 10, 10);
        layoutConst.gridx = 2;
        layoutConst.gridy = 0;
        add(calcButton, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 0, 1, 10);
        layoutConst.gridx = 1;
        layoutConst.gridy = 1;
        add(kilometersLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1, 0, 10, 10);
        layoutConst.gridx = 1;
        layoutConst.gridy = 2;
        add(kilometerField, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 0, 1, 10);
        layoutConst.gridx = 2;
        layoutConst.gridy = 1;
        add(metersLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(1, 0, 10, 10);
        layoutConst.gridx = 2;
        layoutConst.gridy = 2;
        add(meterField, layoutConst);
    }

    /* Method is automatically called when an event
       occurs (e.g, Enter key is pressed) */
    @Override
    public void actionPerformed(ActionEvent event) {
        double totMiles;     // Distance to travel
        double toKm;       // Corresponding Kilometers
        double toM;     // Corresponding Meters

        // Get value from distance field
        totMiles = ((Number) distField.getValue()).doubleValue();

        // Check if miles input is positive
        if (totMiles >= 0.0) {
            toKm = totMiles * 1.609344;
            toM = totMiles * 1609.344;

            kilometerField.setText(Double.toString(toKm));
            meterField.setText(Double.toString(toM));
        }
        else {
            // Show failure dialog
            JOptionPane.showMessageDialog(this, "Enter a positive distance value!");
        }
    }

    public static void main(String[] args) {
        // Creates MilestoKMandM and its components
        MilestoKMandM myFrame = new MilestoKMandM();

        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```

