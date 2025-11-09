# 1
* Flowchart is in current directory

# 2
* I initialliy was trying to use a switch statement for my program like the example in the lecture. Took me a while to realize that i could just multiply the km value everytime a spinner action is called instead of having a set value. This was a big challenge to realize.

# 3
* https://youtu.be/FNn_wViDHRs?si=kASD6vgPjBICn3D-&t=876

# 4
``` java
import java.awt.GridBagConstraints;
import java.awt.GridBagLayout;
import java.awt.Insets;
import javax.swing.JFrame;
import javax.swing.JLabel;
import javax.swing.JSpinner;
import javax.swing.JTextField;
import javax.swing.SpinnerNumberModel;
import javax.swing.event.ChangeEvent;
import javax.swing.event.ChangeListener;

public class MilesToKm extends JFrame implements ChangeListener {
    private JSpinner milesSpinner;    
    private JTextField milesField; 
    private JLabel milesLabel;        
    private JLabel kmLabel;

    /* Constructor creates GUI components and adds GUI components
       using a GridBagLayout. */
    MilesToKm() {
        int initMile;     
        int minMile;      
        int maxMile;      
        int stepVal;     

        initMile = 0;
        minMile = 0;
        maxMile = 30;
        stepVal = 1;

        // Used to specify GUI component layout
        GridBagConstraints layoutConst = null;

        // Specifies the types of values displayed in spinner
        SpinnerNumberModel spinnerModel = null;

        // Set frame's title
        setTitle("Miles to km!");

        // Create labels
        milesLabel = new JLabel("Select amount of miles:");
        kmLabel = new JLabel("kilometers(km):");

        // Create a spinner model, the spinner, and set the change listener
        spinnerModel = new SpinnerNumberModel(initMile, minMile, maxMile, stepVal);
        milesSpinner = new JSpinner(spinnerModel);
        milesSpinner.addChangeListener(this);

        // Create field
        milesField = new JTextField(15);
        milesField.setEditable(false);
        milesField.setText("0");

        // Use a GridBagLayout
        setLayout(new GridBagLayout());

        // Specify component's grid location
        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 0;
        add(milesLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 0;
        add(milesSpinner, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 10, 10, 1);
        layoutConst.anchor = GridBagConstraints.LINE_END;
        layoutConst.gridx = 0;
        layoutConst.gridy = 1;
        add(kmLabel, layoutConst);

        layoutConst = new GridBagConstraints();
        layoutConst.insets = new Insets(10, 1, 10, 10);
        layoutConst.fill = GridBagConstraints.HORIZONTAL;
        layoutConst.gridx = 1;
        layoutConst.gridy = 1;
        add(milesField, layoutConst);
    }

    @Override
    public void stateChanged(ChangeEvent event) {
        int distanceMiles;

        distanceMiles = (Integer) milesSpinner.getValue();
        milesField.setText(Double.toString(distanceMiles * 1.609344));
    }

    public static void main(String[] args) {
        MilesToKm myFrame = new MilesToKm();

        myFrame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        myFrame.pack();
        myFrame.setVisible(true);
    }
}
```
