
# Database Migrations with Liquibase and Flyway

## A comparison between tools

![](https://miro.medium.com/max/5962/0*9vFU-o3uJLSuUX_V)

Photo by  [Aryan Singh](https://unsplash.com/@wuzclicks?utm_source=medium&utm_medium=referral)  on  [Unsplash](https://unsplash.com/?utm_source=medium&utm_medium=referral)

As a software developer, I want to automatize my relational database migrations on  _test, staging_ or  _production_ environments. To achieve that, I have tested two migration tools widely know on Java universe:  [Liquibase](https://www.liquibase.org/)  and  [Flyway](https://flywaydb.org/).

The stack behind this test project was:

-   Spring Boot & Java 11 application.
-   MySQL database.
-   Maven plugin to run both Liquibase and Flyway.

----------

## Some background

Database changes can be painful and destructive, not only on monoliths but especially on distributed systems. I have found some recommendations about the best practices, such as the article  [“Evolutionary Database Design” by Martin Fowler](https://martinfowler.com/articles/evodb.html)  and this  [talk](https://www.youtube.com/watch?v=eRz3xjM08l0)  _plus_ [book](https://developers.redhat.com/books/migrating-microservice-databases-relational-monolith-distributed-data/) by Edson Yanaga.

Roughly, the important things are:

-   To keep  **database scripts versioned** with the application code.
-   To  **keep backward and forwards compatibility**. For example, a table column can not be renamed right away. It is necessary to have intermediate states between this action: add a new column, write in both columns during version 1.x, change the code to read the new column during version 2.x and drop column during version 3.x.

## Automate tasks

I do not want all my team to have direct access to  _test, staging_ or  _production_ databases and also I do not want to execute scripts manually. Liquibase and Flyway will play this role and all I need to do is to write the scripts.

Since I have tested the  **free**  version of both tools with  **MySQL** database in a  **Spring Boot**  project and  **Maven plugin**, I will summarize their functionalities and why I have chosen one instead of another.

There are plenty of articles focused on Liquibase and Flyway, so I will not extensively talk about them.

You can check these two separated stories for a brief overview:

-   [here is Flyway’s](https://medium.com/@danianepg/flyway-b91f53debede?sk=8535e07de61e84ba6ecce0bff818d02a)  and
-   [here is Liquibase’s](https://medium.com/@danianepg/liquibase-38ea6344a4b9?sk=695158733356e84bcccccd3e40995c67).

## And the chosen one is…

In my humble opinion, both tools are great and they do the job. However, I decided to go for  **Flyway**.

I do not believe I will ever need the all functionalities that Liquibase offers and it was a little bit more painful to configure and run it than Flyway. Also, I always found XML files kind of messy/ugly. *sorry*

**Flyway** does the job straight away and it is much more intuitive than Liquibase. It is easier to simply write SQL in a way that everybody is already used to and thus, there is no learning curve.

Flyway is the most “lightweight” and trouble-free solution to automatize the database migrations.

----------
[*Originally posted on my Medium stories.*](https://medium.com/@danianepg/database-migrations-with-liquibase-and-flyway-5946379c7738?source=friends_link&sk=3d73f41cf8d50a0bba38ab0fc0bb6cd5)
