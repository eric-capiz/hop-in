# HopIn Backend

This is the backend for **HopIn**, an Uber-like ride-sharing app built with **Go**, **Gin**, and **MongoDB**. It handles user authentication, ride requests, real-time updates, push notifications, and payments.

## Table of Contents

1. Project Structure
2. Dependencies
3. Environment Variables
4. Setup & Installation
5. Key Modules
6. Core Features
7. Next Steps

## Project Structure

hop-in/
backend/
main.go
go.mod
go.sum
.env
routes/
controllers/
models/
utils/

## Dependencies

- Gin → HTTP routing
- MongoDB Driver → database access
- bcrypt → password hashing
- JWT → authentication
- Stripe → payment processing
- Firebase Admin SDK → push notifications
- Gorilla WebSocket → real-time ride updates
- Validator → input validation
- Logrus → structured logging

## Environment Variables

Create a .env file in backend/:

MONGO_URI=your_mongodb_connection_string
JWT_SECRET=your_jwt_secret
STRIPE_KEY=your_stripe_secret_key
FIREBASE_CREDENTIALS_PATH=path_to_your_firebase_credentials.json

## Setup & Installation

1. Install Go: https://go.dev/dl/
2. Navigate to the backend folder:

cd hop-in/backend

3. Install dependencies:

go get github.com/gin-gonic/gin
go get go.mongodb.org/mongo-driver/mongo
go get golang.org/x/crypto/bcrypt
go get github.com/golang-jwt/jwt/v5
go get github.com/stripe/stripe-go
go get firebase.google.com/go
go get github.com/gorilla/websocket
go get github.com/go-playground/validator/v10
go get github.com/sirupsen/logrus

4. Run the server:

go run main.go

Server runs on http://localhost:8080/.

## Key Modules

- Models → MongoDB schemas (Users, Rides)
- Controllers → Business logic (auth, ride handling)
- Routes → API endpoints grouped by feature
- Utils → Helpers (password hashing, JWT generation)
- Config → Load environment variables

## Core Features

- User authentication (register/login) with hashed passwords and JWT
- Ride requests: create, accept, update, cancel
- Real-time driver-rider updates via WebSockets
- Push notifications via Firebase
- Payment processing via Stripe (to be implemented later)

## Next Steps

1. Set up .env and MongoDB connection
2. Create user model and authentication routes
3. Add ride model and CRUD routes
4. Integrate WebSockets for real-time ride tracking
5. Add push notifications (Firebase)
6. Add payments (Stripe) when ready

# Notes:

## Notes

- Drivers receive 100% of fares.
- Only drivers pay a low monthly subscription.
- Subscription status must be verified for access to driver features.
- App prioritizes driver-first experience.
- Riders can select their destination and optionally specify the amount they want to spend.
- A minimum fare per mile will be enforced.
- Drivers can choose to accept rides based on rider-specified amounts.
- If no amount is selected by the rider, the system will generate a cost using a pricing algorithm.
- No surge pricing or peak fees; riders always pay fair, predictable rates.
- Pricing is transparent and consistent, regardless of demand or location.
- Riders can schedule rides in advance.
- Ratings and reviews for both drivers and riders.
- Safety features: SOS button, live location sharing, verified driver profiles.
- Loyalty or rewards system for frequent riders and drivers.
- Transparent reporting/dashboard for drivers: earnings, ride history, and stats.
- Real-time ETA updates without inflating prices.
- Support for multiple payment methods for subscriptions and future upgrades.
