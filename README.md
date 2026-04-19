# Wallet App

Wallet App is a full-stack mobile expense tracking project built with Expo React Native on the frontend and Express on the backend. The app is designed to help users keep track of daily spending and income through a clean mobile interface, secure authentication, and a simple transaction management flow.

## About The Project

This project combines a cross-platform mobile app with a lightweight API to create a complete personal finance tracking experience. Users can sign in, add transactions, review their balance, and manage their transaction history from a mobile device. The application is structured to keep the experience straightforward while still covering the core pieces of a modern full-stack app such as authentication, API communication, database operations, and state handling.

The mobile side focuses on an easy-to-use experience with dedicated screens for authentication, viewing account activity, and creating new transactions. The backend handles transaction storage, summary calculations, and API routes that connect the app to persistent data.

## What The App Does

The app allows users to record both expenses and income in one place. Each transaction includes a title, amount, category, and user association. Once transactions are created, the home screen displays a running financial summary along with the most recent entries.

Users can:

- sign in and access a personal transaction dashboard
- create new income or expense entries
- choose from multiple transaction categories
- view total balance, total income, and total expenses
- refresh the dashboard to get the latest data
- delete transactions they no longer want to keep
- sign out and return to the authentication flow

## Main User Flow

After authentication, the user lands on the main dashboard. This screen presents a welcome section, a balance summary card, and a list of recent transactions. From there, the user can move to the create transaction screen, enter the amount and title, choose whether the entry is income or expense, and assign a category before saving it.

When the transaction is submitted, the mobile app sends the data to the backend API. The backend stores the record and the app updates the dashboard so the latest balance and transaction list are shown. Users can also delete any existing transaction, which immediately updates the totals and history shown in the app.

## Tech Stack

- Expo and React Native for the mobile application
- Expo Router for app navigation and screen structure
- Clerk for authentication
- Express for the backend API
- PostgreSQL for transaction data storage
- Neon serverless Postgres client for database access
- Upstash Redis and rate limiting middleware for API protection

## Project Structure

```text
backend/
  src/
    config/         database, cron, and service configuration
    controllers/    transaction handlers and summary logic
    middleware/     request rate limiting
    routes/         API route definitions
    server.js       backend entry point

mobile/
  app/              Expo Router screens and layouts
  assets/           images, fonts, and styles
  components/       reusable UI pieces
  constants/        shared values such as API config and colors
  hooks/            client-side data loading and transaction logic
```

## Feature Breakdown

### Authentication

The app uses Clerk to manage user authentication. Signed-in users can access the main application flow, while signed-out users are directed to the authentication screens. This keeps account-specific transaction data tied to the current user experience.

### Dashboard

The home screen works as the central overview of the app. It displays the current user, a financial summary, and a scrollable list of transactions. Pull-to-refresh support makes it easy to reload both the list and summary values without leaving the screen.

### Transaction Creation

The create screen lets users add either income or expense entries. The form includes validation for title, amount, and category selection, helping keep the stored data consistent. Categories such as food, shopping, transportation, entertainment, bills, income, and other make entries easier to organize.

### Transaction Summary

The backend calculates three key values for each user:

- total balance
- total income
- total expenses

These values are returned through the API and displayed in the app so users can quickly understand their financial activity at a glance.

### Transaction Deletion

Each transaction can be removed from the list. After deletion, the app refreshes the dashboard data so the updated totals and recent activity are reflected immediately.

## Backend Overview

The backend exposes API routes for creating, listing, deleting, and summarizing transactions. It includes a health route, JSON request handling, and rate limiting middleware. In production mode, a cron job is also initialized, which shows the backend is structured with room for scheduled tasks and ongoing maintenance work.

The transaction controller is responsible for:

- fetching all transactions for a user
- creating new transactions
- deleting transactions by id
- calculating balance, income, and expense summaries

## Mobile App Overview

The mobile app is organized around reusable components and a small custom hook for transaction operations. The `useTransactions` hook loads the transaction list and summary data in parallel, which helps keep the dashboard responsive. Reusable UI components such as the balance card, transaction items, loaders, and empty-state views keep the code easier to maintain and extend.

The interface is designed around a simple finance workflow rather than a complex accounting system, which makes the project approachable and practical as a mobile full-stack application.

## Why This Project Stands Out

This project is more than a static mobile UI. It includes real authentication, real backend communication, persistent storage, user-specific data, and a clear end-to-end transaction flow. It is a strong example of how a React Native app can be connected to an API and database to deliver a complete feature set instead of only frontend screens.
