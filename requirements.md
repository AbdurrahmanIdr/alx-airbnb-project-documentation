# Airbnb Clone – Backend Feature Specifications

## Overview

This document outlines the technical and functional requirements for three major backend features of the Airbnb Clone application:

- User Authentication
- Property Management
- Booking System

Each section includes API endpoint definitions, input/output formats, validation rules, and performance considerations.

---

## 1. User Authentication

### User Authentication Functional Requirements

- Users must be able to register and log in securely.
- Only authenticated users can access protected routes.
- Tokens must be issued using JWT and validated on every request.

### User Authentication API Endpoints

#### `POST /api/auth/register`

- **Description**: Register a new user (guest or host)
- **Input (JSON)**:

  ```json
  {
    "first_name": "John",
    "last_name": "Doe",
    "email": "john@example.com",
    "password": "securepass123",
    "role": "guest"
  }

- **Validation**:

  - `email`: must be valid and unique
  - `password`: min 8 characters
  - `role`: must be one of `guest`, `host`

- **Output**:

  ```json
  {
    "message": "User registered successfully",
    "token": "<jwt_token>"
  }
  ```

#### `POST /api/auth/login`

- **Input**:

  ```json
  {
    "email": "john@example.com",
    "password": "securepass123"
  }
  ```

- **Output**:

  ```json
  {
    "message": "Login successful",
    "token": "<jwt_token>"
  }
  ```

#### Security & Performance

- Passwords must be hashed using bcrypt or Argon2.
- JWT tokens expire after 1 hour and require refresh tokens.
- Brute-force protection should be implemented (e.g., rate limiting).

---

## 2. Property Management

### Property Management Functional Requirements

- Hosts can create, update, and delete listings.
- Listings must include all relevant details for guests to view and search.
- Only authenticated hosts can manage properties.

### Property Management API Endpoints

#### `POST /api/properties/`

- **Input**:

  ```json
  {
    "name": "Beachside Apartment",
    "description": "Spacious and oceanfront",
    "location": "Lagos, Nigeria",
    "price_per_night": 250.00,
    "amenities": ["wifi", "air conditioning"]
  }
  ```

- **Output**:

  ```json
  {
    "message": "Property created successfully",
    "property_id": "uuid"
  }
  ```

#### `PUT /api/properties/:id`

- **Input**: JSON payload with fields to update
- **Access**: Only the host who created the listing

#### `DELETE /api/properties/:id`

- **Validation**:

  - Host must own the property
  - Property must not have active bookings

### Property Management Performance Considerations

- Use database indexing on `location`, `price`, and `host_id` for efficient search.
- Store images via a file server or cloud bucket.

---

## 3. Booking System

### Booking System Functional Requirements

- Guests can book available properties.
- System must validate dates and prevent double booking.
- Booking status must be tracked: `pending`, `confirmed`, `canceled`.

### Booking System API Endpoints

#### `POST /api/bookings/`

- **Input**:

  ```json
  {
    "property_id": "uuid",
    "start_date": "2025-07-10",
    "end_date": "2025-07-12"
  }
  ```

- **Validation**:

  - `start_date` must be before `end_date`
  - Dates must not overlap with existing confirmed bookings

- **Output**:

  ```json
  {
    "message": "Booking created",
    "booking_id": "uuid",
    "status": "pending"
  }
  ```

#### `DELETE /api/bookings/:id`

- Cancels a pending or confirmed booking (guest or host)

### Booking System Performance Considerations

- Use transactions for atomic booking + payment handling.
- Cache availability data using Redis for fast lookup.

---
