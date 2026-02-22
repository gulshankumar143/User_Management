# SQLNode User Management App

This is a simple Node.js application for managing users with a SQL database. The app uses Express.js for the server, EJS for templating, and a SQL database for data storage. It provides basic CRUD (Create, Read, Update, Delete) operations for user management.

## Features
- List all users
- Add a new user
- Edit user details
- Delete a user
- Password-protected edit and delete actions
- Uses UUIDs for user IDs
- Generates fake users for testing (via Faker.js)

## Project Structure
```
index.js           # Main server file
package.json       # Project dependencies and scripts
schema.sql         # SQL schema for database setup
views/             # EJS templates for UI
  ├── delete.ejs
  ├── edit.ejs
  ├── home.ejs
  ├── new.ejs
  └── showusers.ejs
```


## Application Flow

1. **Home Page**: Shows the total number of users in the database.
2. **Show Users**: Lists all users with options to edit or delete each user.
3. **Add User**: Form to add a new user (email, username, password required).
4. **Edit User**: Edit a user's username (requires password confirmation).
5. **Delete User**: Delete a user (requires password confirmation).

## Getting Started

### Prerequisites
- Node.js (v14 or higher recommended)
- MySQL database (or compatible with `mysql2`)

### Installation
1. Clone the repository or download the source code.
2. Install dependencies:
   ```bash
   npm install
   ```
3. Set up your database using the `schema.sql` file:
   - Create a database (default: `delta_app`).
   - Run the SQL in `schema.sql` to create the `user` table.
4. Configure your database connection in `index.js`:
   - Update `host`, `user`, `password`, and `database` as needed.
5. Start the server:
   ```bash
   node index.js
   ```
6. Open your browser and go to `http://localhost:8080` (or the port specified in your code).

## Usage

- **Add User**: Go to `/user/new` and fill out the form.
- **View Users**: Go to `/user` to see all users.
- **Edit User**: Click "Edit username" next to a user, enter new username and password.
- **Delete User**: Click "Delete" next to a user, enter password to confirm.

### Example Request (Add User)

```
POST /user/new
Body: email, username, password
```

### Troubleshooting

- **Database connection errors**: Check your MySQL server is running and credentials in `index.js` are correct.
- **Port in use**: Change the port in `index.js` if 3000 is occupied.
- **Password errors**: Edit and delete actions require the correct password for the user.

## Configuration & Environment

Database connection is configured in `index.js`:

```js
const connection = mysql.createConnection({
   host: 'localhost',
   user: 'root',
   database: 'delta_app',
   password: 'your_password_here'
});
```

You may use environment variables for sensitive data in production.

## Dependencies

- **express**: Web server framework
- **ejs**: Templating engine
- **mysql2**: MySQL database driver
- **method-override**: Supports HTTP verbs like PATCH/DELETE in forms
- **@faker-js/faker**: Generates fake user data for testing
- **uuid**: Generates unique user IDs
