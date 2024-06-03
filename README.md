# KryptoniteApp

## Overview

KryptoniteApp is a web application designed for the advanced civilization of Krypton in the year 3030. The app allows Kryptonians to register, authenticate, and upload images using a secure API key mechanism. These images are stored in the database as Base64 strings and can be accessed publicly.

## Features

- **User Registration and Authentication**: Email confirmation and Two-Factor Authentication (2FA) using OTP.
- **API Key Generation**: Generate API keys for uploading files.
- **File Upload**: Upload images as Base64 strings.
- **Public Image Access**: Access images without authentication.
- **API Key Management**: Invalidate API keys.

## Tech Stack

- **Node.js**
- **Express.js**
- **MongoDB**
- **Mongoose**
- **Redis** (optional for OTP storage)
- **nodemailer** (for sending emails)

## Directory Structure

```
project-root/
├── src/
│   ├── controllers/
│   │   ├── authController.js
│   │   ├── fileController.js
│   │   ├── apiKeyController.js
│   ├── models/
│   │   ├── user.js
│   │   ├── image.js
│   │   ├── token.js
│   ├── routes/
│   │   ├── authRoutes.js
│   │   ├── fileRoutes.js
│   ├── middleware/
│   │   ├── validateApiKeyAuth.js
│   │   ├── validateImage.js
│   │   ├── authMiddleware.js
│   ├── services/
│   │   ├── userService.js
│   │   ├── authService.js
│   │   ├── apiKeyService.js
│   ├── utils/
│   │   ├── email/
│   |   |   |── template/
│   │   |   |    ├── registrationConfirmation.handlebars
│   │   |   |    ├── otp.handlebars
│   |   |   |── sendEmail.js
│   │   ├── redis.js
│   ├── app.js
│   ├── server.js
├── .env
├── package.json
└── README.md
```

## Installation

1. Clone the repository:
   ```bash
   git clone https://github.com/your-username/kryptoniteapp.git
   cd kryptoniteapp
   ```

2. Install dependencies:
   ```bash
   npm install
   ```

3. Set up environment variables in a `.env` file:
   ```env
   MONGO_URI=your_mongo_connection_string
   REDIS_URL=your_redis_url (if using Redis)
   FROM_EMAIL=sender's_email_address
   EMAIL_PASSWORD=gmail_app_password
   EMAIL_HOST=smtp.gmail.com
   EMAIL_USERNAME=same_as_FROM_EMAIL
   EMAIL_PORT=465
   CLIENT_URL=localhost
   JWT_SECRET=your_JWT_secret
   PORT=PORT_NUMBER
   BCRYPT_SALT=NUMER_OF_SALT_ROUNDS
   ```

4. Start the server:
   ```bash
   npm start
   ```

## Usage

### User Registration and Authentication

1. **Register**:
   - Endpoint: `POST /auth/register`
   - Payload: `{ "name": "username.com","email": "user@example.com", "password": "yourpassword","confirmPassword": "password" }`

2. **Login and 2FA**:
   - Endpoint: `POST /auth/login`
   - Payload: `{ "email": "user@example.com", "password": "yourpassword" }`
   - Followed by OTP submission.

### File Upload

1. **Upload Image**:
   - Endpoint: `POST /files/upload`
   - Headers: `{ "x-api-key": "your_api_key" }`
   - Payload: `multipart/form-data` with an image file.

### Public Image Access

1. **Get All Images**:
   - Endpoint: `GET /files/images`

2. **Get Single Image**:
   - Endpoint: `GET /files/images/:id`

## API Key Management

1. **Invalidate API Key**:
   - Endpoint: `POST /auth/invalidateApiKey`
   - Payload: `{ "apiKey": "your_api_key" }`

## Contributing

1. Fork the repository.
2. Create a new branch: `git checkout -b my-feature-branch`
3. Make your changes.
4. Commit your changes: `git commit -m 'Add some feature'`
5. Push to the branch: `git push origin my-feature-branch`
6. Submit a pull request.

## License

This project is licensed under the MIT License. See the [LICENSE](LICENSE) file for more details.
>>>>>>> master
