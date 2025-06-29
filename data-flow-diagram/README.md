# Airbnb Clone – Data Flow Diagram (DFD)

## Overview

This document provides the Data Flow Diagram (DFD) for the backend system of the Airbnb Clone project. The DFD models how data flows between users, backend services, databases, and external systems throughout key operations such as registration, bookings, and payments.

The diagram covers inputs, processes, data stores, and outputs for the core functionalities of the platform.

## Key Elements in the Diagram

### External Entities

- **Guest**: A user searching for and booking properties.
- **Host**: A user listing properties.
- **Admin**: A platform administrator.
- **Payment Gateway**: External service used to process transactions.

### Processes

- **User Registration & Authentication**
- **Property Listing Management**
- **Search & Booking Process**
- **Payment Handling**
- **Review Submission**
- **Admin Monitoring**

### Data Stores

- **User Database**
- **Property Database**
- **Booking Records**
- **Payment Records**
- **Review Records**

### Data Flows

- User inputs (forms, credentials, search queries)
- API responses (listing results, booking confirmations)
- Internal system operations (validations, verifications)
- Database read/write operations

## File

[data-flow](./data-flow.png)
