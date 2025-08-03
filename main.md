#include <iostream>
using namespace std;
class ATM {
private:
    double balance;
public:
    ATM() : balance(0.0) {}
    void deposit(double amount) {
        if (amount > 0) {
            balance += amount;
            cout << "Deposited: $" << amount << endl;
        } else {
            cout << "Invalid deposit amount." << endl;
        }
    }
    void withdraw(double amount) {
        if (amount > 0 && amount <= balance) {
            balance -= amount;
            cout << "Withdrew: $" << amount << endl;
        } else {
            cout << "Invalid withdrawal amount." << endl;
        }
    }
    void checkBalance() const {
        cout << "Current balance: $" << balance << endl;
    }
};
class ATMController {
private:
    ATM atm;
public:
    void start() {
        int choice;
        double amount;
        do {
            cout << "\nATM Menu:\n";
            cout << "1. Deposit\n";
            cout << "2. Withdraw\n";
            cout << "3. Check Balance\n";
            cout << "4. Exit\n";
            cout << "Choose an option: ";
            cin >> choice;
            switch (choice) {
                case 1:
                    cout << "Enter amount to deposit: ";
                    cin >> amount;
                    atm.deposit(amount);
                    break;
                case 2:
                    cout << "Enter amount to withdraw: ";
                    cin >> amount;
                    atm.withdraw(amount);
                    break;
                case 3:
                    atm.checkBalance();
                    break;
                case 4:
                    cout << "Exiting...\n";
                    break;
                default:
                    cout << "Invalid choice. Please try again.\n";
            }
        } while (choice != 4);
    }
};
int main() {
    ATMController controller;
    controller.start();
    return 0;
}
