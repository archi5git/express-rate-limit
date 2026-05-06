# Express Rate Limit

A simple Express.js application that implements rate limiting protection on API endpoints to prevent abuse and DDoS attacks.

## Overview

This project demonstrates how to implement rate limiting in Express.js applications using the `express-rate-limit` middleware. It protects the user registration endpoint by limiting the number of requests from each IP address.

## Features

- **IP-Based Rate Limiting**: Restricts requests per IP address to prevent abuse
- **Configurable Limits**: Easily adjust request limits and time windows
- **User Registration API**: RESTful endpoint for user registration with built-in protection
- **Custom Error Messages**: Clear feedback when rate limits are exceeded
- **Simple Setup**: Minimal configuration required to get started

## Installation

1. Clone or download this repository:
```bash
cd express-rate-limit
```

2. Install dependencies:
```bash
npm install
```

This will install Express.js and any required middleware packages.

## Dependencies

- **express** (^5.2.1): Fast, unopinionated web framework for Node.js
- **express-rate-limit**: Middleware for implementing rate limiting

## Usage

### Starting the Server

Run the following command to start the server:

```bash
node app.js
```

The server will start on `http://localhost:3000`

You should see:
```
Server is running on port 3000
```

### Making Requests

To register a new user, send a POST request to the registration endpoint:

```bash
curl -X POST http://localhost:3000/api/auth/register
```

Expected response:
```json
{
  "message": "User registered successfully"
}
```

## Rate Limiting Configuration

The rate limiter is configured with the following parameters:

| Parameter | Value | Description |
|-----------|-------|-------------|
| `window` | 1 minute | Time window for counting requests |
| `max` | 100 | Maximum requests per IP per time window |
| `message` | Custom error message | Response when limit is exceeded |

### Default Limits

- **Window Duration**: 1 minute (60,000 milliseconds)
- **Max Requests**: 100 requests per minute per IP address
- **Rate Limit Message**: "Too many requests from this IP, please try again after a minute"

## API Endpoints

### User Registration
- **Endpoint**: `POST /api/auth/register`
- **Rate Limit**: 100 requests per minute per IP
- **Request Body**: None required in this example
- **Success Response** (HTTP 201):
  ```json
  {
    "message": "User registered successfully"
  }
  ```
- **Rate Limit Exceeded** (HTTP 429):
  ```json
  {
    "message": "Too many requests from this IP, please try again after a minute"
  }
  ```

## How Rate Limiting Works

1. When a request is received, the rate limiter checks the client's IP address
2. It counts how many requests have been made from that IP in the time window
3. If the request count exceeds the limit (100), the request is rejected
4. After the time window expires, the counter resets for that IP

## Customization

To modify the rate limiting settings, edit the `limiter` configuration in `app.js`:

```javascript
const limiter = rateLimit({
    window: 1 * 60 * 1000,        // Change time window (in milliseconds)
    max: 100,                      // Change max requests
    message: 'Custom error message' // Change error message
});
```

## Common HTTP Status Codes

- **201 Created**: User registration successful
- **429 Too Many Requests**: Rate limit exceeded

## Project Structure

```
express-rate-limit/
├── app.js          # Main application file with rate limiting
├── package.json    # Project metadata and dependencies
└── readme          # This file
```

## Future Enhancements

- Add request body validation
- Implement persistent rate limit storage (Redis)
- Add multiple rate limits for different endpoints
- Implement different limits for authenticated vs unauthenticated users
- Add logging and monitoring

## Testing

You can test the rate limiting by sending multiple requests in rapid succession:

```bash
# Send 150 requests in a loop (first 100 succeed, rest should be rate limited)
for i in {1..150}; do curl -X POST http://localhost:3000/api/auth/register; done
```

## License

ISC

## Author

Your Name/Organization
