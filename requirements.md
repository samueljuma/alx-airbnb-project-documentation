# 📋 Backend Requirement Specifications – Airbnb Clone

This document outlines the **functional** and **technical** requirements for key backend features in the Airbnb Clone project. These specifications guide backend development, API design, validation logic, and performance targets.

---

## 🔐 1. User Authentication

### ✅ Functional Requirements

* Users can register as a guest or host using an email and password.
* Users can log in securely using JWT-based authentication.
* Passwords must be hashed before storage.

### 🔗 API Endpoints

| Method | Endpoint           | Description       |
| ------ | ------------------ | ----------------- |
| POST   | /api/auth/register | Register new user |
| POST   | /api/auth/login    | Authenticate user |

### 🧾 Input

* `first_name` (string, required)
* `last_name` (string, required)
* `email` (string, required, unique)
* `password` (string, required, min 8 chars)
* `role` (enum: guest, host, required)

### 📤 Output

* Success: JWT token and user info
* Error: Validation message or unauthorized access

### 🔐 Validation

* Check for existing email
* Strong password enforcement

### ⚙️ Performance

* Authentication response time < 300ms

---

## 🏠 2. Property Management

### ✅ Functional Requirements

* Hosts can create, update, and delete property listings.
* Listings must include details like name, location, price, and description.
* Only hosts can manage their own listings.

### 🔗 API Endpoints

| Method | Endpoint             | Description             |
| ------ | -------------------- | ----------------------- |
| POST   | /api/properties      | Create property         |
| GET    | /api/properties      | View all properties     |
| GET    | /api/properties/\:id | View single property    |
| PUT    | /api/properties/\:id | Update property (owner) |
| DELETE | /api/properties/\:id | Delete property (owner) |

### 🧾 Input

* `name` (string, required)
* `description` (string, required)
* `location` (string, required)
* `price_per_night` (decimal, required)
* `amenities` (array of strings, optional)

### 📤 Output

* Success: Property object
* Error: Unauthorized or validation error

### 🔐 Validation

* Only host can modify/delete their listing
* Required fields must not be empty

### ⚙️ Performance

* Response time < 500ms
* Index on `location` and `price_per_night`

---

## 📅 3. Booking System

### ✅ Functional Requirements

* Guests can book a property by selecting a date range.
* Prevent overlapping bookings.
* Send notification upon confirmation.

### 🔗 API Endpoints

| Method | Endpoint           | Description           |
| ------ | ------------------ | --------------------- |
| POST   | /api/bookings      | Create a new booking  |
| GET    | /api/bookings/me   | Get bookings for user |
| DELETE | /api/bookings/\:id | Cancel booking        |

### 🧾 Input

* `property_id` (UUID, required)
* `start_date` (date, required)
* `end_date` (date, required)

### 📤 Output

* Success: Booking confirmation
* Error: Dates unavailable or validation error

### 🔐 Validation

* Check date range logic (end > start)
* Prevent booking if dates overlap
* Guest must be authenticated

### ⚙️ Performance

* Max response time < 500ms
* Index on `property_id` and `start_date`

---
