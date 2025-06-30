# Airbnb Clone – Backend Flowchart

## Overview

This document includes a flowchart illustrating the step-by-step process of one of the core backend functionalities of the Airbnb Clone project. The selected process is **Property Booking**, which involves guest interaction, system validations, database updates, and payment handling.

The flowchart helps visualize the logic, decision points, and data flow involved in booking a property.

## Selected Process: Property Booking

This flowchart represents the backend steps when a guest books a property through the platform. It includes:

- User input validation
- Property availability check
- Booking record creation
- Payment initiation
- Booking status update
- Notification dispatch

## Flowchart Components

### Inputs

- Booking request (property ID, user ID, start date, end date)
- Payment details

### Processing Steps

1. Receive booking request
2. Validate user session and input data
3. Check property availability (date conflict check)
4. Calculate total price
5. Save booking record with status `pending`
6. Initiate payment process
7. On success: mark booking `confirmed`
8. On failure: mark booking `canceled`
9. Send booking confirmation or failure notification

### Output

- Booking confirmation
- Payment receipt or error
- Booking status update in DB

## File
[data-flow-diagram](data-flow-diagram.png)
