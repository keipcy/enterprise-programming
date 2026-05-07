# Enterprise Programming Book Application README

This submission contains two versions of the book database application:

- `BookAppMVC` - MVC version using Servlets, JSP, JDBC and MySQL.
- `BookAppRestful` - RESTful API version with an HTML/CSS/JavaScript client.

The RESTful version was deployed to AWS Elastic Beanstalk with an AWS RDS MySQL database. The report contains the cloud screenshots and main explanation.

## Requirements

- Java 17
- Maven
- Apache Tomcat 9
- MySQL database containing the provided `books` table

## Build

From the project root:

```bash
mvn package
```

This builds both project modules and creates WAR files.

## Deploying the Programs

After building, deploy the WAR files to Apache Tomcat 9:

- MVC app: `BookAppMVC/target/BookAppMVC-1.0-SNAPSHOT.war`
- RESTful app: `BookAppRestful/target/ROOT.war`

This can be done through the Tomcat Manager page or by copying the WAR file into Tomcat's `webapps` folder.

For the RESTful app, database settings are read from environment variables:

```text
DB_HOST
DB_PORT
DB_NAME
DB_USER
DB_PASSWORD
```

The MVC app currently uses the university/mudfoot database settings in its DAO class.

## Finding the MVC Web Application

After deploying the MVC WAR to Tomcat, open:

```text
http://localhost:8080/BookAppMVC-1.0-SNAPSHOT/
```

This opens the MVC book application. From there, the user can view, insert, update and delete books.

## Finding the RESTful Web Application

After deploying the RESTful WAR to Tomcat as `ROOT.war`, open:

```text
http://localhost:8080/
```

This opens the JavaScript client for the RESTful book application.

The deployed AWS version used the Elastic Beanstalk URL shown in the report screenshots.

## Finding the REST Web Service

The REST API endpoint is:

```text
/api/books
```

Local example:

```text
http://localhost:8080/api/books
```

Supported methods:

- `GET` - retrieve/search books
- `POST` - add a book
- `PUT` - update a book
- `DELETE` - delete a book

The API supports JSON, XML and TEXT output using the `format` query parameter:

```text
/api/books?format=json
/api/books?format=xml
/api/books?format=text
```

Search parameters:

```text
title
year
genre
```

Example:

```text
http://localhost:8080/api/books?format=json&title=hunger
```

## Notes

The critical analysis document contains the detailed explanation of the architecture, cloud deployment, design decisions, screenshots, and evaluation.
