# User Registration Flowchart

This diagram visualizes the **User Registration** process for the Airbnb Clone backend. It is part of the system design documentation for the `alx-airbnb-project-documentation` project.

## 📌 Objective

To map the workflow and decision logic for registering a new user (guest or host) on the platform.

## 🧩 Key Components

- **Start**: User initiates registration by accessing the registration form.
- **Input Validation**: System checks that all required fields (e.g., email, password, role) are provided.
- **Email Uniqueness Check**: Verifies if the provided email is not already associated with another user.
- **Password Hashing**: Securely hashes the user’s password before storing it.
- **Store in Database**: Saves user data in the `users` table.
- **Send Confirmation Email** (optional): Sends a welcome or verification email.
- **End**: User registration is successful.

## 📂 File

- **Diagram**: `flowcharts/user-registration.png`
- **Directory**: `flowcharts/`

## 🛠️ Tools Used

- Draw.io (<https://draw.io>)

## 🔖 Related Features

- User Management
- Authentication System
- Database Design (User Table)
