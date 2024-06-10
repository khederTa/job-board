# Task Board Application

The main goal of this project is to develop a fully functional, feature-rich task board application that can be monetized. The application should allow users to manage their tasks efficiently with the ability to create, edit, and delete tasks.

## Project Structure

The repository contains two main folders:

1. **api**: Handled by our backend team. It contains all the API endpoints and types/schemas you'll need.
2. **client**: Where you'll be spending most of your time. This contains our React frontend built with Vite and styled with TailwindCSS.

## Getting Started

### Prerequisites

- Node.js
- NPM (or Yarn)
- SQLite (for backend setup)

### Setup

1. **Clone the repository**:
    ```bash
    git clone https://github.com/khederTa/job-board.git
    cd job-board
    ```

2. **Backend Setup**:
    - Install dependencies:
      ```bash
      cd api
      npm install
      ```
    - Copy environment variables:
      ```bash
      cp .env.example .env
      ```
    - Push the database schema:
      ```bash
      npx prisma db push
      ```
    - Start the backend server:
      ```bash
      npm run dev
      ```

3. **Frontend Setup**:
    - Install dependencies:
      ```bash
      cd ../client
      npm install
      ```
    - Copy environment variables:
      ```bash
      cp .env.example .env.local
      ```
    - Start the frontend server:
      ```bash
      npm run dev
      ```

### Folder Structure

#### Client

- **components**: Contains the UI components created by our design system team using Shadcn.
- **constants**: Configuration and environment variables.
- **features**: Contains all the application features. Import from the `index.ts` file within each feature.
- **hooks**: Global hooks used across the application.
- **layouts**: Layout components used across the application.
- **pages**: Organizes pages according to their URL paths.
- **utils**: Global utility functions.

#### Backend

- **constants**: Types and schemas shared with the frontend.
- **utils/getJobListingPriceInCents.ts**: Utility for determining job listing prices.

### Import Aliases

- `@/<folder>`: Imports from the `src` folder in the client.
- `@backend/<folder>`: Imports from the `api/src` folder for types and schemas.

### Common Tasks

- **Creating new tasks**: Use the "New Task" button on the main task board.
- **Editing/deleting tasks**: Click on the triple dots on the right of each task row.

## Additional Information

### API Documentation

- **User Routes**:
  - `POST /users/login`
  - `POST /users/signup`
  - `DELETE /users/logout`
  - `GET /users/session`

- **Job Listing Routes**:
  - `GET /job-listings/published`
  - `GET /job-listings/my-listings`
  - `POST /job-listings`
  - `PUT /job-listings/:id`
  - `DELETE /job-listings/:id`
  - `POST /job-listings/:id/create-publish-payment-intent`

- **Stripe Routes**:
  - `POST /stripe-webhooks/job-listing-order-complete`

### Stripe Setup

- Create a Stripe account.
- Add your secret API key to the `.env` file as `STRIPE_SECRET_KEY`.
- Run the Stripe CLI to test webhooks:
  ```bash
  stripe login
  stripe listen --forward-to localhost:3000/stripe-webhooks/job-listing-order-complete
  ```
- Add the webhook secret to your `.env` file as `STRIPE_ORDER_COMPLETE_WEBHOOK_SECRET`.

### Environment Variables

- Ensure `SESSION_SECRET` is set to a random string for testing purposes. In production, our devops team will handle this.
