# merchandise_sales.py

import sqlite3


class merchandise_sales:
    conn = None


# configuring database handler
try:
    conn = sqlite3.connect('test.db')
except sqlite3.Error as e:
 print("Connection Error : " + str(e))


# Insert Items
def insert_item(self):
    cur = self.conn.cursor()

item = str(input('Enter Item Name: '))
cost = int(input('Enter Item Cost: '))
merchant = int(input('Enter Merchandise ID: '))
query = "INSERT INTO item(name, costs,merchant_id)VALUES ('" + item + "', '" + str(cost) + "', '" + str(merchant) + "')"
cur.execute(query)
print('Successfully Item Saved')
db.commit()


# View ALl itesms
def view_item(self):
 cur = self.conn.cursor()


query = "SELECT * FROM item"
cur.execute(query)
rows = cur.fetchall()
print('\n************************************************************\
All Items\n')
if rows:
    for row in rows:
        print("ITEM ID = ", row[0])
print("ITEM = ", row[1])
print("ITEM = ", row[2])
print("MERCHANT ID = ", row[3], "\n")
else:
print('No Event Found')
print('\n************************************************************')
#return 0
db.commit

# Insert details about the event
def add_event(self):
    cur = self.conn.cursor()


date = str(input('Enter Item Date: '))
venue = str(input('Enter Venue:'))


query = "INSERT INTO events(dates, venue) VALUES('" + date + "', '" + venue + "')"
cur.execute(query)
#return 0
db.commit()

# Show all event
def view_event(self):
    cur = self.conn.cursor()


query = "SELECT * FROM events"
cur.execute(query)
rows = cur.fetchall()
print('\n************************************************************\
All Events\n')
if rows:
    for row in rows:
        print("EVENT ID = ", row[0])
print("Date = ", row[1])
print("Venue = ", row[2], "\n")
#else:
print('No Event Found')
print('\n************************************************************')
#return 0
db.commit()

# Add detail about sales
def add_sale(self):
 cur = self.conn.cursor()


game_id = str(input('Enter Event ID: '))
merch_id = str(input('Enter Merchandise ID: '))

# Populate the sales table
query = "INSERT INTO sales(game_id, merchant_id)VALUES ('" + game_id + "', '" + merch_id + "')"
cur.execute(query)
#return 0
db.commit()

# Show all event
def view_all_sale(self):
    cur = self.conn.cursor()


query = "SELECT * FROM sales"
cur.execute(query)
rows = cur.fetchall()
print('\n************************************************************\
All Events\n')
if rows:
    for row in rows:
        print("SALES ID = ", row[0])
print("Game ID = ", row[1])
print("MERCHANT ID = ", row[2], "\n")
else:
print('No Event Found')
print('\n************************************************************')
#return 0
db.commit()

# Add detail about sales by Game ID and merchant id
def view_sale(self):
 cur = self.conn.cursor()

# Taking inputs from users
gameID = str(input('Enter Game ID: '))
merch_id = str(input('Enter Merchandise ID: '))

#Retrieving data from the sales table
query = "SELECT game_id, merchant_id, COUNT(game_id) FROM sales\
WHERE game_id = " + gameID + " AND merchant_id = " + merch_id + " GROUP BY game_id,merchant_id"
cur.execute(query)
rows = cur.fetchall()

print('\n************************************************************\
Sale\n')
if rows:
    for row in rows:
        print("GAME ID = ", row[0])
print("MERCHANT ID = ", row[1])
print("ITEM SOLD = ", row[2], "\n")
else:
print('No Sale has found')
print('\n************************************************************')
db.commit()

app = merchandise_sales()
print(
    "1. Add Items\n2. View All Items\n3. Add Events\n4. View All Events\n5. Add Sales\n6. View All Sales\n7. View Sales and Item Sold")
choice = int(input('Enter Your Choice: '))

if choice == 1:
    app.insert_item()
elif choice == 2:
    app.view_item()
elif choice == 3:
 app.add_event()
elif choice == 4:
 app.view_event()
elif choice == 5:
 app.add_sale()
elif choice == 6:
 app.view_all_sale()
elif choice == 7:
 app.view_sale()
else:
 print('Wrong Input')
