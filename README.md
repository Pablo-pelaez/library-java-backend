# This is meant to be a guide for executing and understanding the functionality of the project

## Description
This project is a library application developed with Spring Boot. It includes basic functionalities for managing users and books, using an in-memory H2 database.

## Requirements
- **Java 17**: Make sure you have Java 17 installed on your machine.
- **Gradle**: This project uses Gradle as the build system.

## Clone the Repository
First, clone the repository to your local machine

cmd/powershell
git clone https://github.com/Pablo-pelaez/library-java-backend.git
cd library-java-backend

## Project Execution
To bear in mind, here are some key information to test and run the application:
  * This is going to be the Console URL  where the endpoits will be executed and its respective port ==> http://localhost:8080
  * JDBC URL ==> http://localhost:8080/h2-console/  This will allow you to access to the DB where you can check the records made by each endpoint
  * User ==> sa
  * Password ==> password

## CRUD Guidelines

* The first thing you might wonder is to register. Here's the process how you can do it:
   - Endpoint ==> http://localhost:8080/api/users/register
   - Body ==> { "email": "user1@example.com", "password": "securepassword3" }
   - Method ==> POST

* The process to login is quite similar in terms of information. Keeping in mind that the user you want to use is already registered, here we have how to do it:
   - Endpoint ==> http://localhost:8080/api/users/login
   - Body ==> { "email": "user1@example.com", "password": "securepassword3" }
   - Method ==> POST

* The process to add a new book is the following one:
   - Endpoint ==> http://localhost:8080/api/books
   - Body ==> {
    "title": "The Wheel of Time",
    "author": "Robert Jordan",
    "publishYear": 1990
    }
   - Method ==> POST
   - Headers ==> It's important to add a token when you login: Key: Authorization || value: "Given_Token_After_Login"
 
* The process to get all the books is the following one:
   - Endpoint ==> http://localhost:8080/api/books
   - Body ==> empty
   - Method ==> GET
   - Headers ==> It's important to add a token when you login: Key: Authorization || value: "Given_Token_After_Login"

* The process to update a book is the following one:
   - Endpoint ==> http://localhost:8080/api/books/{id}
   - Body ==> {
    "title": "The Wheel of Time_edit",
    "author": "Robert Jordan_edit",
    "publishYear": 1999
    }
   - Method ==> PUT
   - Headers ==> It's important to add a token when you login: Key: Authorization || value: "Given_Token_After_Login"

* The process to delete a book is the following one:
   - Endpoint ==> http://localhost:8080/api/books/{id}
   - Body ==> empty
   - Method ==> DELETE
   - Headers ==> It's important to add a token when you login: Key: Authorization || value: "Given_Token_After_Login"
 
* You can also search by the id of that book your looking for this way:
   - Endpoint ==> http://localhost:8080/api/books/{id}
   - Body ==> empty
   - Method ==> GET
   - Headers ==> It's important to add a token when you login: Key: Authorization || value: "Given_Token_After_Login"

* There is also the possibility to search a serie of books by keywords this way:
   - Endpoint ==> http://localhost:8080/api/books/search?query={keyword} Its important to mention that this kind of matches are CASE_SENSITIVE [which means that one thing is "House" and another is "house"]
   - Body ==> empty
   - Method ==> GET
   - Headers ==> It's important to add a token when you login: Key: Authorization || value: "Given_Token_After_Login"
 

# NOTES:
  * All the tests were made in Postman in order to check every single endpoint and simulating the respective session for a registered user and their role to use these endpoints
  * If there's any hesitation or the given guide might have a mistake, please reach me out!
