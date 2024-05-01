# Backend for Media Management System

## Overview
This project serves as the backend for a media management system, handling user management, media item operations, user registration, and history. It provides detailed APIs for interacting with user and media item data stored in a MongoDB database.

## Technologies
- Java
- Spring Boot (assuming usage for HTTP status responses)
- MongoDB
- Oracle Database (used in conjunction with MongoDB)

## Functionalities

### Registration
- **registerNewUser**: Registers a new user and handles conflicts if the username already exists.
- **isExistUser**: Checks if a username exists in the system.
- **validateUser**: Validates user credentials for login purposes.
- **getNumberOfRegistredUsers**: Retrieves the count of users registered within a specified time frame.
- **getAllUsers**: Fetches a list of all users from the system.

### Media Items
- **fillMediaItems**: Transfers media item data from an Oracle database to MongoDB.
- **fillMediaItemsFromUrl**: Imports media item data from a remote CSV file into MongoDB.
- **getTopNItems**: Retrieves the top N media items based on a specified criterion from MongoDB.

### History
- **insertToHistory**: Adds a viewing record to user and item history collections in MongoDB.
- **getHistoryByUser**: Retrieves viewing history for a specified user.
- **getHistoryByItems**: Retrieves viewing history for a specified media item.
- **getUsersByItem**: Fetches users who have viewed a particular media item.
- **getItemsSimilarity**: Calculates the Jaccard similarity between viewers of two specified media items.

## Setup and Running Locally
1. Ensure Java and MongoDB are installed on your system.
2. Clone the repository to your local machine.
3. Navigate to the project directory and compile the Java files. If using Maven or Gradle, run the appropriate build command.
4. To run the server, use:
   ```
   java -jar build/libs/media-management-system.jar
   ```

## Configuration
- Environment variables for database connections must be set up, including URLs and credentials for MongoDB and Oracle databases.
