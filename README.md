# Campus Library – GraphQL Tutorial

**Name:** Shivam Kumar Soni  
**Roll Number:** 20251651084  
**Course:** CS543 – Web Services  
**Institute:** IIIT Vadodara

## About the Project

Campus Library is a small web application developed as part of the GraphQL tutorial. It displays authors and their books and allows users to add new books through a simple form.

The project uses HTML, CSS and JavaScript for the frontend, Node.js and Apollo Server for the GraphQL API, and MySQL (MariaDB through XAMPP) to store the data.

## Technologies Used

- HTML – webpage structure
- CSS – webpage styling
- JavaScript – frontend functionality
- Node.js – backend runtime
- GraphQL – fetching and modifying data
- Apollo Server – GraphQL API
- MySQL/MariaDB with XAMPP – database
- Git and GitHub – version control

## Project Structure

```text
campus-library/
├── public/
│   ├── index.html
│   └── style.css
├── schema.sql
├── db.js
├── server.js
├── package.json
├── package-lock.json
├── .env.example
├── .gitignore
└── README.md
```

## Files and Their Purpose

- **`schema.sql`** – Creates the `gqldemo` database, the `authors` and `books` tables, and inserts sample records.
- **`db.js`** – Creates a connection pool between Node.js and the database.
- **`server.js`** – Defines the GraphQL schema and resolvers. It handles queries for authors and books and the mutation for adding a book.
- **`public/index.html`** – Contains the webpage, author list, book list and form for adding books. Its JavaScript communicates with the GraphQL API.
- **`public/style.css`** – Contains the styling for the webpage.
- **`package.json`** – Stores project details, scripts and dependencies.
- **`package-lock.json`** – Records the installed dependency versions.
- **`.env.example`** – Shows the environment variables required for the database connection without storing actual credentials.
- **`.gitignore`** – Prevents files such as `node_modules` and `.env` from being committed to Git.
- **`README.md`** – Provides project information and setup instructions.

## How to Run the Project

### 1. Install the requirements

Install Node.js, XAMPP and Visual Studio Code. Install the Live Server extension in VS Code.

### 2. Start XAMPP

Open XAMPP Control Panel and start MySQL. Start Apache as well if you want to access phpMyAdmin.

Open [http://localhost/phpmyadmin](http://localhost/phpmyadmin).

### 3. Create the database

Open the SQL tab in phpMyAdmin and execute the code from `schema.sql`. This creates the database, tables and sample data.

### 4. Install dependencies

Open the terminal in the project folder and run:

```bash
npm install
```

### 5. Configure the database connection

Create a `.env` file in the project root using `.env.example` as a guide.

Set the following values according to your XAMPP configuration:

```env
DB_HOST=localhost
DB_PORT=3306
DB_USER=root
DB_PASSWORD=
DB_NAME=gqldemo
```

If your database has a root password, enter it in `DB_PASSWORD`. Keep `.env` private and do not upload it to GitHub.

### 6. Start the GraphQL server

Run:

```bash
node server.js
```

The server should start at:

[http://localhost:4000/](http://localhost:4000/)

Open this address to test queries using Apollo Sandbox.

### 7. Open the frontend

In VS Code, right-click `public/index.html` and select **Open with Live Server**.

The Campus Library page should display the authors and their books.

### 8. Test adding a book

Enter the book title, year and author in the form, then click **Add book**.

The application sends a GraphQL mutation to the server, saves the book in the database and refreshes the displayed list.

## GraphQL Operations

### Query

The `authors` query retrieves author names, countries and their books.

```graphql
query {
  authors {
    name
    country
    books {
      title
      year
    }
  }
}
```

### Mutation

The `addBook` mutation adds a book to the database.

```graphql
mutation {
  addBook(
    title: "GraphQL for Beginners"
    year: 2025
    authorId: "2"
  ) {
    id
    title
    year
  }
}
```

## What I Learned

- Creating tables and relationships in a relational database.
- Connecting Node.js with MySQL/MariaDB.
- Defining GraphQL types, queries, mutations and resolvers.
- Fetching related data using Graph