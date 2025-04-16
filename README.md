# Address Book App

This is a full-stack address book application built with Node.js, Express, MySQL, and Flutter. It allows users to manage their contacts, including names, phone numbers, email addresses, organizations, and other relevant information. The application features user authentication, contact sharing, and filtering capabilities.

## Table of Contents

- [Features](#features)
- [Technologies Used](#technologies-used)
- [Installation](#installation)
- [Configuration](#configuration)
- [Running the Application](#running-the-application)
- [API Endpoints](#api-endpoints)
- [Database Schema](#database-schema)
- [Flutter Application Structure](#flutter-application-structure)
- [Error Handling](#error-handling)
- [Security Considerations](#security-considerations)
- [Future Enhancements](#future-enhancements)
- [Troubleshooting](#troubleshooting)
- [Contributing](#contributing)

## Features

* **User Authentication:** Secure signup and login functionality using bcrypt for password hashing and JWT for authentication.
* **Contact Management:**
  * Add new contacts with detailed information.
  * Update existing contact details.
  * Delete contacts.
  * View detailed information for each contact.
* **Contact Sharing:**
  * Share contacts with specific users.
  * Control contact visibility (visible to all or only shared users).
* **Filtering:**
  * Filter contacts based on name, city, date of birth range, organization, and job title.
* **Visible to All:** Option to make contacts visible to all logged-in users.
* **Responsive Design:** Flutter frontend provides a cross-platform mobile experience (iOS and Android).
* **Database Persistence:** Data is stored in a MySQL database.
* **Data Validation:** Backend validation implemented using MySQL Triggers to ensure data integrity and consistency, particularly for phone numbers and username/password constraints.
* **Transaction Management:** Backend uses transactions to ensure atomicity of operations when creating or updating contacts and related data (addresses, phone numbers, etc.), preventing data inconsistencies.
* **Real-time Updates:** Refresh the contacts list after adding, editing, or deleting contacts.
* **User Interface:** A clean and intuitive user interface designed for easy navigation and contact management.
* **Date Picker:** For selecting date of births.
* **User Friendliness:** Easy-to-use interface that's intuitive to use.

## Technologies Used

### Backend:
* Node.js (v16 or higher)
* Express (v4 or higher)
* MySQL2 (v2 or higher)
* jsonwebtoken (JWT)
* bcrypt
* dotenv
* cors

### Frontend:
* Flutter (v3 or higher)
* Dart
* http (Flutter package for making HTTP requests)
* shared_preferences (Flutter package for local storage)

### Database:
* MySQL (v8 or higher recommended)

## Installation

### 1. Prerequisites
* **Node.js and npm:** Download from [nodejs.org](https://nodejs.org/).
* **Flutter SDK:** Install from [flutter.dev](https://flutter.dev/).
* **MySQL:** Install MySQL server.
* **A Code Editor** (Visual Studio Code or any other IDE)
* **Android Studio** or Xcode for running and testing.
* **MySQL Workbench or other SQL client**

### 2. Clone the Repository
```bash
git clone https://github.com/Swarnadip-Dey/addressbook_combined.git
cd addressbook_combined
```

### 3. Backend Setup
```bash
cd backend
npm install
```

### 4. Frontend Setup
```bash
cd ../frontend
flutter pub get
```

### 5. MySQL Database Setup
```sql
CREATE DATABASE addressbook;
```
Run the table creation scripts: `createTables.js` in the backend directory.
Run the trigger creation scripts: `createTriggers.js` in the backend directory.
Seed the database (Optional):
```bash
node seeder.js
```

### 6. Setup Environment Variables
Create a `.env` file in the backend directory:
```env
DB_HOST=localhost
DB_USER=your_db_user
DB_PASSWORD=your_db_password
DB_DATABASE=addressbook
DB_PORT=3306
PORT=3000
```
Modify `config.dart` in the frontend directory:
```dart
class Config {
  static const String apiBaseUrl = 'http://localhost:3000';
}
```

## Running the Application

### 1. Start the Backend
```bash
cd backend
npm start
```

### 2. Start the Frontend
```bash
cd frontend
flutter run
```

## API Endpoints

### User Authentication
* `POST /signup` - Registers a new user.
* `POST /login` - Authenticates a user.

### Contacts
* `GET /contacts` - Retrieves all visible contacts.
* `GET /contacts/:contactId` - Retrieves a specific contact.
* `GET /contacts/user/:userId` - Retrieves contacts accessible to the specified user.
* `POST /contacts` - Creates a new contact.
* `PUT /contacts/:contactId` - Updates an existing contact.
* `DELETE /contacts/:contactId` - Deletes a contact.

### Filtering & Sharing
* `GET /filter` - Filters contacts based on query parameters.
* `GET /filter/Visible_to_all` - Retrieves contacts visible to all.
* `GET /users` - Retrieves all users.
* `PUT /userShares` - Updates shared user IDs.

## Database Schema
Tables include `user`, `contacts`, `addresses`, `phone_numbers`, `emails`, `relationships`, `share`, and `UserShares`.

## Flutter Application Structure
* `main.dart` - Entry point.
* `add_contact.dart` - UI for adding contacts.
* `update_contact.dart` - UI for editing contacts.
* `about_contact.dart` - UI for viewing contact details.
* `config.dart` - API configuration.
* `preferred_share.dart` - Contact sharing management.

## Error Handling
* Backend: Middleware for API errors, proper HTTP responses.
* Frontend: Try-catch blocks, SnackBar for error messages.

## Security Considerations
* **Password Hashing:** bcrypt.
* **Authentication:** JWT.
* **Input Validation:** MySQL triggers.
* **CORS:** Enabled.
* **Data Sanitization:** Server-side validation.

## Future Enhancements
* **Image Support:** Upload contact images.
* **Advanced Search:** Multi-criteria search.
* **Contact Groups:** Organize contacts.
* **Import/Export:** CSV, vCard support.
* **Offline Support:** Local data caching.
* **Notifications:** Push notifications.
* **Testing:** Add unit and integration tests.
* **Docker:** Add Docker support.

## Troubleshooting
* **Database connection error?** Ensure MySQL is running.
* **Login issues?** Verify credentials in the database.
* **Flutter not connecting to backend?** Ensure `apiBaseUrl` is correct.
* **Phone number validation trigger issues?** Ensure numeric input with 10-digit limit.

## Contributing
1. Fork the repository.
2. Create a new branch.
3. Make changes and test.
4. Commit changes.
5. Push branch and submit a pull request.

