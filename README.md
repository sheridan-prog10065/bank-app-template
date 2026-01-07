# Exercise: OOP Bank. An Object-Oriented ATM Application
In this exercise, students practice object-oriented programming, working with relationships including inheritance, polymorphsim, collections and working with persistence.
 
The application should allow a user to create and select accounts, perform typical banking operations, and later extend this functionality using inheritance, polymorphism, error handling, and basic data persistence.

***

## Learning Objectives

- Practice object-oriented design using multiple collaborating classes. 
- Implement inheritance and polymorphism with specialized account types. 
- Apply basic error handling and simple file-based data persistence. 

***

## Project Setup

- Implement the following classes (see your own UML or design diagram): 
  - `AtmApplication`  
  - `Account`  
  - `Bank`  

For each class, define appropriate fields and methods following your design. 

***

## Class Responsibilities

### AtmApplication

- Handles all user interaction (display menus, read input, show output). 
- Displays an ATM main menu in a loop until the user chooses to exit. 
- Main menu options (at minimum): 
  - Create Account  
  - Select Account  
  - Exit  

- When an account is selected, display an account menu: 
  - Check Balance  
  - Deposit  
  - Withdraw  
  - Predict Balance (reuse the functionality from the earlier assignment for interest prediction)  
  - Exit Account  

- Create a `Bank` object that initializes a list of 10 default accounts with IDs 100–109, each with an initial balance of 100 and an annual interest rate of 10%. 
- Implement each menu option in its own handler method, named using a clear pattern such as `OnCreateAccount()`, `OnSelectAccount()`, `OnCheckBalance()`, etc. 

### Bank

- Maintains a list (or other collection) of `Account` objects. 
- Constructor should: 
  - Create the collection to hold accounts.  
  - Populate it with 10 default accounts (IDs 100–109, balance 100, interest rate 10%).  

- Implement a method `RetrieveAccount()` that returns an `Account` given an account ID, to be used by `AtmApplication`. 

### Account

- Implements basic account features: 
  - Balance  
  - Withdrawals  
  - Deposits  
  - Interest calculation / prediction  

***

## Business Logic Requirements

Implement the following behaviors in your ATM application. 

### Main Menu

- **Create Account**  
  - Prompt for: account number, initial balance, interest rate, and annual interest rate. 
  - Create a new account and add it to the bank’s list. 

- **Select Account**  
  - Prompt for an account number. 
  - Retrieve the account from the bank.  
  - If found, display the account menu for that account. 

- **Exit**  
  - Cleanly exit the application. 

### Account Menu

Operate on the previously selected account. 

- **Check Balance**  
  - Display the current balance. 

- **Deposit**  
  - Prompt for a deposit amount and apply it to the account. 
  - Record the deposit as a transaction. 

- **Withdraw**  
  - Prompt for a withdrawal amount and apply it to the account, respecting account rules. 
  - Record the withdrawal as a transaction. 

- **Predict Balance**  
  - Display a predicted statement showing balance and interest for the next 12 months (reuse your earlier interest-calculation logic). 

***

## Inheritance and Polymorphism

Extend the `Account` class with two subclasses: `ChequingAccount` and `SavingsAccount`. 

### ChequingAccount

- Inherits from `Account` without duplicating fields. 
- Supports an overdraft limit of 500 units (balance may go as low as -500). 
- Enforces a maximum annual interest rate of 1%. 

### SavingsAccount

- Inherits from `Account` without duplicating fields. 
- Cannot be overdrawn (no negative balance allowed). 
- Enforces a minimum annual interest rate of 3%. 
- For every 1 unit deposited by the user, the bank automatically adds an extra 0.5 units. 

### ATM Integration

- Update the account creation menu so the user can choose the account type (chequing or savings). 
- Instantiate `ChequingAccount` or `SavingsAccount` based on the user’s choice. 
- Ensure the rest of the application works unchanged by relying on polymorphism through the base `Account` type. 

***

## Error Handling

- Validate all user input for type and range (for example, numeric input where required, non-negative amounts where appropriate). 
- Use standard error checking plus exception handling to manage invalid input or unexpected conditions without crashing the program. 

***

## Data Persistence

Add simple file-based persistence for account data. 

- Store each account’s data in a separate text file, named using the account number to ensure uniqueness. 
- Each file should contain: 
  - Account properties (number, balance, interest rate, account type).  
  - The list of transactions performed.  

Behavior: 

- On startup, the `Bank` should scan a data directory for account files and reconstruct accounts with their data.  
- When the user exits the account menu after performing transactions, save the updated account data back to its file.  

***

# Object-Oriented Design
![ATM Simulator Class Diagram](https://github.com/user-attachments/assets/3db68339-5a8e-4e2c-892b-167fc108ed07)

![ATM Simulator Start Behaviour](https://github.com/user-attachments/assets/2eed9903-e914-464f-81e3-e25734bf04f8)

![ATM Simulator Run Behaviour](https://github.com/user-attachments/assets/528ca2d6-31a7-4ba0-bf27-f0131fbba171)
