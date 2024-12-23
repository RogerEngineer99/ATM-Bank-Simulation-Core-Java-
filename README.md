ATM Bank Simulation (Core Java)



Overview



The ATM Bank Simulation is a Core Java-based application designed to simulate a banking system. This project demonstrates advanced Java programming concepts, including object-oriented principles like inheritance, encapsulation, and interaction between classes. The application allows users to perform typical banking operations such as withdrawing money, depositing funds, checking balances, transferring money between accounts, and more.



Project Duration:



Spring 2019



Features

• Bank Account Operations:

• Users can perform basic banking operations such as withdraw, deposit, and check the current balance of their account.

• Transfer Funds:

• Users can transfer money between accounts, specifying the target bank account.

• Transaction Fees:

• Transaction fees are applied to specific actions like deposits, withdrawals, and transfers.

• Account Locking:

• Users can lock their account via the application for security purposes.

• PIN Protection:

• Users must enter a PIN to log in to their account, ensuring secure access to banking operations.

• Transaction History:

• All transactions are recorded within the application for future reference.



Components and Technologies Used

• Java: Core Java was used to develop the entire application.

• Object-Oriented Programming: The application is designed using object-oriented principles, such as inheritance, abstraction, and polymorphism.

• Classes and Subclasses: Various subclasses were implemented to represent different functionalities, with interdependencies between them.



Key Classes:

• BankAccount: The main class representing a bank account, with methods for deposit, withdrawal, checking balance, and transferring funds.

• Transaction: A subclass that handles transaction history and applies fees to specific transactions.

• Security: A subclass for handling account locking and PIN verification.

• ATM: The entry point of the program where users interact with the application.



Design and Implementation



1. Bank Account Operations:



The application allows users to interact with their bank account by performing typical operations:

• Withdraw: Users can withdraw funds from their bank account.

• Deposit: Users can deposit funds into their account.

• Check Balance: Users can check their current balance.



2. Money Transfer:



The transfer feature allows users to move money from one account to another. It ensures that both the sender’s and the receiver’s balances are updated correctly.



3. Transaction Fees:



Fees are applied on certain actions, such as:

• A small fee for each withdrawal or deposit.

• Transfer fees for moving money between accounts.



4. Account Locking:



The program allows users to lock their account for security. Once locked, the account cannot perform transactions until it is unlocked.



5. PIN Verification:



For security, users must enter their PIN before they can log in and access any banking features. The PIN is securely stored and checked against the user’s input during login.



6. Interdependent Subclasses:



The program implements several subclasses with dependencies:

• Account: Contains the core methods for interacting with the bank account.

• Transaction: Handles transaction logs and fee calculations.

• Security: Manages account locking and PIN validation.

These classes interact with the main ATM class, which serves as the controller, running all the functionality and providing a user interface.



Example of Usage



1. Creating an Account:



To create an account, the user simply runs the application and is prompted to enter their initial balance, PIN, and other personal details.



2. Performing Transactions:



Once logged in with a valid PIN, users can:

• Withdraw funds from their account by specifying the amount.

• Deposit funds into their account.

• Transfer money to another account by entering the target account number and amount.



3. Locking an Account:



Users can lock their account from within the application, making it inaccessible for any further transactions until they unlock it.



Example Java Code



import java.util.Scanner;



class BankAccount {

    private double balance;

    private String pin;

    private boolean locked;

    private String transactionHistory = "";



    public BankAccount(String pin, double initialBalance) {

        this.pin = pin;

        this.balance = initialBalance;

        this.locked = false;

    }



    public boolean checkPin(String enteredPin) {

        return this.pin.equals(enteredPin);

    }



    public void deposit(double amount) {

        if (!locked) {

            balance += amount;

            transactionHistory += "Deposited: " + amount + "\n";

        } else {

            System.out.println("Account is locked!");

        }

    }



    public void withdraw(double amount) {

        if (!locked) {

            if (balance >= amount) {

                balance -= amount;

                transactionHistory += "Withdrew: " + amount + "\n";

            } else {

                System.out.println("Insufficient funds!");

            }

        } else {

            System.out.println("Account is locked!");

        }

    }



    public void transfer(double amount, BankAccount targetAccount) {

        if (!locked) {

            if (balance >= amount) {

                balance -= amount;

                targetAccount.deposit(amount);

                transactionHistory += "Transferred: " + amount + "\n";

            } else {

                System.out.println("Insufficient funds for transfer!");

            }

        } else {

            System.out.println("Account is locked!");

        }

    }



    public void lockAccount() {

        this.locked = true;

    }



    public void unlockAccount() {

        this.locked = false;

    }



    public double getBalance() {

        return balance;

    }



    public String getTransactionHistory() {

        return transactionHistory;

    }

}



public class ATM {

    public static void main(String[] args) {

        Scanner scanner = new Scanner(System.in);



        // Create bank accounts for two users

        BankAccount user1 = new BankAccount("1234", 1000);

        BankAccount user2 = new BankAccount("5678", 500);



        System.out.println("Enter PIN to access your account:");

        String enteredPin = scanner.nextLine();



        if (user1.checkPin(enteredPin)) {

            System.out.println("Login successful.");

            System.out.println("Current balance: $" + user1.getBalance());

            

            // Perform transactions

            user1.deposit(500);

            user1.withdraw(200);

            user1.transfer(100, user2);



            // Display transaction history

            System.out.println("Transaction history:");

            System.out.println(user1.getTransactionHistory());

        } else {

            System.out.println("Incorrect PIN.");

        }



        scanner.close();

    }

}



Key Methods:

• deposit(): Adds money to the account balance.

• withdraw(): Subtracts money from the account balance.

• transfer(): Transfers money between two bank accounts.

• lockAccount(): Locks the account to prevent any transactions.

• unlockAccount(): Unlocks the account for further transactions.

• checkPin(): Verifies the PIN entered by the user.



Future Enhancements

• GUI Interface: Adding a graphical user interface (GUI) for a more user-friendly interaction.

• Database Integration: Storing account details and transaction histories in a database.

• Additional Account Types: Implementing different account types (e.g., savings, checking, etc.) with unique features.

• Multi-user Support: Allowing multiple users to access the application concurrently.



License



This project is licensed under the MIT License. See the LICENSE file for more details.



This README.md outlines the main functionality and design of the ATM Bank Simulation project, providing an overview of the features, classes, and example usage. I can extend the implementation by adding a GUI or integrating with a database, as mentioned in the future enhancements section.
