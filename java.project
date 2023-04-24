import java.util.ArrayList;
import java.util.Scanner;

public class BankManagementSystem {

    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        Bank bank = new Bank();

        int choice;
        do {
            System.out.println("Enter your choice: ");
            System.out.println("--------------------");
            System.out.println("1. Create Account");
            System.out.println("2. Deposit");
            System.out.println("3. Withdraw");
            System.out.println("4. Transfer");
            System.out.println("5. Check Balance");
            System.out.println("6. Show All Accounts");
            System.out.println("0. Exit");
            System.out.println("--------------------");
         
            choice = scanner.nextInt();

            switch (choice) {
                case 1:
                    // create a new bank account
                    System.out.print("Enter your name: ");
                    String name = scanner.next();
                    System.out.print("Enter your initial balance: ");
                    double balance = scanner.nextDouble();
                    bank.createAccount(name, balance);
                    System.out.println("\n------------------------------");
                    System.out.println("Account created successfully!");
                    System.out.println("------------------------------");
                    break;
                case 2:
                    // deposit money into an account
                    System.out.print("Enter your account number: ");
                    int accountNumber = scanner.nextInt();
                    System.out.print("Enter the amount to deposit: ");
                    double amount = scanner.nextDouble();
                    boolean depositResult = bank.deposit(accountNumber, amount);
                    if (depositResult) {
                        System.out.println("\n----------------------");
                        System.out.println("Deposit successful!");
                        System.out.println("----------------------");
                    } else {
                        System.out.println("\n--------------------");
                        System.out.println("Account not found!");
                        System.out.println("---------------------");
                    }
                    break;
                case 3:
                    // withdraw money from an account
                    System.out.print("Enter your account number: ");
                    accountNumber = scanner.nextInt();
                    System.out.print("Enter the amount to withdraw: ");
                    amount = scanner.nextDouble();
                    boolean withdrawResult = bank.withdraw(accountNumber, amount);
                    if (withdrawResult) {
                        System.out.println("\n-----------------------");
                        System.out.println("Withdrawal successful!");
                        System.out.println("------------------------");
                    } else {
                        System.out.println("\n-----------------------------------------");
                        System.out.println("Account not found or insufficient funds!");
                        System.out.println("-----------------------------------------");
                    }
                    break;
                case 4:
                    // transfer money between two accounts
                    System.out.print("Enter the account number to transfer from: ");
                    int fromAccountNumber = scanner.nextInt();
                    System.out.print("Enter the account number to transfer to: ");
                    int toAccountNumber = scanner.nextInt();
                    System.out.print("Enter the amount to transfer: ");
                    amount = scanner.nextDouble();
                    boolean transferResult = bank.transfer(fromAccountNumber, toAccountNumber, amount);
                    if (transferResult) {
                        System.out.println("\n----------------------");
                        System.out.println("Transfer successful!");
                        System.out.println("----------------------");
                    } else {
                        System.out.println("\n-----------------------------------------------------");
                        System.out.println("One or both accounts not found or insufficient funds!");
                        System.out.println("------------------------------------------------------");
                    }
                    break;
                case 5:
                    // check account balance
                    System.out.print("Enter your account number: ");
                    accountNumber = scanner.nextInt();
                    double balanceResult = bank.checkBalance(accountNumber);
                    if (balanceResult != -1) {
                        System.out.println("\n------------------------------------");
                        System.out.println("Your balance is: " + balanceResult);
                        System.out.println("------------------------------------");
                    } else {
                        System.out.println("\n--------------------");
                        System.out.println("Account not found!");
                        System.out.println("---------------------");
                    }
                    break;
                case 6:
                    // show all accounts
                    bank.showAllAccounts();
                    break;
                case 0:
                    // exit the program
                    System.out.println("\n-----------");
                    System.out.println("Goodbye!");
                    System.out.println("-----------");
                    break;
                default:
                    System.out.println("\n-----------------------------------");
                    System.out.println("Invalid choice. Please try again.");
                    System.out.println("-----------------------------------");
                    break;
            }
        } while (choice != 0);

        scanner.close();
    }

}

class Bank {
    private ArrayList<BankAccount> accounts;

public Bank() {
    accounts = new ArrayList<>();
}

public void createAccount(String name, double balance) {
    BankAccount account = new BankAccount(name, balance);
    accounts.add(account);
}

public boolean deposit(int accountNumber, double amount) {
    BankAccount account = findAccount(accountNumber);
    if (account != null) {
        account.deposit(amount);
        return true;
    } else {
        return false;
    }
}

public boolean withdraw(int accountNumber, double amount) {
    BankAccount account = findAccount(accountNumber);
    if (account != null && account.getBalance() >= amount) {
        account.withdraw(amount);
        return true;
    } else {
        return false;
    }
}

public boolean transfer(int fromAccountNumber, int toAccountNumber, double amount) {
    BankAccount fromAccount = findAccount(fromAccountNumber);
    BankAccount toAccount = findAccount(toAccountNumber);
    if (fromAccount != null && toAccount != null && fromAccount.getBalance() >= amount) {
        fromAccount.withdraw(amount);
        toAccount.deposit(amount);
        return true;
    } else {
        return false;
    }
}

public double checkBalance(int accountNumber) {
    BankAccount account = findAccount(accountNumber);
    if (account != null) {
        return account.getBalance();
    } else {
        return -1;
    }
}

public void showAllAccounts() {
    if (accounts.size() == 0) {
        System.out.println("No accounts found!");
    } else {
        for (BankAccount account : accounts) {
            System.out.println(account);
        }
    }
}

private BankAccount findAccount(int accountNumber) {
    for (BankAccount account : accounts) {
        if (account.getAccountNumber() == accountNumber) {
            return account;
        }
    }
    return null;
}
}
class BankAccount {
    private static int nextAccountNumber = 1;

private int accountNumber;
private String name;
private double balance;

public BankAccount(String name, double balance) {
    this.accountNumber = nextAccountNumber++;
    this.name = name;
    this.balance = balance;
}

public int getAccountNumber() {
    return accountNumber;
}

public String getName() {
    return name;
}

public double getBalance() {
    return balance;
}

public void deposit(double amount) {
    balance += amount;
}

public void withdraw(double amount) {
    balance -= amount;
}

@Override
public String toString() {
    return "Account Number: " + accountNumber + "\nName: " + name + "\nBalance: " + balance + "\n";
}
}
