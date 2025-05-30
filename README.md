# Survify

**Survify** is a full-stack survey web application that allows users to participate in surveys and earn points, businesses to create and analyze surveys, and admins to manage the platform. The app is designed with role-based access control and provides separate interfaces for Users, Businesses, and Admins.

## Features

### User

* Register and log in
* View available surveys
* Submit answers to surveys (one option per question)
* Earn points for each completed survey (feature coming soon)

### Business

* Register and log in
* Create, update, and delete surveys
* View survey response reports with aggregated one-hot encoded results
* Manage survey lifecycle and monitor performance

### Admin

* Log in with special access
* Create and manage business accounts
* View and manage all users and surveys
* Create new admins (inline section at the end of Admin Dashboard)
* Log admin creation actions in the console

## Technologies Used

### Frontend

* React
* Zustand (for state management)
* TanStack Query (for API data fetching and caching)
* Axios (for HTTP requests)
* Tailwind CSS or any UI library (based on user preference)

### Backend

* Node.js
* Express.js
* MongoDB (Mongoose ODM)
* JSON Web Tokens (JWT) for authentication

### Other Tools

* Firebase (optional - for auth or hosting if needed)

## Folder Structure (Simplified)

```
/client
  /src
    /components
    /pages
    /api
    /store
/server
  /controllers
  /routes
  /models
  /middleware
```

## Survey Answer Model

* Each survey has a `questions` array.
* Responses are stored in a `SurveyResult` model.
* Each result uses a 2D array to represent answers in one-hot encoding.
* One-hot encoding format: each question has an array with `1` at the selected option index.

## API Overview

### Auth

* `POST /api/auth/register`
* `POST /api/auth/login`

### User

* `GET /api/user/surveys`
* `POST /api/user/surveys/:id/submit`

### Business

* `POST /api/business/surveys`
* `PUT /api/business/surveys/:id`
* `DELETE /api/business/surveys/:id`
* `GET /api/business/surveys/:id/results`

### Admin

* `POST /api/admin/create-business`
* `POST /api/admin/create-admin`
* `GET /api/admin/all-users`
* `GET /api/admin/all-surveys`

## Installation

1. Clone the repository:

```bash
git clone https://github.com/yourusername/survify.git
```



2. Set up environment variables:

* Create a `.env` file in the server root with:

```
PORT=5000
MONGO_URI=your_mongodb_uri
JWT_SECRET=your_jwt_secret
```

3. Run the development servers:

```bash
# In folder which contains both the frontend and backend folders
npm run build
npm run start
```

## Future Improvements

* Implement points and rewards system for users
* Add email verification and password reset
* Add export/download reports for businesses
* Improve responsiveness and accessibility

## License

This project is open-source and available under the MIT License.
