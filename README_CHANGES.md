# Solution Changes & Setup Guide

This document explains the completed challenges, setup configurations, and running instructions.

## Completed Challenges

1. **Challenge 1: Real-time messages with Pusher (Backend + Frontend)**
   - Configured Pusher client on the backend to publish `new-message` and `message-deleted` events.
   - Initialized Pusher on the React frontend to subscribe to the `chat-channel` channel.
   - Handled real-time appending of new messages and removal of deleted messages in the UI.
   - Added environment variable support on both ends.

2. **Challenge 2: Message search endpoint + realtime filter (Backend + Frontend)**
   - Added the `GET /api/messages/search` endpoint on the Express backend (case-insensitive search, newest first, max 100 results).
   - Designed a debounced search input (300ms debounce) in the React frontend with full loading and empty state handling.
   - Integrated the search state cleanly such that clearing the query immediately restores the live, Pusher-updated message feed.

---

## Configuration & Quick Start

### 1. Backend Setup (`api/`)
1. Navigate to the backend directory:
   ```bash
   cd api
   ```
2. Copy the example environment file:
   ```bash
   cp env.example .env
   ```
3. Edit `.env` and fill in your Pusher credentials (optional, fallback warnings included):
   ```env
   PORT=3001
   PUSHER_APP_ID=your_pusher_app_id
   PUSHER_KEY=your_pusher_key
   PUSHER_SECRET=your_pusher_secret
   PUSHER_CLUSTER=your_pusher_cluster
   ```
4. Install dependencies and start the development server:
   ```bash
   pnpm install
   pnpm dev
   ```

### 2. Frontend Setup (`app/`)
1. Navigate to the frontend directory:
   ```bash
   cd ../app
   ```
2. Copy the example environment file:
   ```bash
   cp env.example .env
   ```
3. Edit `.env` and fill in your Pusher credentials (starts with `REACT_APP_` for React integration):
   ```env
   REACT_APP_API_URL=http://localhost:3001
   REACT_APP_PUSHER_KEY=your_pusher_key
   REACT_APP_PUSHER_CLUSTER=your_pusher_cluster
   ```
4. Install dependencies and start the React application:
   ```bash
   pnpm install
   pnpm dev
   ```
