<details>
<summary>📚 Click to expand Inventory Management Code</summary>

```python
# Paste your full code here
# Inventory-Management-Program 

import json

dic = {
   'Books' : [
    {'Title':'War and Peace','Author ' : 'Leo Tolstoy','Price':120, 'Quantity':127},
    {'Title':'Ulysses','Author' : 'Thomas Moor Price','Price': 10,  'Quantity':123},
    {'Title':'Waste Land' ,'Author ' :'T.S Eliot','Price':10, 'Quantity':100 },
    {'Title':'Treasure Island' ,'Author ' : 'R.L. Stevenson','Price':13, 'Quantity':300},
    {'Title':'Time Machine','Author '  :'H.G Wells','Price':20, 'Quantity':120},
    {'Title':'The Tempest' ,'Author ' :'William Shakespeare','Price':500, 'Quantity':1200 },
    {'Title':'Romeo and Juliet' ,'Author ' :'William Shakespeare','Price':120, 'Quantity':100 },
    {'Title':'Macbeth','Author ':'William Shakespeare','Price':56, 'Quantity':250 },
    {'Title':'The Merchant of Venice','Author '  :'William Shakespeare','Price':120, 'Quantity':100 },
    {'Title':'Mein Kamph','Author '  :'Adolf Hitler','Price':50, 'Quantity':100 },
    {'Title':'The Great Gatsby' ,'Author' :'F. Scott Fitzgerald','Price':100, 'Quantity':110 }
   ],
   'Added Books':[]
}

with open("inventory.txt",'w+') as data:
    data.write(json.dumps(dic))

def add_book():
    while 1: 
        title_book = input('Enter the title of the book:') 
        author_book = input('Enter author of book:') 
        quantity_book = int(input('Enter the quantity of book:')) 
        price_book = int(input('Enter the price of book')) 
        num1 = input('To stop the loop...write stop, otherwise ignore it:\n')
        if num1.lower() == 'stop':
            print('Loop stopped') 
            break
        elif num1 != 'stop':
            continue
        else: 
            print(f'You entered {num1}')
    
    key_value = {
        'Title of book': title_book, 
        'Author of book': author_book,
        'Quantity': quantity_book,
        'Price': price_book
    }
    
    dic['Added Books'].append(key_value) 
    print(dic)
    return dic

def del_book():
    del1 = int(input("To remove any book enter 1, or to remove whole data enter 2:"))
    print('You entered:', del1) 
    book = int(input('Enter the book number to delete:'))
    remove_books = dic['Books']
    new_remove = dic['Added Books']
    
    if del1 == 1:
        if 1 <= book <= len(remove_books):
            remove_books.pop(book - 1)
        else:
            print('Invalid book number!')
    elif del1 == 2:
        dic.clear()
    else:
        print('Enter a valid number!')
    
    print("After Deletion....\nUpdated Data:", dic)
    return dic

def sale_transaction():
    num11 = int(input("Enter the book's indexing: "))
    if num11 > 0:
        data = dic['Books']
        piece = int(input(f"How many copies of {data[num11]['Title']} would you like? : "))
        print(data[num11])
        total = piece * data[num11]['Price']
        print(f"The price of one book is ${data[num11]['Price']}. Total price is ${total}")

def total_cost():    
    book = dic['Books']
    total_quantity = 0 
    total_price = 0
    for j in book:
        total_price += j['Price'] * j['Quantity']
        total_quantity += j['Quantity']
    print('The total quantity of books is:', total_quantity)
    print('The total price of inventory is: $', total_price)

def greet():
    name = input("Enter your name: ")
    print(f"""Welcome to my store, {name}!
Choose an option:
1 -> View store
2 -> Add item
3 -> Delete item
4 -> Make purchase""")
    
    num = int(input('Enter a number:'))
    count = 1

    if num == 1:
        for key, value in dic.items():
            print(f"\nCategory: {key}")
            for items in value:
                print(f"Book indexing {count}: {items}")
                count += 1
        total_cost()

    elif num == 2:
        add_book()

    elif num == 3:
        for key, value in dic.items():
            print(f"\nCategory: {key}")
            for items in value:
                print(f"{count}: {items}")
                count += 1
        del_book()

    elif num == 4:
        for key, value in dic.items():
            print(f"\nCategory: {key}")
            for items in value:
                print(f"Book indexing {count}: {items}")
                count += 1
        sale_transaction()

greet()

# etc.
