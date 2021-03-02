# Book Search Engine


## Description 
AS AN avid reader
I WANT to search for new books to read
SO THAT I can keep a list of books to purchase

## Acceptance Criteria
- GIVEN a book search engine
- WHEN I load the search engine, I am presented with a menu with the options Search for Books and Login/Signup and an input field to search for books and a submit button.

- WHEN I click on the Search for Books menu option , I am presented with an input field to search for books and a submit button

- WHEN I am not logged in and enter a search term in the input field and click the submit button, I am presented with several search results, each featuring a book’s title, author, description, image, and a link to that book on the Google Books site

- WHEN I click on the Login/Signup menu option, a modal appears on the screen with a toggle between the option to log in or sign up

- WHEN the toggle is set to Signup , I am presented with three inputs for a username, an email address, and a password, and a signup button

- WHEN the toggle is set to Login, I am presented with two inputs for an email address and a password and login button

- WHEN I enter a valid email address and create a password and click on the signup button,  my user account is created and I am logged in to the site

- WHEN I enter my account’s email address and password and click on the login button , I the modal closes and I am logged in to the site

- WHEN I am logged in to the site ,  the menu options change to Search for Books, an option to see my saved books, and Logout

- WHEN I am logged in and enter a search term in the input field and click the submit button, I am presented with several search results, each featuring a book’s title, author, description, image, and a link to that book on the Google Books site and a button to save a book to my account

- WHEN I click on the Save button on a book, that book’s information is saved to my account

- WHEN I click on the option to see my saved books, I am presented with all of the books I have saved to my account, each featuring the book’s title, author, description, image, and a link to that book on the Google Books site and a button to remove a book from my account

- WHEN I click on the Remove button on a book, that book is deleted from my saved books list

- WHEN I click on the Logout button ,I am logged out of the site and presented with a menu with the options Search for Books and Login/Signup and an input field to search for books and a submit button  



## Deployed Application: 
https://enigmatic-ravine-51332.herokuapp.com/

## Specifications 
You’ll need to complete the following tasks in each of these back-end files:

server.js: Implement the Apollo Server and apply it to the Express server as middleware.

auth.js: Update the auth middleware function to work with the GraphQL API.

## Back-End Specifications

- **`server.js`**: Implement the Apollo Server and apply it to the Express server as middleware.
- **`auth.js`**: Update the auth middleware function to work with the GraphQL API.
- **`Schemas`** Directory: 
     - **`index.js`**: Export your typeDefs and resolvers
    - **`resolvers.js`**: Define the query and mutation functionality to work with Mongoose models
- **`typeDefs.js`**: Define the necessary `Query` and `Mutation` types:
    - `Query` type:
    - `me`: which returns a `User` type
- **`Mutation`** type:
    - **`login`**: Accepts an email and password as parameters;
        returns an `Auth` type
    - **`addUser`**: Accepts a username, email and password, parameters; returns an `Auth` type
    - **`saveBook`**:Accepts a book author's array, description, title, bookId, image, and link as parameters; returns a
    - **`User`** type. (look into creating whats now as an `input` type to handle all of these parameters).
    - **`removeBook`**: Accepts a book's `bookId` as a parameter; returns a `User` type.

- **`User`** type:
    - **`_id`**
    - **`username`**
    - **`email`**
    - **`bookCount`**
    - **`savedBooks`**(This will be an array of the `Book` type)
- **`Book`** type:
    - **`bookId`** (Not the `_id`, but the book's `id` value returned from Google's Book API.)
    - **`authors`**(An array of strings, as there may be more than one author.)
    - **`description`**
    - **`title`**
    - **`image`**
    - **`link`**
- **`Auth`** type:
    - **`token`**
    - **`user`**(reference the `User` type).


## Front-End specifications

- **`queries.js`**: This will hold the query `GET_ME`, which will execute the `me` query set up using Apollo Server.

- **`mutation.js`**:
    - **`LOGIN_USER`** will execute the `loginUser` mutation set up using Apollo Server.
    - **`ADD_USER`** will execute the `addUser` mutation.
    - **`SAVE_BOOK`** will execute the `saveBook`mutation.
    - **`REMOVE_BOOK`** will execute the `removeBook` mutation.

Additionally, you’ll need to complete the following tasks in each of these front-end files:

- **`App.js`**: Create an Apollo Provider to make every request work with the Apollo server.
- **`SearchBook.js`**:
    - Use the Apollo `useMutation()` Hook to execute the `SAVE_BOOK` mutation in the `handleSaveBook()` function instead of the `saveBook()` function imported from the `API` file.
    - Make sure you keep the logic for saving the book's ID to state in the `try...catch` block!

- **`SavedBooks.js`**:
    - Remove the `useEffect()` Hook that sets the state for UserData.
    - Instead, use the `useQuery()` Hook to execute the `GET_ME` query on load and save it to a variable named `userData`.
    - Use the `useMutation()` Hook to execute the `REMOVE_BOOK `mutation in the `handleDeleteBook()` function instead of the `deleteBook()` function that's imported from `API` file. (Make sure you keep the `removeBookId()` function in place!)

- **`SignupForm.js`**: Replace the `addUser()` functionality imported from the `API` file with the `ADD_USER` mutation functionality

- **`LoginForm.js`**:Replace the `loginUser()` functionality imported from the `API` file with the `LOGIN_USER` mutation functionality.

