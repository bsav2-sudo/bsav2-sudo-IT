# 2. Databases - SQL Databases

![Sql_data_base_with_logo svg](https://github.com/user-attachments/assets/4f4b3513-63b5-4c58-b611-91c31fb05673)

### Skills Utilised

<code>Querying</code> <code>Database Management</code> <code>SQL</code> <code>Server and Client</code> <code>Data Management</code> <code>IT Security</code>

## Overview

While looking into Cybersecurity and developing my role as an IT Technician - one of the subjects that always keeps coming up is Databases. They're the backbone of corporate environments for storing data from Usernames to Customer Databases. For me this is an area that I am very new to as I have not dealt with using databases until coming into my IT role where I now find myself surrounded by databases full of data that end users access on a daily basis in order to complete their tasks. From my look into cybersecurity - the one thing I always see is vulnerabilities in SQL servers such as easily-guessed passwords or the server version has been updated to support the latest patches.

So to get started in my journey at looking at databases - it only felt right that I started with SQL and learnt how to use SQL queries and commands to build a database as well as learning about some of the features of mySQL. Without further ado - time to get this started.

## Blog Entry - 04/02/25

## Downloading mySQL 

I chose to go with mySQL for this project as when researching SQL databases that I could use I found it to be the most reliable SQL database and is also open-source which is always something I like. So I got started by heading to the mySQL website ([mySQL Homepage](https://www.mysql.com/)) and downloading the latest mySQL Community Version. Once downloaded and installed I can set what I want to install - in this case I went for everything including the mySQL Workbench and the mySQL Command Line Client - just so I can get a feel for how both interfaces work with SQL.

And now I have it installed and of course setting a password...

<img width="1439" alt="MySQL Running - CMD" src="https://github.com/user-attachments/assets/b47fbbfb-de21-44b3-8888-dbc17d51f181" />

Tah Dah! Successfully got mySQL running and as you can see I decided to go for a Command Line Interface - can never beat a good CLI. If I run the <code>status</code> command in the CLI - this will show me the status of the SQL server and whether the CLI Client is connected to the server or not.

<img width="866" alt="MySQL Server Status - CMD" src="https://github.com/user-attachments/assets/7ea5547e-190e-4bca-a5e7-a96bc42f6397" />

Cool we are connected to the server - I'm also going to run one more command to check that everything is how I expect it to be in this install - <code>show databases;</code> does what it says on the tin and lets me look at the databases that are on the server - should only see 4 as I haven't done anything yet.

<img width="860" alt="MySQL Show Databases - CMD" src="https://github.com/user-attachments/assets/52d58a87-9e30-4cec-81c5-b2b08ce3892b" />

Wahey all sorted! This is where I'll end it today but tomorrow I'll look at the basic commands in SQL to get a good starting basis.

## Blog Entry - 05/02/2025

## Getting a Sample Database

Okay now for the nitty gritty with SQL and getting started with commands in SQL. But first I need a database to be able to practice the commands on - luckily for me there is a really good wesbite for being able to learn about SQL and the management of mySQL (something I will be looking at later once I get my feet under the table with SQL) which is available from [mySQL Tutorial](https://www.mysqltutorial.org/). After I have downloaded the SQL practice database from the site I can use the <code>source</code> command and direct it to the location of the database to add it to the server which looks a little something like this:

<img width="1439" alt="Adding a New Database" src="https://github.com/user-attachments/assets/5fa1298a-42cb-4e6a-bb62-f2476867f593" />

Now that I can see mySQL has found the database - I can confirm it has added it by running the <code>show databases;</code> command again to see the list of databases:

<img width="293" alt="New Database Shown" src="https://github.com/user-attachments/assets/492aca72-9dd4-4459-8484-a42837bd6d1c" />

Voila! Classic Models has been added and I can now query this database, so lets do that.

## Basic SQL Commands - SELECT and FROM

The SELECT commands in SQL do exactly what you would expect them to do - they select the information from where it is specified from. It is basically a way of saying I want to know about this piece of information from this database - and that is how it is used as you can see from the screenshot below:

<img width="323" alt="SELECT FROM" src="https://github.com/user-attachments/assets/e483d2d4-9320-407a-8131-0759aff3ab9f" />

So in the query above I want to know the Last Name of the Employees in the database - so I ask SQL in a Query to SELECT lastName FROM Employees which will get the Last Names from the Employee Table.

Simple when you think about it but I just want to prove it a little bit more...

<img width="1370" alt="SELECT FROM - Everything" src="https://github.com/user-attachments/assets/f9d58e1a-1f49-4984-9c3a-b2a9d63d1de4" />

The screenshot above is me querying EVERYTHING from EMPLOYEE'S table (using the * to determine everything) - and sure enough that is what is returned.

<img width="710" alt="SELECT FROM - Multiple Arguments" src="https://github.com/user-attachments/assets/4a7a4fb4-c051-4581-8d7d-7c8909275f51" />

I can also use multiple arguments in my SELECT query - so I want to know the First Name, Last Name and Job Title from the Employees Table - which again it has returned. 

Cool I'm quite happy with how this works - now to move on to one last command for today.

## ORDER

The ORDER command will let me choose the way in which the data is shown - what order is it going to be shown in. Let me run one now just to show it off a little bit...

<img width="459" alt="ORDER - By Last Name" src="https://github.com/user-attachments/assets/0fa79829-603e-4785-96f7-13902a95f10f" />

In this query I've asked SQL to do the following:

1. Select Contact Last Name and Contact First Name
2. Get this Information from Customers Table
3. Order by Contact Last Name (A->Z)

And the result is exaclty what I queried - awesome - lets run some more to see what it is doing and also get a bit more complex:

<img width="440" alt="ORDER - By Last Name DESC" src="https://github.com/user-attachments/assets/3fd3ce56-2e54-4bf3-a9bd-3b3bc4f78184" />

Same as before only this time the Last Name is in descending order (Z->A)

<img width="1439" alt="ORDER - FIELD" src="https://github.com/user-attachments/assets/0da2ebae-3166-49a5-8bc6-fc00ec238466" />

This time we've got multiple statuses that I want to order from the status collumn - SQL will do this by the first argument to the last:

1. In Process
2. On Hold
3. Cancelled
4. Resolved
5. Disputed
6. Shipped

Even thoough this is simple I love how the queries can be manipulated to be able to view the data more easily and not have to go searching for it - probably why I also like KQL from doing my Microsoft Learn training on Sentiel!

<img width="1439" alt="ORDER - By Last Name DESC and First ASC" src="https://github.com/user-attachments/assets/26117b02-c744-4bc0-b2ec-745952611e9d" />

Order by the Last Name in a Descending order and First Name in an Ascending order - yep bit of a brain teaser for me as well but looking at it in the screenshot it makes more sense.

Cool that is it for today but I'm quite happy with what I've learnt from these commands and can't wait to explore some more tomorrow.

## Blog Entry - 06/02/25

This session I want to learn some more commands I can use in SQL - just to give myself a bit more understanding of all the commands in SQL and how they can be used for multiple scenarios.

## Basic SQL Commands - AND

The and commands lets me add more arguments to an SQL Query such as I want to SELECT one table AND another - very useful instead of having to run multiple queries I can just run one, here's some examples of the AND command being used in mySQL lab:

<img width="482" alt="AND - Operator" src="https://github.com/user-attachments/assets/52136294-29d2-49ba-8f2f-c12e1e7ed5b6" />

In these query there are multiple steps:

1. SELECT Customer Name, Country and State
2. FROM Customers Table
3. WHERE the Country is USA and State is Californaia (CA)

Nice way to be able to search for something very specific within the SQL Database.

<img width="397" alt="AND - NULL" src="https://github.com/user-attachments/assets/3ec74dd3-c2a1-4675-b2e2-7b4b7116b2b5" />

The AND command can be also used for NULL values and will return the NULL values.

## Basic SQL Commands - LIMIT

The LIMIT command will let me limit the amount of results that are returned from the SQL query. Looking at the SQL query execution order that I have been able to find - I can see that the LIMIT command is the last one in the chian of command so we will get all the results from previous commands such as SELECT and FROM before it gets filtered with the LIMIT command:

<img width="414" alt="image-1-order-blog" src="https://github.com/user-attachments/assets/57a0e670-bb8b-435e-9c02-f4de53166616" />

Time to use the LIMIT within my lab:

<img width="542" alt="LIMIT" src="https://github.com/user-attachments/assets/9febe18b-359b-4c5f-84bb-6d7f39a8b3f0" />

This query gives me back the first 5 results as I have set the LIMIT argument to be 5. Nice way of being able to refine results to only lets say the first 5...

<img width="503" alt="LIMIT - Second Set of Row" src="https://github.com/user-attachments/assets/c9cd77a3-8622-409f-ba98-e84f0ca82e0e" />

This query I have set the LIMIT argument to be 10,10 which means I will get 10 rows in the first and 10 results in the second set.

## Basic SQL Commands - WHERE

The WHERE command will let me refine my SQL query to only look for specific details within a table - for example it could be I only want people named John to be in the results of the query or I only want people with the Office Codes between 1 and 5 to be returned in the results. Lets start with some of these queries and see what they look like in action:

<img width="409" alt="WHERE - BETWEEN" src="https://github.com/user-attachments/assets/f76b5031-63f8-489f-8c77-7ed71f68c4ce" />

In thsi query I have asked for the Office Codes to be between 1 and 3 where is says <code>WHERE officeCode BETWEEN 1 AND 3</code>. Cool I can already see this is going to be a really helpful command, but of course there is more ways to use it.

<img width="523" alt="WHERE - Clause" src="https://github.com/user-attachments/assets/e63a1687-6b51-4c22-8f87-981030e264c8" />

I can use it as a clause to only return on single value - in this case anyone who has the Job Title of Sales Rep.

<img width="385" alt="WHERE - Comparison Less or Equal To" src="https://github.com/user-attachments/assets/fef557f0-3581-40a5-a341-e131b23701a1" />

I can also use it with mathmatical equations such as being less than or equal to.

<img width="573" alt="WHERE - Two Clauses and ORDER" src="https://github.com/user-attachments/assets/6ca6950a-24cb-4be3-83f8-1a95bdcdeea5" />

Using two clauses to ask whether they are in Office Code 1 or have a JOb Title of Sales Rep and then Order them by Job Title.

<img width="356" alt="WHERE - Wildcard Match" src="https://github.com/user-attachments/assets/e38e7eed-c184-4129-8343-
6c93b30ce199" />

And one that I find really cool is the wildcard match - where using the argument %argument will return with ones similar as you can see from the query above!

A little cool one is being able to searhc for NULL values - quite a simple one by using the WHERE operand and then stating if something is a NULL or not NULL value as you can see from the screenshots below:

<img width="594" alt="IS NULL" src="https://github.com/user-attachments/assets/ca413176-e8f5-401f-8b6a-84ab332f7534" />

<code>Where IS NULL</code>

<img width="1439" alt="IS NOT NULL" src="https://github.com/user-attachments/assets/fa2fc887-87f5-4e4a-a774-b6404f3f0158" />
]<code>Where ISN'T NULL</code>

The final thing in the WHERE operand comes in really well is looking for values NOT BETWEEN and NOT IN a certain range of values which are shown below - very cool:

<img width="539" alt="NOT BETWEEN" src="https://github.com/user-attachments/assets/1a8d739b-ea1d-42c6-ab99-0a324825bdd6" />

<code>Values NOT BETWEEN</code>

<img width="388" alt="NOT IN" src="https://github.com/user-attachments/assets/63c808ea-aea8-4dd5-92c0-5a2f7866b141" />

<code>Values NOT IN</code>

Cool that is all for today - very happy with my progress so far and lets see what the next day brings.

## Blog Entry - 07/02/25

## Basic SQL Commands - Creating a Table

Now that I've seen how I can search SQL databases using SQL queries - I think I should take a look at how to make tables within an SQL database using the SQL CLI Client and see how it is done. The process is much more simpler than I first expected - there is just a few things that I need to know:

1. What I want the name of the table to be
2. What the collumns will be called
3. What Data Types will be in each collumn
4. A Primary Key

So let me look at one that I'm going to create:

<img width="357" alt="CREATE - Creating Tables" src="https://github.com/user-attachments/assets/e8ad6495-2b98-44bc-992a-6651f00c1ab3" />

So in the first command - I've set the following:

1. Table will be called members
2. Collumns will be called member_id and name
3. member_id = Integer that Auto Increments, name is a variable character that has a max count of 100
4. Primary Key will be member_id

Now that I have completed that I can start putting information into this table - to do this I use the commmand INSERT TO and then define the table(collumn) as shown in the screenshot below:

<img width="550" alt="INSERT INTO - adding to table" src="https://github.com/user-attachments/assets/a4d5146d-c9f6-4f9c-a89b-f10fcd82c8d5" />

If I now do a SELECT FROM on these tables I should see that this information has been added:

<img width="371" alt="CREATE - Tables updated" src="https://github.com/user-attachments/assets/32666cad-cc8c-4475-94e2-a03026c42f27" />

Waheeyyy nice and simple I think - todays entry is only a short one as I've been busy all day but it's good to find a little bit of time to keep looking at SQL and how I can use it. 

## Blog Entry - 08/02/25

## Basic SQL Commands - Creating a Database

In this entrty - I want to look more at the tables and more importantly how to actually create a Database to store all of the tables within. As well as this it would also be good to get a look and use the SQL Workbench interface as everything up to now has been done through the CLI client so will be worth opening the Workbench and working through that interface. But first databases!

One of the commands that I have accidently skipped over is how to actually set a database that I want to work on - this is a simple command just simply typing USE *database name* will tell the SQL server which database I want to use and select it for me:

<img width="280" alt="USE - Setting Database" src="https://github.com/user-attachments/assets/e51cf8ef-1539-4138-95b2-154325514a17" />

Now to creating a database - through the CLI the command is very simple - the only argument required is what the name of the database will be - the command CREATE DATABASE will create it as shown below:

<img width="714" alt="CREATE - Making new DB" src="https://github.com/user-attachments/assets/f3a1dd60-2478-4202-b677-c3a76d9b9df5" />

But what about if I want to delete it - easy using the command DROP DATABASE and specifying which database I want to drop:

<img width="314" alt="DROP - Delete Database" src="https://github.com/user-attachments/assets/804955cd-3e9b-4e27-bb3b-3007e4f06971" />

A very brief look but that is at least the basics of being able to create a database, now let's look at the SQL Workbench interface.

## SQL Workbench Interface

SQL Workbench is a GUI so it is easier at least for me to visually see what is going on when I am sending queries from the CLI to the server. I just want to take some time to explore the application just to see what it is about and anything that is of interest to me:

<img width="1439" alt="Data Import and Export" src="https://github.com/user-attachments/assets/a42157ee-ac85-456e-8264-a9e1fc4c2984" />

<code>Being able to import and export data</code>

<img width="1439" alt="Perfromance Dashboard" src="https://github.com/user-attachments/assets/7b8d7519-830f-426a-806a-8db10cdfe979" />

<code>SQL Server Performance Dashboard</code>

<img width="1439" alt="Server Status" src="https://github.com/user-attachments/assets/6c425827-2dd5-4f89-be12-b38268246704" />

<code>Status of SQL Server</code>

Some very useful tools already from what I can see - but let me see what else I can do - such as being able to create a database in this environment:

The process in the GUI is quite simple - simply going through the Database wizard I can go through the process to make a new database and choose what options I want to apply to it:

<img width="1439" alt="CREATE - Make New Database" src="https://github.com/user-attachments/assets/d1913d71-1494-4632-a37f-714832b0ca8c" />

Very nice - but what about if I want to make this database a default database to be able to work in - well that will involve making the schema a default which is as easy as right clicking on the database and selecting the option *Set as Default Schema*.

<img width="1438" alt="Setting Default Schema" src="https://github.com/user-attachments/assets/ed542708-a303-4bdb-9252-b47365dbf696" />

Cool - I'm finding SQL so far to be quite enjoyable - so lets see what the next blog entry brings!

## Blog Entry - 09/02/2025

## Managing Tables in SQL


