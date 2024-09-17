Basic Authentication

### What Authentication Means
Authentication is the process of verifying the identity of a user or entity attempting to access a system. It confirms that the user is who they claim to be, typically through:
- Username/Password: The most common form of authentication, where users provide credentials.
- Tokens: A secure token issued after login (such as OAuth or JWT tokens).
- Biometrics: Fingerprints, face recognition, etc.

### What Base64 Is
Base64 is an encoding scheme used to convert binary data (like images, audio, or any arbitrary data) into a text-based string that can be safely transmitted over media that only supports text. Base64 uses a set of 64 ASCII characters to represent binary data.

### How to Encode a String in Base64
To encode a string in Base64, you need to convert it from its plain text form into its Base64 encoded form.

### What Basic Authentication Means
Basic Authentication is a simple HTTP authentication mechanism where the client sends a username and password to the server in an encoded form using Base64. The format is as follows:

- The client concatenates the username and password with a colon (:) in between.
- This concatenated string is then encoded using Base64.
- The resulting Base64-encoded string is included in the Authorization header of the HTTP request.

```Authorization: Basic <Base64 encoded string>```

### How to Send the Authorization Header
The Authorization header is used to provide credentials (like Basic Authentication) to a server. You can send the Authorization header in various ways depending on the programming language or HTTP client you’re using.

# Simple API

Simple HTTP API for playing with `User` model.


## Files

### `models/`

- `base.py`: base of all models of the API - handle serialization to file
- `user.py`: user model

### `api/v1`

- `app.py`: entry point of the API
- `views/index.py`: basic endpoints of the API: `/status` and `/stats`
- `views/users.py`: all users endpoints


## Setup

```
$ pip3 install -r requirements.txt
```


## Run

```
$ API_HOST=0.0.0.0 API_PORT=5000 python3 -m api.v1.app
```


## Routes

- `GET /api/v1/status`: returns the status of the API
- `GET /api/v1/stats`: returns some stats of the API
- `GET /api/v1/users`: returns the list of users
- `GET /api/v1/users/:id`: returns an user based on the ID
- `DELETE /api/v1/users/:id`: deletes an user based on the ID
- `POST /api/v1/users`: creates a new user (JSON parameters: `email`, `password`, `last_name` (optional) and `first_name` (optional))
- `PUT /api/v1/users/:id`: updates an user based on the ID (JSON parameters: `last_name` and `first_name`)