# Safe-Space Frontend

## Project Overview

**Safe-Space** is a full-stack blog application where users can create, edit, and manage blog posts. The frontend is built with React and communicates with a Flask backend using RESTful APIs. It offers user registration, login, blog management, and profile management, with secure authentication via JSON Web Tokens (JWT).

This single-page application is designed to be responsive, accessible, and user-friendly.

---
## Features

* **Authentication**: Register and log in securely using JWT.
* **Blog Management**: Create, view, edit, and manage blogs.
* **Profile Page**: View user details and blogs.
* **Client-Side Routing**: Navigation via React Router.
* **Form Validation**: Robust validation using Formik and Yup.
* **Responsive Design**: Fully responsive layout with accessible styling.
* **Backend Integration**: Fetch and manipulate data via RESTful API.

---

## Technologies Used

* **React**: Building the user interface.
* **React Router v6**: Client-side routing.
* **Formik**: Form state and validation handling.
* **Yup**: Schema-based validation for forms.
* **CSS**: Styling and responsiveness.
* **Fetch API**: Communication with Flask backend.
* **Create React App**: React project scaffolding.
* **Node.js & NPM**: Dependency management and local server.
* **Flask** (Backend): For user authentication and data persistence.

---

## Setup Instructions

### Prerequisites

* Node.js (v14+)
* NPM (comes with Node.js)
* Git
* Flask backend running at `http://localhost:5555`

### Installation

1. **Clone the Repository**

```bash
git@github.com:Jjumaaa/Safe-Space-Frontend.git
cd Safe-Space-Frontend
```

2. **Install Dependencies**

```bash
npm install
```

3. **Run the Application**

```bash
npm start
```

The app will run at `http://localhost:3000`. Ensure the Flask backend is also running for full functionality.

---

## Project Structure

```
frontend/
├── public/
├── src/
│   ├── components/
│   │   ├── Navbar.js
│   │   ├── LoginForm.js
│   │   ├── RegisterForm.js
│   │   ├── BlogList.js
│   │   ├── BlogForm.js
│   │   └── Profile.js
│   ├── pages/
│   │   ├── Home.js
│   │   ├── BlogCreate.js
│   │   └── ProfilePage.js
│   ├── styles/
│   │   ├── App.css
│   │   ├── Navbar.css
│   │   ├── Form.css
│   │   ├── Blog.css
│   │   └── Profile.css
│   ├── App.js
│   └── index.js
├── package.json
└── README.md
```

---

## API Documentation

The frontend connects to the Flask backend via the following endpoints (base URL: `http://localhost:5555`).

### Authentication Routes

#### `POST /register`

Register a new user.
**Request Body:**

```json
{
  "username": "string",
  "email": "string",
  "password": "string"
}
```

**Response:**

```json
{
  "id": number,
  "username": "string",
  "email": "string"
}
```

#### `POST /login`

Log in and receive a JWT token.
**Request Body:**

```json
{
  "username": "string",
  "password": "string"
}
```

**Response:**

```json
{
  "access_token": "string"
}
```

#### `GET /me`

Retrieve authenticated user profile.
**Headers:**

```
Authorization: Bearer <token>
```

**Response:**

```json
{
  "id": number,
  "username": "string",
  "email": "string"
}
```

---

### Blog Routes

#### `GET /blogs`

Fetch all blog posts.
**Response:**

```json
[
  {
    "id": number,
    "title": "string",
    "bio": "string",
    "image_url": "string",
    "user_id": number,
    "created_at": "string"
  }
]
```

#### `POST /blogs`

Create a new blog post.
**Headers:**

```
Authorization: Bearer <token>
```

**Request Body:**

```json
{
  "title": "string",
  "bio": "string",
  "image_url": "string"
}
```

**Response:**

```json
{
  "id": number,
  "title": "string",
  "bio": "string",
  "image_url": "string",
  "user_id": number,
  "created_at": "string"
}
```

#### `PATCH /blogs/<id>`

Update a blog post (must be the owner).
**Headers:**

```
Authorization: Bearer <token>
```

**Request Body:**

```json
{
  "title": "string",
  "bio": "string",
  "image_url": "string"
}
```

#### `GET /users/<id>/blogs`

Fetch all blogs by a specific user.
**Response:**

```json
[
  {
    "id": number,
    "title": "string",
    "bio": "string",
    "image_url": "string",
    "user_id": number,
    "created_at": "string"
  }
]
```

---

## Deployment

To deploy the frontend to a service like Vercel:

1. Push the code to a GitHub repository.
2. Go to [vercel.com](https://vercel.com) and connect your GitHub repo.
3. Set the build command to:

   ```
   npm run build
   ```
4. Set the output directory to:

   ```
   build
   ```
5. Update all `fetch` URLs in your frontend to point to the deployed backend API On Render or another hosting service.

---

## Notes

* Ensure the Flask backend is running before starting the React app.
* JWT tokens are stored in `localStorage` for authentication.
* Update API base URLs when deploying the frontend and backend.

---