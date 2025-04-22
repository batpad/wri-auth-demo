# WRI API Authentication Demo

A minimal frontend application demonstrating how to authenticate with the WRI (World Resources Institute) API as a client-side application.

## Overview

This demo implements the WRI API authentication flow which consists of:

1. Opening a popup window to the WRI login page
2. User completes authentication on WRI's platform
3. WRI redirects back to our callback page with a JWT token
4. Token is stored in localStorage for future API requests

## Files

- `index.html` - Main application page with login button and status display
- `callback.html` - Handles the OAuth callback, stores the received token
- Both files are kept minimal for demonstration purposes

## Running Locally

1. Clone this repository
2. Start a local HTTP server on port 3000. You can do this in several ways:
   ```bash
   # Using npx (recommended)
   npx http-server -p 3000

   # Or if you have Python installed
   # Python 3
   python -m http.server 3000
   # Python 2
   python -m SimpleHTTPServer 3000
   ```
3. Open http://localhost:3000 in your browser
4. Click "Login with WRI" to test the authentication flow

## Configuration

The application uses a simple configuration object in `index.html` where you can modify:
- `callbackUrl` - The URL that WRI will redirect to after login (default: http://localhost:3000/callback.html)
- `wriAuthUrl` - The WRI authentication endpoint (default: https://api.resourcewatch.org/auth/login)

## How it Works

1. When the user clicks "Login with WRI", the application:
   - Constructs the auth URL with callback parameters
   - Opens a popup window to the WRI login page
   - Starts polling for the presence of a token

2. After successful login, WRI redirects to callback.html with a token:
   - The callback page extracts the token from URL parameters
   - Stores it in localStorage
   - Closes the popup window

3. The main page detects the stored token and updates the UI to show the logged-in state
