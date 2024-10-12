import javax.swing.*;
import java.awt.*;
import java.awt.event.ActionEvent;
import java.awt.event.ActionListener;
import java.util.ArrayList;
import java.util.Collections;
import java.util.Comparator;

public class PhonebookApp {

    private static ArrayList<Contact> phonebook = new ArrayList<>();

    public static void main(String[] args) {
        // Create the frame
        JFrame frame = new JFrame("Enhanced Phonebook Application");
        frame.setDefaultCloseOperation(JFrame.EXIT_ON_CLOSE);
        frame.setSize(600, 400);
        
        // Set the color scheme (orange and blue)
        Color orangeColor = new Color(255, 165, 0);
        Color blueColor = new Color(30, 144, 255);
        
        // Create the panel for components
        JPanel panel = new JPanel();
        panel.setLayout(new GridLayout(7, 2, 10, 10));
        panel.setBackground(orangeColor);

        // Labels and text fields
        JLabel nameLabel = new JLabel("Name:");
        nameLabel.setForeground(Color.WHITE);
        JTextField nameField = new JTextField();

        JLabel numberLabel = new JLabel("Phone Number:");
        numberLabel.setForeground(Color.WHITE);
        JTextField numberField = new JTextField();

        JTextArea displayArea = new JTextArea(10, 40);
        displayArea.setEditable(false);
        displayArea.setBackground(blueColor);
        displayArea.setForeground(Color.WHITE);
        
        JScrollPane scrollPane = new JScrollPane(displayArea);

        // Buttons
        JButton addButton = new JButton("Add Contact");
        JButton searchButton = new JButton("Search Contact");
        JButton displayButton = new JButton("Display All Contacts");
        JButton deleteButton = new JButton("Delete Contact");
        JButton updateButton = new JButton("Update Contact");
        JButton sortButton = new JButton("Sort Contacts");
        JButton analyzeButton = new JButton("Analyze Search Efficiency");

        // Adding components to the panel
        panel.add(nameLabel);
        panel.add(nameField);
        panel.add(numberLabel);
        panel.add(numberField);
        panel.add(addButton);
        panel.add(searchButton);
        panel.add(displayButton);
        panel.add(deleteButton);
        panel.add(updateButton);
        panel.add(sortButton);
        panel.add(analyzeButton);

        // Add panel and display area to the frame
        frame.add(panel, BorderLayout.NORTH);
        frame.add(scrollPane, BorderLayout.CENTER);

        // Button actions
        addButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String name = nameField.getText();
                String number = numberField.getText();
                insertContact(name, number);
                // Provide feedback to the user
                if (phonebook.stream().anyMatch(contact -> contact.getName().equalsIgnoreCase(name))) {
                    JOptionPane.showMessageDialog(null, "Contact already exists: " + name);
                } else {
                    displayArea.append("Contact added: " + name + "\n");
                    showSuccessDialog("Contact added successfully!");
                }
            }
        });

        searchButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String name = nameField.getText();
                String result = searchContact(name);
                displayArea.append(result + "\n");
                if (result.contains("not found")) {
                    showNotFoundDialog(name);
                }
            }
        });

        displayButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                displayAllContacts(displayArea);
            }
        });

        deleteButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String name = nameField.getText();
                boolean deleted = deleteContact(name);
                if (deleted) {
                    displayArea.append("Contact deleted: " + name + "\n");
                    showSuccessDialog("Contact deleted successfully!");
                } else {
                    showNotFoundDialog(name);
                }
            }
        });

        updateButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String name = nameField.getText();
                String newNumber = numberField.getText();
                boolean updated = updateContact(name, newNumber);
                if (updated) {
                    displayArea.append("Contact updated: " + name + "\n");
                    showSuccessDialog("Contact updated successfully!");
                } else {
                    showNotFoundDialog(name);
                }
            }
        });

        sortButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                sortContacts();
                displayArea.append("Contacts sorted.\n");
                showSuccessDialog("Contacts sorted successfully!");
            }
        });

        analyzeButton.addActionListener(new ActionListener() {
            @Override
            public void actionPerformed(ActionEvent e) {
                String name = nameField.getText();
                analyzeSearchEfficiency(name);
            }
        });

        // Display the frame
        frame.setVisible(true);
    }

    // Helper methods to handle phonebook operations

    public static void insertContact(String name, String phoneNumber) {
        if (name.isEmpty() || phoneNumber.isEmpty()) {
            JOptionPane.showMessageDialog(null, "Invalid contact details.");
            return;
        }
        Contact newContact = new Contact(name, phoneNumber);
        phonebook.add(newContact);
    }

    public static String searchContact(String name) {
        for (Contact contact : phonebook) {
            if (contact.getName().equalsIgnoreCase(name)) {
                return "Found: " + contact.getName() + " - " + contact.getPhoneNumber();
            }
        }
        return "Contact " + name + " not found.";
    }

    public static void displayAllContacts(JTextArea displayArea) {
        displayArea.setText(""); // Clear the display area
        if (phonebook.isEmpty()) {
            displayArea.append("No contacts available.\n");
        } else {
            for (Contact contact : phonebook) {
                displayArea.append(contact.getName() + " - " + contact.getPhoneNumber() + "\n");
            }
        }
    }

    public static boolean deleteContact(String name) {
        for (Contact contact : phonebook) {
            if (contact.getName().equalsIgnoreCase(name)) {
                phonebook.remove(contact);
                return true; // Contact found and removed
            }
        }
        return false; // Contact not found
    }

    public static boolean updateContact(String name, String newPhoneNumber) {
        for (Contact contact : phonebook) {
            if (contact.getName().equalsIgnoreCase(name)) {
                contact.setPhoneNumber(newPhoneNumber);
                return true; // Contact found and updated
            }
        }
        return false; // Contact not found
    }

    public static void sortContacts() {
        Collections.sort(phonebook, Comparator.comparing(Contact::getName));
    }

    public static void analyzeSearchEfficiency(String name) {
        int comparisons = 0;
        for (Contact contact : phonebook) {
            comparisons++;
            if (contact.getName().equalsIgnoreCase(name)) {
                JOptionPane.showMessageDialog(null, "Contact found after " + comparisons + " comparisons.");
                return;
            }
        }
        JOptionPane.showMessageDialog(null, "Contact " + name + " not found after " + comparisons + " comparisons.");
    }

    // Dialog methods for success and not found scenarios
    public static void showSuccessDialog(String message) {
        JOptionPane.showMessageDialog(null, message);
    }

    public static void showNotFoundDialog(String name) {
        JOptionPane.showMessageDialog(null, "Contact " + name + " not found.");
    }
}

// Contact class to hold contact details
class Contact {
    private String name;
    private String phoneNumber;

    public Contact(String name, String phoneNumber) {
        this.name = name;
        this.phoneNumber = phoneNumber;
    }

    public String getName() {
        return name;
    }

    public String getPhoneNumber() {
        return phoneNumber;
    }

    public void setPhoneNumber(String phoneNumber) {
        this.phoneNumber = phoneNumber;
    }
}