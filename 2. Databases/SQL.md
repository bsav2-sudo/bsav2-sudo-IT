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

<img width="839" alt="ORDER - By Last Name DESC and First ASC" src="https://github.com/user-attachments/assets/d65ec5a8-fb36-4b6a-b215-4d6f5949d213" />

Order by the Last Name in a Descending order and First Name in an Ascending order - yep bit of a brain teaser for me as well but looking at it in the screenshot it makes more sense.

Cool that is it for today but I'm quite happy with what I've learnt from these commands and can't wait to explore some more tomorrow.

## Blog Entry - 06/02/25
