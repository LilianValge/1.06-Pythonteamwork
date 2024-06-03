# 1.06-Pythonteamwork

Transforming this Pythoncode to Java

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
import java.time;
import java.util.ArrayList;
import java.util.List;

public class Main {
    public static void main(String[] args) {

class Client {
    static int numberOfClients = 0;
    private String id; //  OR SHOUD WE PUT INTEGER???????
    private String name;
    private List<Account> accounts;

    public Client(String id, String name) { // OR INTEGER???
        this.id = id;
        this.name = name;
        this.accounts = new ArrayList<>();
        numberOfClients++;
    }

class Account {
    private String number;
    private String currency;
    private double balance;
    private List<Transaction> transactions;

    public Account(String number, String currency, double balance) {
        this.number = number;
        this.currency = currency;
        this.balance = balance;
        this.transactions = new ArrayList<>();
    }

class Transaction {
    private String currency;
    private double amount;
    private String note;
    private Date timeStamp;

    public Transaction(String currency, double amount, String note) {
        this.currency = currency;
        this.amount = amount;
        this.note = note;
        this.timeStamp = new Date();
    }
```
