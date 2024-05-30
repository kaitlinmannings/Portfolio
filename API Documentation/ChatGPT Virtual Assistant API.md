# ChatGPT Virtual Assistant API Documentation

## Overview

The ChatGPT Virtual Assistant API allows developers to integrate conversational
AI capabilities into their applications. This API provides endpoints for sending
messages, receiving responses, and managing conversations.

### Base URL

```
https://api.chatgptva.com/v1
```

## Authentication

All requests to the ChatGPT Virtual Assistant API must include an API key. You
can obtain an API key by signing up on our
[developer portal](https://developer.chatgptva.com).

### Example Header

```
Authorization: Bearer YOUR_API_KEY
```

## Endpoints

### 1. Send Message

**Endpoint:**

```
POST /messages
```

**Description:**

Sends a message to the ChatGPT Virtual Assistant and receives a response.

**Request:**

- **Headers:**
  - `Authorization: Bearer YOUR_API_KEY`
  - `Content-Type: application/json`

- **Body:**

```json
{
  "conversation_id": "12345",
  "message": "Hello, how can I improve my cybersecurity?"
}
```

**Response:**

- **Status: 200 OK**

```json
{
  "conversation_id": "12345",
  "response": "To improve your cybersecurity, you should start by identifying
  your assets and potential risks. Implement strong passwords and use encryption
  where possible."
}
```

### 2. Get Conversation History

**Endpoint:**

```
GET /conversations/{conversation_id}
```

**Description:**

Retrieves the history of a specific conversation.

**Request:**

- **Headers:**
  - `Authorization: Bearer YOUR_API_KEY`

- **Parameters:**
  - `conversation_id` (required): The ID of the conversation.

**Response:**

- **Status: 200 OK**

```json
{
  "conversation_id": "12345",
  "history": [
    {
      "timestamp": "2024-05-28T12:34:56Z",
      "message": "Hello, how can I improve my cybersecurity?",
      "response": "To improve your cybersecurity, you should start by
      identifying your assets and potential risks. Implement strong passwords
      and use encryption where possible."
    }
  ]
}
```

### 3. List Conversations

**Endpoint:**

```
GET /conversations
```

**Description:**

Lists all conversations for the authenticated user.

**Request:**

- **Headers:**
  - `Authorization: Bearer YOUR_API_KEY`

**Response:**

- **Status: 200 OK**

```json
{
  "conversations": [
    {
      "conversation_id": "12345",
      "last_message": "Hello, how can I improve my cybersecurity?",
      "last_response": "To improve your cybersecurity, you should start by
      identifying your assets and potential risks. Implement strong passwords
      and use encryption where possible.",
      "timestamp": "2024-05-28T12:34:56Z"
    }
  ]
}
```

### 4. Delete Conversation

**Endpoint:**

```
DELETE /conversations/{conversation_id}
```

**Description:**

Deletes a specific conversation.

**Request:**

- **Headers:**
  - `Authorization: Bearer YOUR_API_KEY`

- **Parameters:**
  - `conversation_id` (required): The ID of the conversation to be deleted.

**Response:**

- **Status: 204 No Content**

## Error Handling

The API uses standard HTTP status codes to indicate the success or failure of an
API request. Here are some common status codes you might encounter:

- **200 OK:** The request was successful.
- **201 Created:** The resource was successfully created.
- **400 Bad Request:** The request was invalid or cannot be otherwise served.
- **401 Unauthorized:** Authentication failed or user does not have permissions
for the requested operation.
- **404 Not Found:** The requested resource could not be found.
- **500 Internal Server Error:** An error occurred on the server.

## Rate Limiting

To ensure fair usage and stability of the API, rate limiting is enforced. If you
exceed the rate limit, you will receive a `429 Too Many Requests` response.
Please refer to the rate limit headers for more details.

### Rate Limit Headers

- `X-RateLimit-Limit`: The maximum number of requests that the user is allowed to make.
- `X-RateLimit-Remaining`: The number of requests remaining in the current rate
limit window.
- `X-RateLimit-Reset`: The time at which the current rate limit window resets.

## Contact and Support

For any questions or issues, please contact our support team at support@chatgptva.com or visit our [support page](https://support.chatgptva.com).
