# How to choose a database?

I am not a DBA. I am a software engineer writing apps. When I start to research which is a good database for my app, I found very limited resources on that. So I decide to write this. Hope this can help more software engineers to choose the proper database for their apps.

RDBMS

I will start with RDBMS. This is the basic one. Without knowing whether there exists a particular database that is suitable for your app, use RDBMS. RDBMS should work for most of the apps, though it might not be the optimal solution. 

Basically, RDBMS is organized and viewed as a table. For other databases that I want to talk about, their views are not table like. So this is a major attribute when you compare RDBMS to the other database offerings. 

Beacuse it is a table, it is optimzed for the following generic operations: Query/Update a few of the rows in a table with indexes, and you also can easily read/write any columns that you want. You can see that RDBMS is optimized for these two things: row and column. So that is why it is suitable for most of the application. But remember, it is not super optimized for row only, or column only. We will talk about other database offerings if you want to optimize more on one of them, with the trade off to optimize less on the other.

Note that it is now in the cloud computing age, you really should move your apps into the cloud space. So you don't really need to install and maintain a database on a server by yourself. Find a managed database that can be scaled well. In this way, you can also easily to write apps with serverless concept. 



