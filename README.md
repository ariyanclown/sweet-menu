import pandas as pd
import matplotlib.pyplot as plt
b=pd.read_csv(r"E:\Download\menu.csv",index_col=['Codeno'])
def table():
    print(b)

def add():
    while True:
      Codeno=int(input("Enter code no "))
      Item=input("Enter Item ")
      Amount=int(input("Enter Amount "))
      Quantity=int(input('Enter Quantity '))
      b.loc[Codeno]=[Item,Amount,Quantity]
      b.to_csv(r"E:\Download\menu.csv")
      print("1 record inserted")
      new_rec=input("Do You Wants To Enter Another Records (Y/N).... ")
      if new_rec=='N' or new_rec=='n':
           break

def remove():
    Codeno=int(input("Enter Code no To Delete "))
    b.drop([Codeno],axis=0,inplace=True)
    b.to_csv(r"E:\Download\menu.csv")

def update():
    Codeno=int(input('Enter Code no in which changes are required '))
    Item=input("Enter New Item ")
    Amount=int(input("Enter New Amount "))
    Quantity=input("Enter New Quantity ")
    b.loc[Codeno]=[Item,Amount,Quantity]
    b.to_csv(r"E:\Download\menu.csv")

def search():
    a=int(input('Enter Sweet code no to be searched '))
    print()
    print(b.loc[a])
    print()

def chart():
    plt.bar(b['Item'],b['Amount'])
    plt.title("Rate List of Sweets")
    plt.show()

a=True
while a:
    print()
    print()
    print('*'*20)
    print('Sweets shop menu')
    print('*'*20)
    print('1: Show Data')
    print('2: Add Data')
    print('3: Remove Data')
    print('4: Update Data')
    print('5: Search for Sweet')
    print('6: Show chart of Sweets')
    print('7: Exit Shop')
    choice=input('Choose fromm (1-7): ')
    print()
    print()
    if choice=='1':
        table()
    elif choice=='2':
        add()
    elif choice=='3':
        remove()
    elif choice=='4':
        update()
    elif choice=='5':
        search()
    elif choice=='6':
        chart()
    elif choice=='7':
        a=False
    else:
        print('That is not a valid choice')
print('Come back soon')
