---
layout: post
title: Using SQLite with Python
categories: ['data analysis']
tags: ['python', 'sqlite']
---

A SQLite database is perfect for projects where you want a small portable file.  I find it has three big advantages over other database, which using it in this regard.  First, it comes with the Python distribution so you don't need to install or configure any addtional software.  Second, the entire databae is stored in a single file making cloud storage super easy.  And third, there is a light weight GUI plugin for Firefox called SQLite Manager which you can use to create, update, and delete tables. 

To create a database all you need to do is connect to a file path, and if it doesn't exist Python will create the database file.  How much easier could that be?

The only part that I've struggled with is creating multiple fields from the command which I can't seem to figure out how to do.  However, a quick and easy workaround for this is to use the Firefox GUI to create the fields, which for ad hoc setup isn't that bad.

### Create a Database

First, I should note that while you can put any data into the database, according to the documents the supported data filed types are INTEGER, REAL (aka floating value), TEXT, BLOB (for storing binary data), and NULL.

```python
import sqlite3

sqlite_file_path = 'c:/Users/Curious/Documents/db_example.sqlite'  
table_name = 'sample_table'  
new_field = 'user_name'
field_type = 'TEXT'

# Connect to the database file
conn = sqlite3.connect(sqlite_file_path)
c = conn.cursor()

c.execute("ALTER TABLE {tn} ADD COLUMNN '{nf}' {ft}".format(tn=table_name, nf=new_field, ft=field_type))

# Committing changes and closing the connection to the database file
conn.commit()
conn.close()
```

That's it, you've now created a new database file with a table named sample_table and a text field labeled user_name.  If you want to write data to this table you would use the same construct, just change the `c.execute()` function to pass a simple SQL statement.  Just remember to include the `conn.commit()` function otherwise it will not update the database.  

### Retrive Data

Getting data out of the database is just as easy as putting it in.  The only difference here is we're going to use a c.fecthall() function to get the data, instead of a conn.commit() function to write the data.

```python
import sqlite3

sqlite_file_path = 'c:/Users/Curious/Documents/db_example.sqlite'  
table_name = 'sample_table'  

# Connect to the database file
conn = sqlite3.connect(sqlite_file_path)
c = conn.cursor()

c.execute("SELECT * FROM table_name")
results = c.fecthall()

conn.close()
```

Once this runs all of the data will be stored in the results variable from which you can extract it from.