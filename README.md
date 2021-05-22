# How to choose a database?

I am not a DBA. I am a software engineer writing apps. When I start to research which is a good database for my app, I found very limited resources on that. So I decide to write this. Hope this can help more software engineers to choose the proper database for their apps.

RDBMS

I will start with RDBMS. This is the basic one. Without knowing whether there exists a particular database that is suitable for your app, use RDBMS. RDBMS should work for most of the apps, though it might not be the optimal solution. 

Basically, RDBMS is organized and viewed as a table. For other databases that I want to talk about, their views are not table like. So this is a major attribute when you compare RDBMS to the other database offerings. 

Beacuse it is a table, it is optimzed for the following generic operations: Query/Update a few of the rows in a table with indexes, and you also can easily read/write any columns that you want. You can see that RDBMS is optimized for these two things: row and column. So that is why it is suitable for most of the application. But remember, it is not super optimized for row only, or column only. We will talk about other database offerings if you want to optimize more on one of them, with the trade off to optimize less on the other.

Note that it is now in the cloud computing age, you really should move your apps into the cloud space. So you don't really need to install and maintain a database on a server by yourself. Find a managed database that can be scaled well. In this way, you can also easily to write apps with serverless concept. 

DocumentDB/NoSQL

Now I want to move to the next popular database, called DocumentDB. When people talks about NoSQL, it is most likely DocumentDB. 

Basically, DocumentDB tries to solve one issue in RDBMS: you want flexible columns in a row. Thinking of a user profile, which might have lots of attributes. But for a particular user, it may only have a few of them. In this case, if you use RDBMS columns to store each of the attributes, you are wasting a lof ot storage room for the empty fields. Remember that RDBMS is normally stored row by row in a file, and the space of each row is not sizeable, because otherwise you have to re-write the remaining file to update a row. So the RDBMS columns are fixed length, and you have to reserve the space of all columns even if it is empty.

In DocumentDB, each row is stored in a file, which allows a flexible row size. You don't have to reserve space for a column that is not used.

However, when you want to update a column in a row file, you have to read the whole file, update it, and write the whole file back. So the file itself cannot be very large. Compare this with the RDBMS, RDBMS can find the column location in a row on the disk, and update only that part of the file, without reading/writing the whole file.

ColumnDB

Now we move on to the next type of database: ColumnDB. 

In most of the applications, you will generally query a row. For example, find a particluar user from a user table, so it makes sense that data is stored row by row.

But consider if you have a table that stores stock price data. The data has columns on date, symbol, open, close, high, low, volume. Your most used query is to return historical close price for a particular symbol. In such cases, it makes more sense that data is stored by column in a data file.

ColumnDB is exactly designed for this purpose. You can have a lot of columns. But your most query only need to return one or a few columns on many rows for a particular tag ( stock symbol in the above example). ColumnDB makes this super fast as you are continously read from disk, instead of reading rows randomly on a disk like RDBMS.

Key-value store

When you want super fast query, you may thinking of key-store store in memory. It is a hash table in memory, which gives you the value of a given key. It is designed for speed.







