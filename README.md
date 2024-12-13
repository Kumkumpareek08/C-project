# Bank Account Management System

#include <iostream.h> #include <conio.h> #include <string.h> #include <process.h>
void delay(unsigned int milliseconds) {
for (unsigned int i = 0; i < milliseconds * 100; i++) {
// Empty loop to simulate delay }
}
char usrname[10]; char passwd[10];
class Account { protected:
int accountNumber; char name[30]; double balance;
public:
Account(int accNo, const char* accName, double initialBalance); void display();
void deposit(double amount);
void withdraw(double amount);
};
VII.       
   // Constructor implementation
Account::Account(int accNo, const char* accName, double initialBalance) {
accountNumber = accNo; strcpy(name, accName); balance = initialBalance;
}
// Function to display account details void Account::display() {
cout << "\n\t\tAccount Number: " << accountNumber; cout << "\n\t\tAccount Holder: " << name;
cout << "\n\t\tBalance: " << balance << endl;
}
// Function to deposit money
void Account::deposit(double amount) {
balance += amount;
cout << "\n\t\tAmount Deposited: " << amount; cout << "\n\t\tNew Balance: " << balance << endl;
}
// Function to withdraw money
void Account::withdraw(double amount) {
if (amount > balance) {
cout << "\n\t\tInsufficient Balance!" << endl;
} else {
balance -= amount;
cout << "\n\t\tAmount Withdrawn: " << amount;
cout << "\n\t\tRemaining Balance: " << balance << endl;
} }
class Bank { private:
Account* account;
public:
Bank() : account(NULL) {} void createAccount(); void manageAccount();
};
// Function to create an account void Bank::createAccount() {
int accountNumber; char name[30]; double initialBalance;     
   cout << "\n\t\tEnter Account Number: ";
cin >> accountNumber;
cout << "\n\t\tEnter Account Holder Name: "; cin >> name;
cout << "\n\t\tEnter Initial Balance: ";
cin >> initialBalance;
account = new Account(accountNumber, name, initialBalance);
cout << "\n\t\tAccount Longin Successfully!"; }
// Function to manage an account void Bank::manageAccount() {
if (account == NULL) {
cout << "\n\t\tNo account created yet!"; return;
}
int choice; double amount; do {
clrscr();
cout << "\n\n\t\t********** Bank Account Management System **********"; cout << "\n\t\t1. Deposit Money";
cout << "\n\t\t2. Withdraw Money";
cout << "\n\t\t3. Display Account Details";
cout << "\n\t\t4. Exit";
cout << "\n\t\tEnter Your Choice: ";
cin >> choice;
switch (choice) { case 1:
cout << "\n\t\tEnter amount to deposit: "; cin >> amount; account->deposit(amount);
break;
case 2:
cout << "\n\t\tEnter amount to withdraw: "; cin >> amount; account->withdraw(amount);
break;
case 3: account->display();
break; case 4:
cout << "\n\t\tLogging out..."; break;
   default:
cout << "\n\t\tInvalid Choice!";
} getch();
} while (choice != 4); }
void login() {
int flag1 = 0, flag2 = 0;
cout << "\n\t\t\t**************************************"; cout << "\n\t\t\t Bank Account Management System ";
cout << "\n\t\t\t**************************************"; cout << "\n\t\t\tUsername: ";
cin >> usrname;
cout << "\n\t\t\tPassword: ";
cin >> passwd;
flag1 = strcmp(usrname, "admin"); flag2 = strcmp(passwd, "admin");
if (flag1 == 0 && flag2 == 0) {
cout << "\n\t\t* ---------------- *";
cout << "\n\t\tLogin Successful!\n"; cout << "\n\t\t* ---------------- *" << endl; getch();
} else {
cout << "\n\n\t\tIncorrect Username or Password. Try Again .."; getch();
clrscr();
login();
} }
void main() { clrscr();
login();
Bank bank;
int menuChoice; do {
clrscr();
cout << "\n\n\t\t********** Bank Account Management System **********"; cout << "\n\t\t1. Create Account";
cout << "\n\t\t2. Manage Account";
cout << "\n\t\t3. Logout";
cout << "\n\t\tEnter Your Choice: ";
cin >> menuChoice;        
   switch (menuChoice) { case 1:
bank.createAccount(); getch();
break;
case 2: bank.manageAccount(); getch();
break;
case 3:
cout << "\n\t\tExiting..."; break;
default:
cout << "\n\t\tInvalid Choice!"; getch();
}
} while (menuChoice != 3);
}
