RegistarationController(java file) -	



registerNewUser:

This function registers a new user in the system. It checks if the provided username already exists; if not, it inserts the new user into the system with the provided information (username, password, first name, last name, and registration date). If the username already exists, it returns a HttpStatus.CONFLICT response; otherwise, it returns a HttpStatus.OK response.

isExistUser:

This function checks if a given username already exists in the system. It queries the database to find a user with the provided username and returns true if the user exists; otherwise, it returns false.

validateUser:

This function validates a user's credentials (username and password) by querying the database for a matching entry. If the combination of username and password is found in the system, the function returns true, indicating successful validation; otherwise, it returns false.

getNumberOfRegistredUsers:

This function retrieves the number of registered users in the past days days. It calculates the registration date threshold using the provided number of days and queries the database to count the number of users whose registration date falls within that range.

getAllUsers:

This function retrieves all users registered in the system. It queries the database to retrieve user information (username, password, first name, last name) for all users and constructs an array of User objects. The array is then returned, containing information about all registered users.

These functions collectively handle user registration, validation, information retrieval, and user count calculation in the registration system using a MongoDB database.


ItemsController(java file) - 


fillMediaItems:

This function copies data from an Oracle database table named MediaItems to the MongoDB database's MediaItems collection. It establishes a connection to the Oracle database, retrieves the items' titles and production years, and inserts them into the MongoDB collection if they don't already exist. It returns a HttpStatus.OK response upon successful completion.

fillMediaItemsFromUrl:

This function reads data from a remote CSV file accessible via an HTTP URL and populates the MongoDB MediaItems collection with the extracted items' titles and production years. It processes each line of the CSV file, parses the title and production year, and inserts them into the MongoDB collection if not already present. It returns a HttpStatus.OK response upon successful completion.

getTopNItems:

This function retrieves the top N items from the MongoDB MediaItems collection. It queries the collection for all items and constructs an array of MediaItems objects containing the titles and production years of the retrieved items. The array is then returned to the caller, containing information about the top N items.

These functions collectively manage the process of populating the MongoDB collection with media item data from both an Oracle database table and a remote CSV file, as well as retrieving a specified number of top items from the collection.

HistoryController(java file)


insertToHistory:

This function inserts a record into two MongoDB collections named History_user and History_title. The record consists of a username, title, and a timestamp in milliseconds since 1970. The function checks if the given username and title exist in their respective collections (Users and MediaItems) and, if so, inserts the record into both history collections. It returns an HttpStatus.OK response upon successful insertion.

getHistoryByUser:

This function retrieves an array of HistoryPair objects representing the history of views by a specific user. The function queries the History_user collection for all records associated with the given username and constructs an array of HistoryPair objects containing titles and timestamps. The array is sorted by timestamp in descending order and returned to the caller.

getHistoryByItems:

This function retrieves an array of HistoryPair objects representing the history of views for a specific item (title). It queries the History_title collection for all records associated with the given title and constructs an array of HistoryPair objects containing usernames and timestamps. The array is sorted by timestamp in descending order and returned to the caller.

getUsersByItem:

This function retrieves an array of User objects representing the users who have viewed a specific item (title). It queries the History_title collection for all records associated with the given title, then fetches user information from the Users collection based on the retrieved usernames. The function returns an array of User objects.

getItemsSimilarity:

This function calculates the Jaccard similarity score between the users who have viewed two specified items (titles). It uses the results from getUsersByItem to find the users who have viewed each item and calculates the similarity based on the Jaccard similarity formula. The similarity score is returned as a double value.

These functions together manage the recording of user-item interactions, retrieval of viewing history, calculation of item similarity based on user viewership, and fetching users who have viewed a specific item.









