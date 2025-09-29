# Shaj - A Full-Stack E-commerce Platform

Shaj is a complete and modern e-commerce web application built with the MERN stack (MongoDB, Express.js, React, Node.js). It features a user-friendly client interface for customers and a comprehensive dashboard for administrators to manage the store.

## Features

- **User Authentication:** Secure user registration and login system using JWT.
- **Role-Based Access Control:** Distinct dashboards and privileges for regular users and administrators.
- **Product Catalog:** Browse, search, and filter products. View detailed product pages with descriptions, images, and reviews.
- **Shopping Cart:** Add products to a cart and view the order summary before checkout.
- **Payment Integration:** Seamless checkout process powered by Stripe.
- **Order Management:** Users can view their order history, and admins can manage all customer orders.
- **User Dashboard:** Allows users to manage their profile, track orders, and view payment history.
- **Admin Dashboard:**
  - **Statistics:** Visual charts and stats on sales, users,orders.
  - **Product Management:** Add, update, and delete products.
  - **User Management:** View and manage all registered users.
  - **Order Management:** Track and update the status of all orders.
- **Product Reviews:** Authenticated users can post reviews and ratings for products they have purchased.

## Technology Stack

### Backend (`Shaj-backend`)
- **Runtime:** Node.js
- **Framework:** Express.js
- **Database:** MongoDB with Mongoose ODM
- **Authentication:** JSON Web Tokens (JWT)
- **Image Storage:** Cloudinary
- **Payments:** Stripe

### Frontend (`Shaj-client`)
- **Framework:** React
- **Build Tool:** Vite
- **State Management:** Redux Toolkit (including RTK Query for data fetching)
- **Routing:** React Router
- **Styling:** Tailwind CSS
- **UI Components:** Chart.js for dashboard

## Getting Started

Follow these instructions to get a copy of the project up and running on your local machine for development and testing purposes.

### Prerequisites

- Node.js (v18 or later)
- npm
- MongoDB (local instance or a cloud-hosted solution like MongoDB Atlas)
- A Cloudinary account for image hosting
- A Stripe account for payment processing

### Installation & Setup

1.  **Clone the repository:**
    ```bash
    git clone https://github.com/your-username/Shaj.git
    cd Shaj
    ```

2.  **Setup Backend:**
    - Navigate to the backend directory: `cd Shaj-backend`
    - Install dependencies: `npm install`
    - Create a `.env` file in the `Shaj-backend` root and add the following environment variables. Replace the placeholder values with your actual credentials.

      ```env
      # MongoDB Connection URI
      UB_URL=your_mongodb_connection_string

      # Server Port
      PORT=5000

      # JSON Web Token Secret
      JWT_SECRET=your_jwt_secret_key

      # Cloudinary Credentials for image upload
      CLOUD_NAME=your_cloudinary_cloud_name
      API_KEY=your_cloudinary_api_key
      API_SECRET=your_cloudinary_api_secret

      # Stripe Secret Key
      STRIPE_SECRET_KEY=your_stripe_secret_key
      ```
    - Start the backend server:
      ```bash
      npm run start:dev
      ```
      The server will be running on `http://localhost:5000`.

3.  **Setup Frontend:**
    - Open a new terminal and navigate to the client directory: `cd Shaj-client`
    - Install dependencies: `npm install`
    - Start the frontend development server:
      ```bash
      npm run dev
      ```
      The application will be available at `http://localhost:5173`.

## API Endpoints

The backend exposes the following REST API endpoints:

| Method | Endpoint                  | Description                               | Access       |
|--------|---------------------------|-------------------------------------------|--------------|
| POST   | `/api/auth/register`      | Register a new user                       | Public       |
| POST   | `/api/auth/login`         | Authenticate a user and get a token       | Public       |
| GET    | `/api/products`           | Get all products (with filtering/search)  | Public       |
| GET    | `/api/products/:id`       | Get a single product by ID                | Public       |
| POST   | `/api/products`           | Add a new product                         | Admin        |
| PATCH  | `/api/products/:id`       | Update a product                          | Admin        |
| DELETE | `/api/products/:id`       | Delete a product                          | Admin        |
| GET    | `/api/reviews/:productId` | Get all reviews for a product             | Public       |
| POST   | `/api/reviews`            | Post a new review                         | User         |
| POST   | `/api/orders/create-payment-intent` | Create a payment intent with Stripe | User |
| POST   | `/api/orders`             | Create a new order                        | User         |
| GET    | `/api/orders`             | Get all orders (for the logged-in user)   | User         |
| GET    | `/api/orders/all`         | Get all orders for all users              | Admin        |
| PATCH  | `/api/orders/:id`         | Update order status                       | Admin        |
| GET    | `/api/stats/admin`        | Get statistics for the admin dashboard    | Admin        |
| GET    | `/api/users`              | Get all users                             | Admin        |
| PATCH  | `/api/users/admin/:id`    | Update a user's role                     | Admin        |

## Deployment

Both the frontend and backend are configured for deployment on [Vercel](https://vercel.com/). You can deploy the `Shaj-client` and `Shaj-backend` directories as separate project.

- **Backend:** When deploying the backend, ensure you set the environment variables listed in the `.env` file in your Vercel project settings.
- **Frontend:** The frontend will connect to the deployed backend. You may need to update the `baseURL` in the frontend utility files to point to your deployed backend URL.
