---
title: "Exempel 1 (Bankapplikation)"
date: 2024-09-10T08:00:00Z
draft: false
weight: 100
---
Detta är ett exempel baserat på en simpel version av en bankapplikation med fokus på objektorientering.
- Bankkonto har ett kontonummer och saldo
    - Man kan sätta in pengar (skapa)
    - Man kan ta ut pengar, med kontroll av saldo
- Bank hanterar bankkonton
    - Man kan hämta ett konto baserat på kontonummer
    - Man kan skapa nya konton
    - Man kan flytta pengar mellan två konton

Detta blir indelat i två egna objekt, och sedan en del i `Program.cs` som ger användaren en meny att interagera med.

# `BankAccount.cs`
```csharp
internal class BankAccount
{
    public string accountNumber;
    public float balance;

    public BankAccount(string number, float balance)
    {
        accountNumber = number;
        this.balance = balance;
    }

    public void Deposit(float amount)
    {
        balance += amount;
    }

    public bool Withdraw(float amount)
    {
        if (balance >= amount)
        {
            balance -= amount;
            return true;
        }

        return false;
    }
}
```
# `Bank.cs`
```csharp
internal class Bank
{
    List<BankAccount> accounts = new List<BankAccount>();
    Random accountNumberGenerator = new Random();

    public void CreateAccount()
    {
        // Genererar ett slumpmässigt kontonummer
        string accountNumber = accountNumberGenerator.Next(1000, 9999).ToString();

        // Skapa ett nytt bankkonto och förvara det i listan
        accounts.Add(new BankAccount(accountNumber, 0));

        // Informera användaren om vad kontot har fått för nummer
        Console.WriteLine($"Created an account with number: {accountNumber}");
    }

    // Denna metod gör det möjligt att överföra mellan två
    // olika konton. Den använder sig av de inbyggda
    // metoderna som finns i BankAccount.cs
    public void TransferBetweenAccounts(string transfererAccount, string transfereeAccount)
    {
        // Hämtar ett potentiellt bankkonto baserat på
        // villkoret att kontonummer stämmer mot det
        // användaren har skrivit in.
        BankAccount? transferer = accounts.FirstOrDefault(a => a.accountNumber == transfererAccount);
        BankAccount? transferee = accounts.FirstOrDefault(a => a.accountNumber == transfereeAccount);

        // Ifall båda de efterfrågare kontonen har hämtats
        if(transferer != null && transferee != null)
        {
            Console.Write("Amount to transfer: ");
            float transferAmount = float.Parse(Console.ReadLine());

            if(transferer.Withdraw(transferAmount) == true)
            {
                transferee.Deposit(transferAmount);
                Console.WriteLine($"Transfered {transferAmount} from {transferer.accountNumber} to {transferee.accountNumber}");
            }
            else
            {
                Console.WriteLine($"Could not withdraw {transferAmount} from {transferer.accountNumber}");
            }
        }
        // Detta händer ifall man skrivit in felaktigt eller
        // kontonummer som inte existerar.
        else
        {
            Console.WriteLine("Could not find one of the accounts");
        }
    }

    // Hämtar ett konto baserat på ett kontonummer
    // Kan potentiellt vara null
    public BankAccount? GetAccount(string number)
    {
        return accounts.FirstOrDefault(a => a.accountNumber == number);
    }
}
```

# `Program.cs`
```csharp
// Skapa en bank som ansvarar för alla konton
Bank exempelBank = new Bank();

bool isRunning = true;
while(isRunning)
{
    Console.WriteLine("1. Deposit\n2. Withdraw\n3.Transfer\n4. Create Account\nQ. Quit");
    ConsoleKeyInfo key = Console.ReadKey();

    if(key.Key == ConsoleKey.D1)
    {
        Console.Write("Write account number ");
        string num = Console.ReadLine();

        // Hämtar kontot för att göra en insättning av 100
        exempelBank.GetAccount(num)?.Deposit(100);
    }
    else if(key.Key == ConsoleKey.D2)
    {
        Console.Write("Write account number ");
        string num = Console.ReadLine();

        // Hämtar kontot för att göra ett uttag av 100
        exempelBank.GetAccount(num)?.Withdraw(100);
    }
    else if (key.Key == ConsoleKey.D3)
    {
        Console.Write("Write sender number ");
        string acc1 = Console.ReadLine();
        Console.Write("Write recipient number ");
        string acc2 = Console.ReadLine();

        // Tar emot två olika kontonummer och sedan skickar
        // vidare till banken för att hantera överföringen
        exempelBank.TransferBetweenAccounts(acc1, acc2);
    }
    else if(key.Key == ConsoleKey.D4)
    {
        // Skapar ett konto åt användaren hos banken
        exempelBank.CreateAccount();
    }
    else if(key.Key == ConsoleKey.Q)
    {
        Console.WriteLine("Exiting.");
        isRunning = false;
    }
}
```