# 🧾 Use Case Diagram – Airbnb Clone Backend

This document outlines the major use cases for the backend system of the Airbnb Clone. Each row represents a feature or system capability, and the table shows which actors interact with each feature.

The main actors are:
- **Guest**: A user who books properties.
- **Host**: A user who lists properties.
- **Admin**: A platform manager with oversight responsibilities.
- **External Services**: Third-party systems that interact with our backend, such as payment gateways and email services.

---

| 🧑‍💼 Guest Use Cases | 🏠 Host Use Cases | 🛡️ Admin Use Cases | 🌐 External Services |
|----------------------|------------------|---------------------|----------------------|
| Register             | Register         | Login               | Process payments     |
| Login/Logout         | Login/Logout     | View all users      | Initiate payouts     |
| View profile         | View profile     | Suspend users       | Send email alerts    |
| Update profile       | Update profile   | View all listings   |                      |
| Search listings      | Add listing      | Remove/block listing|                      |
| Filter listings      | Edit listing     | View all bookings   |                      |
| View listing details | Delete listing   | Moderate reviews    |                      |
| Book property        | View bookings    | View payment logs   |                      |
| Cancel booking       | Cancel booking   |                     |                      |
| Make payment         | Receive payouts  |                     |                      |
| Leave a review       | Respond to reviews|                    |                      |
| Send message to host | Reply to messages|                     |                      |
| Receive notifications| Receive notifications |               |                      |

---


