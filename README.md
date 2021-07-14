# Relational Database Basics

## Learning Goals

- Describe the structure of a relational database as tables related through the use of primary and foreign keys
- Define a primary key
- Define a foreign key

## Introduction

We'll introduce the concept of relational databases and how they recognize
relations among stored items of information.

## Relational Databases

Let's say that you've been hired by a big and important company to do the
payroll for all of their employees. We'll call it MyFace (inspired by nothing in
particular). Every two weeks, you need to look up each and every employee and
how much they get paid, and send them a check _and_ send a notice of that check
to their manager (managers, after all, should know when their employees are
getting paid).

In addition, let's say that managers get paid every month, instead of every two
weeks. So, once a month we need to go through the spreadsheet again, find _just
the managers_, and send them _their_ checks. In such a situation, we would need
a place to store all of the managers and employees.

Using a spreadsheet, your storage system might look something like this:

![Payroll Spreadsheet](http://readme-pics.s3.amazonaws.com/Screen%20Shot%202015-09-03%20at%205.12.12%20PM.png)

So every two weeks, we would have to look through every single entry in this
spreadsheet, send each person their check, and then figure out a way to identify
an employee's manager to send that manager a confirmation that each employee has
been paid. We need some way to _associate_ the employees to their manager.

We could add a "Manager" column to the spreadsheet that would be filled out with
the name of that person's manager (if that person is an employee and not a
manager themselves). This is getting messy. Not only do we have to do a lot of
searching through the spreadsheet and manual detection of who is an employee and
who is a manager, but we also have to match each employee with the name of their
manager. If only there was some way to simplify our system!

Enter relational databases. A relational database, simply put, is **a database
structured to recognize relations among stored items.** In such a system, it
would be easy to tell an employee that they _belong to_ a certain manager and to
tell a manager that they _have many_ employees.

### Relational Database Structure

Relational databases have one unique and very powerful feature that allows us to
establish relationships between multiple tables: **primary keys** and **foreign
keys**.

- **Primary Key**: a column in a table with an identifier (ID) that uniquely
  identifies one specific record, or row, in a table
- **Foreign Key**: a column in from one table that refers to a primary key in
  another table

Continuing with our payroll example from earlier, employees and managers would
be stored in their own **tables**. A table is like a spreadsheet; it has columns
and rows.

Our managers table would look something like this:

![managers table](https://cloud.githubusercontent.com/assets/18357112/17033515/7617ab2a-4f4c-11e6-8545-f179bdeeb500.JPG)

And our employees table would look something like this:

![employees table](https://cloud.githubusercontent.com/assets/18357112/17033522/7d7ac122-4f4c-11e6-9116-2cfebe111f27.JPG)

Our employees table has a "Manager ID" column, filled with the ID number of that
person's manager. In a relational database, every row has a number, called a
**primary key**. Relationships between tables can be established by using a
**foreign key** column, like our "Manager ID" column, that uses that primary key
of another table to refer to a member of that table.

In the images above, you can see that in the employees table Bob and Karen both
have a value of 1 in the Manager ID column (**foreign key**). How can we tell
who their manager is? We need to look to the other table for that information —
the managers, and find the manager with the Manager ID (**primary key**) of 1.
That exact process of using a key in one table to identify a corresponding row
in another table is what SQL will do for us programatically when we give it the
right instructions!

Why should our foreign key, our point of reference between an employee and his
or her manager, be a number? Why not just use the manager's name? Well, names
are very rarely unique. What if MyFace hires a new manager, also named Steve?
It's a popular name, after all. How would our database know _which_ Steve
manages which employees. Primary keys, on the other hand, **are always unique!**

Now, with these separated but related tables, our job just got a lot easier. We
should thank...

## Edgar Codd

![Edgar Codd](http://readme-pics.s3.amazonaws.com/Edgar_F_Codd.jpg)

Edgar Codd invented the concept of the relational database, in other words, he
came up with the idea that storing data in tables, indexed by primary key and
related by foreign keys would _normalize_ that data.

> At the time, Nixon was normalizing relations with China. I figured that if he
> could normalize relations, then so could I.
>
> — Edgar Codd

Codd developed Relational Database Theory as a graduate student. Afterwards, he
worked with Don Chamberlain at IBM to create a language that would allow the
user to traverse these relational databases for specific subsets of information.

The language they created was SQL––Structured (or Standard) Query Language. SQL
allows the user to carry out queries like "find the employees who make more than
the managers", or "find the managers whose employees make under $X" in an
efficient and sensical manner. Before SQL, database queries were all about
_where_ data was stored, instead of _what_ data a user is looking for.

## Conclusion

Working with relational databases takes a bit more abstract thought than working
with a flat spreadsheet. Instead of visualizing the data all in one place, we
have to consider how data in multiple places can be related. Thankfully, in SQL,
the only way to relate between two different tables is using **foreign keys**
and **primary keys**, so once you are comfortable with this concept, you'll be
well on your way to mastering relational databases.
