# Hotel Management REST API

**Author:** Saiyash Poojari

A RESTful API for hotel management built with **Node.js**, **Express.js**, **Passport.js**, and **bcryptjs**. This API provides user authentication (registration & login) and full CRUD operations for managing hotels.

---

## 🚀 Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (v14 or higher)
- npm

### Installation

```bash
# Clone or download the project
cd "Saiyash Poojari"

# Install dependencies
npm install

# Start the server
npm start
```

The server will start on **http://localhost:4000**

---

## 📁 Project Structure

```
Saiyash Poojari/
├── server.js        # Main application entry point
├── package.json     # Project metadata and dependencies
└── README.md        # Project documentation
```

---

## 📦 Dependencies

| Package           | Purpose                              |
|-------------------|--------------------------------------|
| express           | Web framework for Node.js            |
| express-session   | Session management middleware        |
| passport          | Authentication middleware            |
| passport-local    | Local username/password strategy     |
| bcryptjs          | Password hashing                     |

---

## 🔌 API Endpoints

### General

| Method | Endpoint | Description         | Auth Required |
|--------|----------|---------------------|---------------|
| GET    | /        | Welcome message     | No            |

### Authentication

| Method | Endpoint    | Description              | Auth Required |
|--------|-------------|--------------------------|---------------|
| POST   | /register   | Register a new user      | No            |
| POST   | /login      | Login with credentials   | No            |

### Hotels

| Method | Endpoint       | Description                                    | Auth Required |
|--------|----------------|------------------------------------------------|---------------|
| POST   | /hotels        | Add a new hotel                                | No            |
| GET    | /hotels        | Get all hotels (supports ?rating= filter)      | No            |
| GET    | /hotels/:id    | Get a hotel by ID                              | No            |
| PUT    | /hotels/:id    | Update a hotel by ID                           | No            |
| DELETE | /hotels/:id    | Delete a hotel by ID                           | No            |

---

## 📋 Request & Response Examples

### Register a User

**POST** `/register`

Request Body:
```json
{
  "username": "john_doe",
  "email": "john@example.com",
  "password": "securepassword"
}
```

Response (201):
```json
{
  "message": "User Registered Successfully"
}
```

### Login

**POST** `/login`

Request Body:
```json
{
  "username": "john_doe",
  "password": "securepassword"
}
```

Response (200):
```json
{
  "message": "Login Successful"
}
```

### Add a Hotel

**POST** `/hotels`

Request Body:
```json
{
  "name": "Grand Hyatt",
  "location": "Mumbai",
  "rating": 5,
  "pricePerNight": 8000
}
```

Response (201):
```json
{
  "message": "Hotel Added Successfully",
  "hotel": {
    "id": 1,
    "name": "Grand Hyatt",
    "location": "Mumbai",
    "rating": 5,
    "pricePerNight": 8000
  }
}
```

### Get All Hotels (with optional rating filter)

**GET** `/hotels?rating=5`

Response (200):
```json
[
  {
    "id": 1,
    "name": "Grand Hyatt",
    "location": "Mumbai",
    "rating": 5,
    "pricePerNight": 8000
  }
]
```

### Update a Hotel

**PUT** `/hotels/1`

Request Body:
```json
{
  "name": "Grand Hyatt Mumbai",
  "location": "Mumbai",
  "rating": 5,
  "pricePerNight": 9000
}
```

Response (200):
```json
{
  "message": "Hotel Updated Successfully",
  "hotel": {}
}
```

### Delete a Hotel

**DELETE** `/hotels/1`

Response (200):
```json
{
  "message": "Hotel Deleted Successfully"
}
```

---

## ⚙️ Configuration

The server runs on port **4000** by default. You can override this by setting the `PORT` environment variable:

```bash
PORT=3000 npm start
```

---

## 🔐 Authentication Details

- Passwords are hashed using **bcryptjs** (salt rounds: 10) before storage.
- Sessions are managed via **express-session** with Passport.js serialization.
- In-memory storage is used (data resets on server restart).
