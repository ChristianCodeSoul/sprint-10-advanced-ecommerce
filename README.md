# ShopIn. — Sprint 10

A modern ecommerce application **Sprint 10: State Integrity vs Database Mutation**.

This project focuses on **Track A  -**

**Frontend Specialists: Advanced State Middleware**, with Redux Toolkit, RTK Query, asynchronous state handling, cache invalidation, and optimistic UI updates.

ShopIn. is a full ecommerce frontend connected to a REST API. The application demonstrates predictable global state management and reliable client-side synchronization with server data.

The main focus of this sprint is keeping the UI state consistent while database mutations are happening in the background.

## Tech Stack

### Frontend

* Next.js
* React
* Redux Toolkit
* RTK Query
* JavaScript
* CSS

### Backend

* Node.js
* Express
* MongoDB
* Mongoose

### Deployment

* Frontend: Next.js production deployment
* Backend: REST API

## Async State Management

The authentication slice uses `createAsyncThunk` to manage asynchronous operations.

The request lifecycle is represented through three states:

or:

The global store keeps track of the current request status and error state.

## RTK Query

RTK Query is used for server-state management and API communication.

The API layer contains queries and mutations for:

* Products
* Users
* Orders

Instead of manually managing loading, error, request, and cache logic for every API call, RTK Query handles these states through its query and mutation hooks.

### Cache Tags

The API uses tag types for cache management:

## Optimistic Updates

Product updates use RTK Query's `onQueryStarted` lifecycle to implement optimistic updates.

### Rollback Test

The optimistic update flow was tested with both successful and failed server mutations.

**Successful mutation:**

```text
Price: ₹2999 → ₹3099
Server accepts request
→ UI remains ₹3099
```

**Failed mutation:**

```text
Invalid price sent
Server rejects request
→ Optimistic UI change is rolled back
```

This demonstrates the required **optimistic update + rollback** behavior.

## Ecommerce Features

The application includes:

* Product listing
* Product detail pages
* Product images
* Product categories
* Add to cart
* Cart quantity management
* Remove from cart
* Clear cart
* Cart item count
* Add-to-cart notification
* Loading states
* Error states
* Responsive layout

## Running Locally

### 1. Clone the repository

```bash
git clone <your-github-repository-url>
cd sprint-10-advanced-ecommerce
```

### 2. Start the backend

```bash
cd backend
npm install
npm run dev
```

### 3. Start the frontend

Open another terminal:

```bash
cd frontend
npm install
npm run dev
```

The frontend runs on the local Next.js development server.

## API Endpoints

### Products

```text
GET    /api/products
GET    /api/products/:id
POST   /api/products
PUT    /api/products/:id
DELETE /api/products/:id
```

### Users

```text
GET    /api/users
GET    /api/users/:id
POST   /api/users
DELETE /api/users/:id
```

### Orders

```text
GET    /api/orders
GET    /api/orders/:id
POST   /api/orders
PUT    /api/orders/:id
DELETE /api/orders/:id
```

## Production Build

From the frontend directory:

```bash
npm run build
```

The production build verifies that the Next.js application compiles successfully before deployment.

**Live Deployment:**
https://sprint-10-advanced-ecommerce.vercel.app
