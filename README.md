Airbnb Clone Database Schema

This repository contains the SQL schema for a normalized version of the Airbnb-like application's database.

Schema Overview

The database is designed with the following tables:

User: Stores user information.
Address: Stores addresses to eliminate redundancy.
Property: Stores property details linked to owners and addresses.
Booking: Records booking details between users and properties.
Review: Users can review properties.
Payment: Handles payments related to bookings.
Message: Facilitates messaging between users.

Normalization

The schema follows Third Normal Form (3NF):
Addresses are stored separately from properties to avoid redundancy.
All dependencies are based on primary keys.
No transitive dependencies are present.

How to Use

1. Run `schema.sql` in your SQL environment to create the database structure.
2. Populate tables with relevant data.
3. Build application logic on top of this schema.

Future Enhancements

Add `Availability` table for booking times.
Add `Images` table for property photos.
Enhance with indexing for performance optimization.

License

