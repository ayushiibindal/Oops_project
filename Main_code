#include<iostream>
#include<fstream>
#include<vector>
using namespace std;

class Account{
private:
    int accountNumber;
    string name;
    double balance;
public:
    Account(int accNum, string accName, double initialBalance = 0.0)
        : accountNumber(accNum), name(accName), balance(initialBalance) {}
        
    void deposit(double amount) {
        balance += amount;
    }
    void withdraw(double amount) {
        if (amount <= balance) {
            balance -= amount;
        } else {
            cout << "Insufficient funds!" << endl;
        }
    }
    void displayAccount() const {
        cout << "Account Number : " << accountNumber
                  << "\nAccount Holder : " << name
                  << "\nBalance : $" << balance << "\n";
    }
    int getAccountNumber() const { return accountNumber; }
    double getBalance() const { return balance; }
};

class BankingSystem{
private:
    vector<Account> accounts;
    int generateAccountNumber() {
        return accounts.size() + 1;
    }
public:
    void createAccount(string name, double initialBalance = 0.0) {
        int accNum = generateAccountNumber();
        accounts.push_back(Account(accNum, name, initialBalance));
        cout << "Account created with account number : " << accNum << endl;
    }
    void deposit(int accountNumber, double amount) {
        for (auto &acc : accounts) {
            if (acc.getAccountNumber() == accountNumber) {
                acc.deposit(amount);
                cout << "Deposited $" << amount << " to account number " << accountNumber << endl;
                return;
            }
        }
        cout << "Account not found." << endl;
    }
    void withdraw(int accountNumber, double amount) {
        for (auto &acc : accounts) {
            if (acc.getAccountNumber() == accountNumber) {
                acc.withdraw(amount);
                cout << "Withdrew $" << amount << " from account number " << accountNumber << endl;
                return;
            }
        }
        cout << "Account not found." << endl;
    }
    void displayAccountDetails(int accountNumber) const {
        for (const auto &acc : accounts) {
            if (acc.getAccountNumber() == accountNumber) {
                acc.displayAccount();
                return;
            }
        }
        cout << "Account not found." << endl;
    }
    void listAccounts() const {
        for (const auto &acc : accounts) {
            acc.displayAccount();
            cout << "---------------------\n";
        }
    }
};

int main() {
    BankingSystem bank;
    int choice;
    string name;
    double amount;
    int accountNumber;

    while (true) {
        cout << "\nBanking Management System\n1. Create Account\n2. Deposit\n3. Withdraw\n4. Account Details\n5. List All Accounts\n6. Exit\nChoose an option : ";
        cin >> choice;

        switch (choice) {
            case 1:
                cout << "Enter name for new account : ";
                cin >> name;
                cout << "Enter initial deposit : ";
                cin >> amount;
                bank.createAccount(name, amount);
                break;
            case 2:
                cout << "Enter account number : ";
                cin >> accountNumber;
                cout << "Enter amount to deposit : ";
                cin >> amount;
                bank.deposit(accountNumber, amount);
                break;
            case 3:
                cout << "Enter account number : ";
                cin >> accountNumber;
                cout << "Enter amount to withdraw : ";
                cin >> amount;
                bank.withdraw(accountNumber, amount);
                break;
            case 4:
                cout << "Enter account number : ";
                cin >> accountNumber;
                bank.displayAccountDetails(accountNumber);
                break;
            case 5:
                bank.listAccounts();
                break;
            case 6:
                cout<<"-------THANKYOU-------";
                return 0;
            default:
                cout << "Invalid option! Try again." << endl;
        }
    }
}
