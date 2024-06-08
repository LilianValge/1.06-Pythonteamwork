# 1.06-Pythonteamwork

Transforming this Python code to Java

```py
import datetime 

class Client: #class 1 - class is a DNA, methods are what class can do. contstuctor - special method.
  number_of_clients = 0

  def __init__(self, id, name): 
    self.id = id
    self.name = name
    self.accounts = []
    Client.number_of_clients += 1 #increasing by one

#adding an account to a client
  def add_account(self, account):
    self.accounts.append(account)

class Account:
  def __init__(self, number, currency, balance = 0.0):
    self.number = number
    self.currency = currency
    self.balance = balance
    self.transactions = []

  def make_deposit(self, amount, note):
    self.transactions.append(Transaction(self.currency, amount, note))
    self.balance += amount

  def make_withdrawal(self, amount, note):
    self.transactions.append(Transaction(self.currency, -amount, note))
    self.balance -= amount

class Transaction:
  def __init__(self, currency, amount, note):
    self.currency = currency
    self.amount = amount
    self.note = note
    self.time_stamp = datetime.datetime.now()

# now, let us work using those classes
# adding clients to a list
clients = []
clients.append(Client('123456', 'Anna'))
clients.append(Client('987654', 'Oskar'))
clients.append(Client('456123', 'Jenifer'))

#adding accounts to clients
#clients[0] = client Anna, add.account = a method, EUR = currency, 1000 = balance
clients[0].add_account(Account('EE654987564321', 'EUR', 1000.0))
clients[0].add_account(Account('JP582147859635', 'JPY', 25000.30)) #another account for same client
clients[0].add_account(Account('US654987643214', 'USD')) #another account for same client
clients[1].add_account(Account('PL849512635445', 'PLN', 47800.00))
clients[2].add_account(Account('SE741254956587', 'SEK', 200.18))


# let's make some transactions
clients[0].accounts[0].make_deposit(1200, 'Salary')
clients[0].accounts[0].make_withdrawal(50, 'Grocery')
clients[0].accounts[0].make_withdrawal(140, 'Clothes')
clients[0].accounts[0].make_withdrawal(20, 'Dinner')

# printing some data
print(f'We have {Client.number_of_clients} clients in our bank:')

for client in clients:
  print(f'Client {client.name} has the following accounts:')
  for account in client.accounts:
    print(f'    {account.number} ({account.currency}) {account.balance}')
    for transaction in account.transactions:
      print(f'        {transaction.time_stamp} {transaction.currency} {transaction.amount}')
```

```java
import java.util.ArrayList;
import java.util.Date;
import java.text.SimpleDateFormat;

class Client {
    private static int numberOfClients = 0;
    private String id, name;
    private ArrayList<Account> accounts;

    public Client(String id, String name) {
        this.id = id;
        this.name = name;
        this.accounts = new ArrayList<>();
        numberOfClients++;
    }

    public void addAccount(Account account) {
        accounts.add(account);
    }

    public static int getNumberOfClients() {
        return numberOfClients;
    }

    public String getName() {
        return name;
    }

    public ArrayList<Account> getAccounts() {
        return accounts;
    }
}

class Account {
    private String number, currency;
    private double balance;
    private ArrayList<Transaction> transactions;

    public Account(String number, String currency, double balance) {
        this.number = number;
        this.currency = currency;
        this.balance = balance;
        this.transactions = new ArrayList<>();
    }

    public Account(String number, String currency) {
        this(number, currency, 0.0);
    }

    public void makeDeposit(double amount, String note) {
        transactions.add(new Transaction(currency, amount, note));
        balance += amount;
    }

    public void makeWithdrawal(double amount, String note) {
        transactions.add(new Transaction(currency, -amount, note));
        balance -= amount;
    }

    public String getNumber() {
        return number;
    }

    public String getCurrency() {
        return currency;
    }

    public double getBalance() {
        return balance;
    }

    public ArrayList<Transaction> getTransactions() {
        return transactions;
    }
}

class Transaction {
    private String currency, note, timeStamp;
    private double amount;

    public Transaction(String currency, double amount, String note) {
        this.currency = currency;
        this.amount = amount;
        this.note = note;
        this.timeStamp = new SimpleDateFormat("yyyy-MM-dd HH:mm:ss").format(new Date());
    }

    public String getCurrency() {
        return currency;
    }

    public double getAmount() {
        return amount;
    }

    public String getTimeStamp() {
        return timeStamp;
    }
}

public class BankSystem {
    public static void main(String[] args) {
        ArrayList<Client> clients = new ArrayList<>();

        clients.add(new Client("123456", "Anna"));
        clients.add(new Client("987654", "Oskar"));
        clients.add(new Client("456123", "Jenifer"));

        clients.get(0).addAccount(new Account("EE654987564321", "EUR", 1000.0));
        clients.get(0).addAccount(new Account("JP582147859635", "JPY", 25000.30));
        clients.get(0).addAccount(new Account("US654987643214", "USD"));
        clients.get(1).addAccount(new Account("PL849512635445", "PLN", 47800.00));
        clients.get(2).addAccount(new Account("SE741254956587", "SEK", 200.18));

        clients.get(0).getAccounts().get(0).makeDeposit(1200, "Salary");
        clients.get(0).getAccounts().get(0).makeWithdrawal(50, "Grocery");
        clients.get(0).getAccounts().get(0).makeWithdrawal(140, "Clothes");
        clients.get(0).getAccounts().get(0).makeWithdrawal(20, "Dinner");

        System.out.println("We have " + Client.getNumberOfClients() + " clients in our bank:");

        for (Client client : clients) {
            System.out.println("Client " + client.getName() + " has the following accounts:");
            for (Account account : client.getAccounts()) {
                System.out.println("    " + account.getNumber() + " (" + account.getCurrency() + ") " + account.getBalance());
                for (Transaction transaction : account.getTransactions()) {
                    System.out.println("        " + transaction.getTimeStamp() + " " + transaction.getCurrency() + " " + transaction.getAmount());
                }
            }
        }
    }
}
```
