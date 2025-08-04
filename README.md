# create bank account programe
import time
    
class BankChatBot:
    user_input = input('You ').lower()
    def __init__(self):
        self.balance = 0
        self.name = 'Utsav Sharma'
        self.account_number = '123456789'
        self.IFSC_Code = 'ABC968949'
        self.account_type = 'Savings'
        self.current_balance = 'current_balance'
        time.sleep(1)
        print('Hello...! Welcome to Bank Chat Bot')
        time.sleep(1)
        
    def deposit(self):
        amount=float(input('Enter amount to be deposited: '))
        self.balance += amount
        print('\nBot: Amount Deposited:',amount)
        time.sleep(2)
        
    def withdraw(self):
        amount = float(input('Enter amount to be withdrawn: '))
        if self.balance>=amount:
            self.balance-=amount
            print('\n Bot: You Withdrew:', amount)
        else:
            print('\n Insuffiecient Balance...')
            time.sleep(2)
            
    def display(self):
        print('\nBot:  Net Available Balance=',self.balance)


    def bank_details(self):
        print('\nBot: Here are your details:')
        print(f'Name: {self.name}')
        print(f'account_number: {self.account_number}')
        print(f'IFSC_Code: {self.IFSC_Code}')
        print(f'account_type: {self.account_type}')
        print(f'Current_Balance: {self.balance}')
        time.sleep(2)

# Main chat loop
account = BankChatBot()

while True:
    print("\nBot: What would you like to do? (deposit / withdraw / balance / exit/ bank details )")
    user_input = input("You: ").lower()

    if user_input == "deposit":
        account.deposit()
    elif user_input == "withdraw":
        account.withdraw()
    elif user_input == "balance":
        account.display()
    elif user_input == 'bank details':
        account.bank_details()
        time.sleep(1)
    elif user_input == "exit" or user_input == "bye":
        print("Bot: Thank you! Have a nice day.")
        break
    else:
        print("Bot: Sorry, I didn't understand that.")
