# PhonebookApp

## Description
The Phonebook Application is a Java-based program that allows users to manage their contacts easily. Users can add, search, update, and delete contacts, making it a handy tool for personal use or small businesses.

## Features
- Add new contacts with names and phone numbers.
- Search for existing contacts by name.
- Update contact details.
- Delete contacts from the phonebook.
- Display all contacts in a user-friendly interface.
- Sort contacts alphabetically.
- Analyze search efficiency based on the number of comparisons made.

## Modules
- **Phonebook**: Contains methods for managing contacts (add, delete, update, sort).
- **Contact**: Represents a contact with a name and phone number.
- **PhonebookAppGUI**: The graphical user interface that allows users to interact with the phonebook.

## Key Functions
- `addContact(String name, String phoneNumber)`: Adds a new contact to the phonebook.
- `searchContact(String name)`: Searches for a contact by name and returns the contact details if found.
- `deleteContact(String name)`: Deletes a contact from the phonebook.
- `updateContact(String name, String newPhoneNumber)`: Updates the phone number of an existing contact.

## Installation Instructions
To run the Phonebook Application, follow these steps:
1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/PhonebookApp.git
cd PhonebookApp
javac *.java
java PhonebookAppGUI

## Usage
- Launch the application, and you will be presented with a graphical interface.
- Use the menu options to add, search, update, or delete contacts.

## Contributors
- **Your Name** (your-username): Lead Developer
- **Collaborator's Name** (collaborator-username): UI Designer

## License
This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## Acknowledgments
- Thanks to the Java Swing library for providing the GUI framework.
- Special thanks to [OpenAI](https://openai.com) for assistance in generating ideas and code.


