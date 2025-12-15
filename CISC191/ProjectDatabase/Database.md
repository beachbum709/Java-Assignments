# I noticed what to submit was different this time around. Only code and video are required. If anything else is needed please let me know.

## Video
* https://www.youtube.com/watch?v=6CC0IxvSaXI

```java
import javax.swing.*;
import javax.swing.table.DefaultTableModel;
import java.awt.*;
import java.io.*;
import java.sql.*;

public class AutoMPGApp extends JFrame {
    //file path for text file
    private static final String DATA_FILE_PATH = "auto.txt";
    private static final String DB_URL = "jdbc:mysql://localhost/Auto";
    private static final String DB_USER = "testuser";
    private static final String DB_PASSWORD = "";
    
    //instantiating gui elements
    private JTextField queryField;
    private JTable resultTable;
    private DefaultTableModel tableModel;
    private JButton searchButton, loadButton, resetButton;
    private JSlider mpgSlider, horsepowerSlider;
    private JLabel mpgValueLabel, horsepowerValueLabel, recordCountLabel;
    
    //setting up main gui and populating records
    public AutoMPGApp() {
        setTitle("Auto MPG Database Application");
        setSize(1200, 700);
        setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        setLayout(new BorderLayout(10, 10));
        
        JPanel mainPanel = new JPanel(new BorderLayout(10, 10));
        mainPanel.setBorder(BorderFactory.createEmptyBorder(10, 10, 10, 10));
        
        JPanel topPanel = createTopPanel();
        mainPanel.add(topPanel, BorderLayout.NORTH);
        
        JPanel centerPanel = createCenterPanel();
        mainPanel.add(centerPanel, BorderLayout.CENTER);
        
        JPanel bottomPanel = createBottomPanel();
        mainPanel.add(bottomPanel, BorderLayout.SOUTH);
        
        add(mainPanel);
        
        displayAllRecords();
        updateRecordCount();
        
        setLocationRelativeTo(null);
    }
    
    // function for creating each panel with all the buttons and sliders that are included
    private JPanel createTopPanel() {
        JPanel panel = new JPanel();
        panel.setLayout(new BoxLayout(panel, BoxLayout.Y_AXIS));
        panel.setBorder(BorderFactory.createTitledBorder("Search and Data Management"));
        
        JPanel searchRow = new JPanel(new FlowLayout(FlowLayout.LEFT, 10, 5));
        searchRow.add(new JLabel("Enter Query:"));
        queryField = new JTextField(30);
        searchRow.add(queryField);
        
        searchButton = new JButton("Search");
        searchButton.setBackground(new Color(70, 130, 180));
        searchButton.setForeground(Color.WHITE);
        searchRow.add(searchButton);
        
        JLabel hintLabel = new JLabel("(Type 'ALL' to see all records)");
        hintLabel.setFont(new Font("Arial", Font.ITALIC, 11));
        searchRow.add(hintLabel);
        
        panel.add(searchRow);
        
        JPanel buttonRow = new JPanel(new FlowLayout(FlowLayout.LEFT, 10, 5));
        loadButton = new JButton("Load Data from File");
        loadButton.setBackground(new Color(60, 179, 113));
        loadButton.setForeground(Color.WHITE);
        buttonRow.add(loadButton);
        
        resetButton = new JButton("Reset Filters");
        resetButton.setBackground(new Color(220, 20, 60));
        resetButton.setForeground(Color.WHITE);
        buttonRow.add(resetButton);
        
        recordCountLabel = new JLabel("Records: 0");
        recordCountLabel.setFont(new Font("Arial", Font.BOLD, 12));
        buttonRow.add(Box.createHorizontalStrut(20));
        buttonRow.add(recordCountLabel);
        
        panel.add(buttonRow);
        
        searchButton.addActionListener(e -> performSearch());
        queryField.addActionListener(e -> performSearch());
        loadButton.addActionListener(e -> loadDataFromFilePath());
        resetButton.addActionListener(e -> resetFilters());
        
        return panel;
    }
    
    private JPanel createCenterPanel() {
        JPanel panel = new JPanel(new BorderLayout());
        panel.setBorder(BorderFactory.createTitledBorder("Query Results"));
        
        String[] columnNames = {"ID", "MPG", "Cylinders", "Displacement", "Horsepower", 
                                "Weight", "Acceleration", "Model Year", "Origin", "Car Name"};
        tableModel = new DefaultTableModel(columnNames, 0) {
            @Override
            public boolean isCellEditable(int row, int column) {
                return false;
            }
        };
        
        resultTable = new JTable(tableModel);
        resultTable.setAutoResizeMode(JTable.AUTO_RESIZE_OFF);
        resultTable.getColumnModel().getColumn(0).setPreferredWidth(50);
        resultTable.getColumnModel().getColumn(1).setPreferredWidth(60);
        resultTable.getColumnModel().getColumn(2).setPreferredWidth(70);
        resultTable.getColumnModel().getColumn(3).setPreferredWidth(90);
        resultTable.getColumnModel().getColumn(4).setPreferredWidth(80);
        resultTable.getColumnModel().getColumn(5).setPreferredWidth(70);
        resultTable.getColumnModel().getColumn(6).setPreferredWidth(90);
        resultTable.getColumnModel().getColumn(7).setPreferredWidth(80);
        resultTable.getColumnModel().getColumn(8).setPreferredWidth(60);
        resultTable.getColumnModel().getColumn(9).setPreferredWidth(300);
        
        JScrollPane scrollPane = new JScrollPane(resultTable);
        panel.add(scrollPane, BorderLayout.CENTER);
        
        return panel;
    }
    
    private JPanel createBottomPanel() {
        JPanel panel = new JPanel(new GridLayout(2, 1, 5, 5));
        panel.setBorder(BorderFactory.createTitledBorder("Filter by MPG and Horsepower"));
        
        JPanel mpgPanel = new JPanel(new BorderLayout(10, 5));
        JLabel mpgLabel = new JLabel("MPG Range:");
        mpgValueLabel = new JLabel("0 - 50");
        mpgValueLabel.setFont(new Font("Arial", Font.BOLD, 12));
        
        mpgSlider = new JSlider(JSlider.HORIZONTAL, 0, 50, 25);
        mpgSlider.setMajorTickSpacing(10);
        mpgSlider.setMinorTickSpacing(5);
        mpgSlider.setPaintTicks(true);
        mpgSlider.setPaintLabels(true);
        
        JPanel mpgLabelPanel = new JPanel(new FlowLayout(FlowLayout.LEFT));
        mpgLabelPanel.add(mpgLabel);
        mpgLabelPanel.add(mpgValueLabel);
        
        mpgPanel.add(mpgLabelPanel, BorderLayout.WEST);
        mpgPanel.add(mpgSlider, BorderLayout.CENTER);
        
        JPanel hpPanel = new JPanel(new BorderLayout(10, 5));
        JLabel hpLabel = new JLabel("Horsepower:");
        horsepowerValueLabel = new JLabel("0 - 300");
        horsepowerValueLabel.setFont(new Font("Arial", Font.BOLD, 12));
        
        horsepowerSlider = new JSlider(JSlider.HORIZONTAL, 0, 300, 150);
        horsepowerSlider.setMajorTickSpacing(50);
        horsepowerSlider.setMinorTickSpacing(25);
        horsepowerSlider.setPaintTicks(true);
        horsepowerSlider.setPaintLabels(true);
        
        JPanel hpLabelPanel = new JPanel(new FlowLayout(FlowLayout.LEFT));
        hpLabelPanel.add(hpLabel);
        hpLabelPanel.add(horsepowerValueLabel);
        
        hpPanel.add(hpLabelPanel, BorderLayout.WEST);
        hpPanel.add(horsepowerSlider, BorderLayout.CENTER);
        
        panel.add(mpgPanel);
        panel.add(hpPanel);
        
        mpgSlider.addChangeListener(e -> {
            int value = mpgSlider.getValue();
            mpgValueLabel.setText(">= " + value);
            if (!mpgSlider.getValueIsAdjusting()) {
                filterBySliders();
            }
        });
        
        horsepowerSlider.addChangeListener(e -> {
            int value = horsepowerSlider.getValue();
            horsepowerValueLabel.setText("<= " + value);
            if (!horsepowerSlider.getValueIsAdjusting()) {
                filterBySliders();
            }
        });
        
        return panel;
    }
    
    private void performSearch() {
        String query = queryField.getText().trim();
        if (query.isEmpty()) {
            JOptionPane.showMessageDialog(this, "Please enter a query");
            return;
        }
        
        if (query.equalsIgnoreCase("ALL")) {
            displayAllRecords();
        } else {
            searchRecords(query);
        }
    }
    
    // function to load info from text file, loads info when pressing button on top panel
    private void loadDataFromFilePath() {
        File file = new File(DATA_FILE_PATH);
        
        if (!file.exists()) {
            JOptionPane.showMessageDialog(this, 
                "File not found: " + DATA_FILE_PATH + "\n\nPlease update the DATA_FILE_PATH constant in the code.", 
                "Error", 
                JOptionPane.ERROR_MESSAGE);
            return;
        }
        
        if (!file.isFile()) {
            JOptionPane.showMessageDialog(this, 
                "Path is not a file: " + DATA_FILE_PATH, 
                "Error", 
                JOptionPane.ERROR_MESSAGE);
            return;
        }
        
        JDialog progressDialog = new JDialog(this, "Loading Data...", true);
        JProgressBar progressBar = new JProgressBar();
        progressBar.setIndeterminate(true);
        progressDialog.add(progressBar);
        progressDialog.setSize(300, 80);
        progressDialog.setLocationRelativeTo(this);
        
        SwingWorker<Integer, Void> worker = new SwingWorker<Integer, Void>() {
            @Override
            protected Integer doInBackground() throws Exception {
                return insertDataFromFile(file);
            }
            
            @Override
            protected void done() {
                progressDialog.dispose();
                try {
                    int count = get();
                    JOptionPane.showMessageDialog(AutoMPGApp.this, 
                        count + " records loaded successfully from:\n" + DATA_FILE_PATH, 
                        "Success", JOptionPane.INFORMATION_MESSAGE);
                    displayAllRecords();
                } catch (Exception e) {
                    JOptionPane.showMessageDialog(AutoMPGApp.this, 
                        "Error loading file: " + e.getMessage(), 
                        "Error", JOptionPane.ERROR_MESSAGE);
                    e.printStackTrace();
                }
            }
        };
        
        worker.execute();
        progressDialog.setVisible(true);
    }
    
    //populate table from data in file
    private int insertDataFromFile(File file) throws Exception {
        try (Connection conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);
             BufferedReader br = new BufferedReader(new FileReader(file))) {
            
            String sql = "INSERT INTO auto_mpg (mpg, cylinders, displacement, horsepower, " +
                        "weight, acceleration, model_year, origin, car_name) VALUES (?, ?, ?, ?, ?, ?, ?, ?, ?)";
            PreparedStatement pstmt = conn.prepareStatement(sql);
            
            String line;
            int count = 0;
            int lineNumber = 0;
            
            System.out.println("Starting to read file: " + file.getAbsolutePath());
            
            while ((line = br.readLine()) != null) {
                lineNumber++;
                line = line.trim();
                
                if (line.isEmpty()) {
                    continue;
                }
                
                if (line.toLowerCase().contains("mpg") && line.toLowerCase().contains("cylinders")) {
                    System.out.println("Line " + lineNumber + ": Header detected, skipping");
                    continue;
                }
                
                String[] values = parseString(line);
                
                if (values != null && values.length >= 9) {
                    try {
                        pstmt.setDouble(1, parseDouble(values[0]));
                        pstmt.setInt(2, parseIntSafe(values[1]));
                        pstmt.setDouble(3, parseDouble(values[2]));
                        pstmt.setDouble(4, parseDouble(values[3]));
                        pstmt.setDouble(5, parseDouble(values[4]));
                        pstmt.setDouble(6, parseDouble(values[5]));
                        pstmt.setInt(7, parseIntSafe(values[6]));
                        pstmt.setInt(8, parseIntSafe(values[7]));
                        pstmt.setString(9, values[8].trim().replace("\"", ""));
                        
                        pstmt.executeUpdate();
                        count++;
                    } catch (Exception e) {
                        System.err.println("ERROR parsing line " + lineNumber + ": " + e.getMessage());
                        e.printStackTrace();
                    }
                }
            }
            
            System.out.println("Finished reading file. Total records inserted: " + count);
            return count;
        }
    }
    
    private String[] parseString(String line) {
        try {
            int quoteStart = line.indexOf('"');
            if (quoteStart == -1) {
                return line.split("\\s+");
            }
            
            String numericPart = line.substring(0, quoteStart).trim();
            String[] numericValues = numericPart.split("\\s+");
            
            String carName = line.substring(quoteStart).trim();
            carName = carName.replaceAll("\"", "");
            
            String[] result = new String[9];
            for (int i = 0; i < Math.min(8, numericValues.length); i++) {
                result[i] = numericValues[i];
            }
            for (int i = numericValues.length; i < 8; i++) {
                result[i] = "0";
            }
            result[8] = carName;
            
            return result;
        } catch (Exception e) {
            System.err.println("Error parsing UCI format: " + e.getMessage());
            return null;
        }
    }
    
    private int parseIntSafe(String value) {
        try {
            value = value.trim();
            
            if (value.equalsIgnoreCase("NA") || value.isEmpty()) {
                return 0;
            }
            
            if (value.contains(".")) {
                double doubleVal = Double.parseDouble(value);
                return (int) doubleVal;
            }
            
            return Integer.parseInt(value);
            
        } catch (NumberFormatException e) {
            System.err.println("Cannot parse int from: '" + value + "' - returning 0");
            return 0;
        }
    }
    
    private double parseDouble(String value) {
        try {
            value = value.trim();
            
            if (value.equalsIgnoreCase("NA") || value.isEmpty()) {
                return 0.0;
            }
            
            return Double.parseDouble(value);
            
        } catch (NumberFormatException e) {
            System.err.println("Cannot parse double: '" + value + "' - returning 0.0");
            return 0.0;
        }
    }
    
    private void displayAllRecords() {
        tableModel.setRowCount(0);
        
        String sql = "SELECT * FROM auto_mpg ORDER BY id";
        
        try (Connection conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);
             Statement stmt = conn.createStatement();
             ResultSet rs = stmt.executeQuery(sql)) {
            
            while (rs.next()) {
                Object[] row = {
                    rs.getInt("id"),
                    rs.getDouble("mpg"),
                    rs.getInt("cylinders"),
                    rs.getDouble("displacement"),
                    rs.getDouble("horsepower"),
                    rs.getDouble("weight"),
                    rs.getDouble("acceleration"),
                    rs.getInt("model_year"),
                    rs.getInt("origin"),
                    rs.getString("car_name")
                };
                tableModel.addRow(row);
            }
            
            updateRecordCount();
            
        } catch (Exception e) {
            JOptionPane.showMessageDialog(this, "Error: " + e.getMessage());
            e.printStackTrace();
        }
    }
    
    private void searchRecords(String query) {
        tableModel.setRowCount(0);
        
        String sql = "SELECT * FROM auto_mpg WHERE car_name LIKE ? OR " +
                    "CAST(mpg AS CHAR) LIKE ? OR CAST(horsepower AS CHAR) LIKE ? OR " +
                    "CAST(cylinders AS CHAR) LIKE ? ORDER BY id";
        
        try (Connection conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);
             PreparedStatement pstmt = conn.prepareStatement(sql)) {
            
            String searchPattern = "%" + query + "%";
            pstmt.setString(1, searchPattern);
            pstmt.setString(2, searchPattern);
            pstmt.setString(3, searchPattern);
            pstmt.setString(4, searchPattern);
            
            ResultSet rs = pstmt.executeQuery();
            
            while (rs.next()) {
                Object[] row = {
                    rs.getInt("id"),
                    rs.getDouble("mpg"),
                    rs.getInt("cylinders"),
                    rs.getDouble("displacement"),
                    rs.getDouble("horsepower"),
                    rs.getDouble("weight"),
                    rs.getDouble("acceleration"),
                    rs.getInt("model_year"),
                    rs.getInt("origin"),
                    rs.getString("car_name")
                };
                tableModel.addRow(row);
            }
            
            updateRecordCount();
            
            if (tableModel.getRowCount() == 0) {
                JOptionPane.showMessageDialog(this, "No records found for: " + query);
            }
            
        } catch (Exception e) {
            JOptionPane.showMessageDialog(this, "Error: " + e.getMessage());
            e.printStackTrace();
        }
    }
    
    private void filterBySliders() {
        tableModel.setRowCount(0);
        
        int minMpg = mpgSlider.getValue();
        int maxHorsepower = horsepowerSlider.getValue();
        
        String sql = "SELECT * FROM auto_mpg WHERE mpg >= ? AND horsepower <= ? ORDER BY mpg DESC, horsepower ASC";
        
        try (Connection conn = DriverManager.getConnection(DB_URL, DB_USER, DB_PASSWORD);
             PreparedStatement pstmt = conn.prepareStatement(sql)) {
            
            pstmt.setInt(1, minMpg);
            pstmt.setInt(2, maxHorsepower);
            
            ResultSet rs = pstmt.executeQuery();
            
            while (rs.next()) {
                Object[] row = {
                    rs.getInt("id"),
                    rs.getDouble("mpg"),
                    rs.getInt("cylinders"),
                    rs.getDouble("displacement"),
                    rs.getDouble("horsepower"),
                    rs.getDouble("weight"),
                    rs.getDouble("acceleration"),
                    rs.getInt("model_year"),
                    rs.getInt("origin"),
                    rs.getString("car_name")
                };
                tableModel.addRow(row);
            }
            
            updateRecordCount();
            
        } catch (Exception e) {
            JOptionPane.showMessageDialog(this, "Error: " + e.getMessage());
            e.printStackTrace();
        }
    }
    
    private void resetFilters() {
        mpgSlider.setValue(0);
        horsepowerSlider.setValue(300);
        queryField.setText("");
        displayAllRecords();
    }
    
    private void updateRecordCount() {
        recordCountLabel.setText("Records: " + tableModel.getRowCount());
    }
    
    public static void main(String[] args) {
        try {
            UIManager.setLookAndFeel(UIManager.getSystemLookAndFeelClassName());
        } catch (Exception e) {
            e.printStackTrace();
        }
        
        try {
            Class.forName("com.mysql.cj.jdbc.Driver");
        } catch (ClassNotFoundException e) {
            System.err.println("MySQL JDBC Driver not found!");
            System.err.println("Please download MySQL Connector/J from:");
            System.err.println("https://dev.mysql.com/downloads/connector/j/");
            e.printStackTrace();
            return;
        }
        
        SwingUtilities.invokeLater(() -> {
            AutoMPGApp app = new AutoMPGApp();
            app.setVisible(true);
        });
    }
}
```
