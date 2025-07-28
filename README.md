# MERN Social Media App

A full-stack social media application built with the MERN stack (MongoDB, Express.js, React.js, Node.js). This application allows users to register, login, create posts, interact with other users' posts, and manage their social connections.

## 🚀 Features

- **User Authentication**: Secure registration and login with JWT tokens
- **User Profiles**: Complete user profiles with profile pictures and personal information
- **Post Management**: Create, view, and interact with posts
- **Social Features**: Like posts, add comments, and connect with friends
- **File Upload**: Upload and manage profile pictures and post images
- **Responsive Design**: Works seamlessly across different devices
- **Real-time Updates**: Dynamic content updates and interactions

## 🛠️ Tech Stack

### Backend
- **Node.js**: JavaScript runtime environment
- **Express.js**: Web application framework
- **MongoDB**: NoSQL database for data storage
- **Mongoose**: MongoDB object modeling for Node.js
- **JWT**: JSON Web Tokens for authentication
- **bcrypt**: Password hashing and security
- **Multer**: File upload handling
- **GridFS**: Large file storage in MongoDB

### Security & Middleware
- **Helmet**: Security headers and protection
- **CORS**: Cross-origin resource sharing
- **Morgan**: HTTP request logging
- **Body-parser**: Request body parsing

## 📁 Project Structure

```
MERN_APP/
├── client/                 # Frontend React application
├── server/                 # Backend Node.js application
│   ├── controllers/        # Business logic controllers
│   │   ├── auth.js        # Authentication logic
│   │   ├── posts.js       # Post management logic
│   │   └── users.js       # User management logic
│   ├── data/              # Sample/seed data
│   │   └── index.js       # Mock users and posts data
│   ├── middleware/        # Custom middleware
│   │   └── auth.js        # JWT token verification
│   ├── models/            # Database schemas
│   │   ├── Post.js        # Post model schema
│   │   └── User.js        # User model schema
│   ├── public/            # Static files storage
│   ├── routes/            # API route definitions
│   │   ├── auth.js        # Authentication routes
│   │   ├── posts.js       # Post-related routes
│   │   └── users.js       # User-related routes
│   ├── .gitignore         # Git ignore rules
│   ├── index.js           # Server entry point
│   ├── package.json       # Dependencies and scripts
│   └── package-lock.json  # Dependency lock file
└── README.md              # Project documentation
```

## 🚀 Getting Started

### Prerequisites

Make sure you have the following installed:
- **Node.js** (v14.0 or higher)
- **npm** (v6.0 or higher)
- **MongoDB** (v4.0 or higher)
- **Git**

### Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/ramya9908/MERN_App.git
   cd MERN_App
   ```

2. **Install server dependencies**
   ```bash
   cd server
   npm install
   ```

3. **Install client dependencies**
   ```bash
   cd ../client
   npm install
   ```

4. **Set up environment variables**
   
   Create a `.env` file in the server directory:
   ```env
   # Database
   MONGO_URL=mongodb://localhost:27017/mern_social_media
   
   # Authentication
   JWT_SECRET=your_super_secret_jwt_key_here
   
   # Server Configuration
   PORT=3001
   NODE_ENV=development
   ```

5. **Start MongoDB**
   ```bash
   # Make sure MongoDB is running on your system
   mongod
   ```

6. **Start the development servers**
   
   **Terminal 1 - Backend Server:**
   ```bash
   cd server
   npm start
   ```
   
   **Terminal 2 - Frontend Client:**
   ```bash
   cd client
   npm start
   ```

The server will run on `http://localhost:3001` and the client on `http://localhost:3000`.

## 📝 API Documentation

### Authentication Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| POST | `/auth/register` | Register new user | No |
| POST | `/auth/login` | User login | No |

### User Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/users/:id` | Get user by ID | Yes |
| GET | `/users/:id/friends` | Get user's friends | Yes |
| PATCH | `/users/:id/:friendId` | Add/remove friend | Yes |

### Post Endpoints

| Method | Endpoint | Description | Auth Required |
|--------|----------|-------------|---------------|
| GET | `/posts` | Get all posts | Yes |
| GET | `/posts/:userId/posts` | Get user's posts | Yes |
| POST | `/posts` | Create new post | Yes |
| PATCH | `/posts/:id/like` | Like/unlike post | Yes |

### Request/Response Examples

**Register User:**
```json
POST /auth/register
Content-Type: multipart/form-data

{
  "firstName": "John",
  "lastName": "Doe",
  "email": "john@example.com",
  "password": "securePassword123",
  "location": "New York, NY",
  "occupation": "Software Developer"
}
```

**Create Post:**
```json
POST /posts
Authorization: Bearer <jwt_token>
Content-Type: multipart/form-data

{
  "userId": "user_id_here",
  "description": "This is my new post!",
  "picture": [file]
}
```

## 🔧 Environment Variables

Create a `.env` file in the server directory with the following variables:

```env
# Required Environment Variables
MONGO_URL=mongodb://localhost:27017/mern_social_media
JWT_SECRET=your_jwt_secret_key_minimum_32_characters
PORT=3001
NODE_ENV=development

# Optional Configuration
DB_NAME=mern_social_media
UPLOAD_PATH=public/assets
MAX_FILE_SIZE=5242880
```

## 🗄️ Database Schema

### User Model
```javascript
{
  firstName: String (required),
  lastName: String (required),
  email: String (required, unique),
  password: String (required),
  picturePath: String,
  friends: [ObjectId],
  location: String,
  occupation: String,
  viewedProfile: Number,
  impressions: Number
}
```

### Post Model
```javascript
{
  userId: ObjectId (required),
  firstName: String (required),
  lastName: String (required),
  location: String,
  description: String,
  picturePath: String,
  userPicturePath: String,
  likes: Map,
  comments: [String]
}
```

## 🚀 Development

### Available Scripts

**Server:**
- `npm start` - Start development server with nodemon
- `npm test` - Run tests (not configured yet)

**Client:**
- `npm start` - Start React development server
- `npm build` - Build for production
- `npm test` - Run React tests

### Development Workflow

1. **Create a new branch** for your feature
   ```bash
   git checkout -b feature/your-feature-name
   ```

2. **Make your changes** and test thoroughly

3. **Commit your changes**
   ```bash
   git add .
   git commit -m "Add: your descriptive commit message"
   ```

4. **Push and create a pull request**
   ```bash
   git push origin feature/your-feature-name
   ```

## 🔒 Security Features

- **Password Hashing**: Using bcrypt for secure password storage
- **JWT Authentication**: Stateless authentication with JSON Web Tokens
- **Helmet**: Security headers and XSS protection
- **CORS**: Controlled cross-origin resource sharing
- **Input Validation**: Mongoose schema validation
- **File Upload Security**: Multer configuration with file type restrictions

## 🐛 Troubleshooting

### Common Issues

**MongoDB Connection Error:**
```bash
Error: MongoNetworkError: failed to connect to server
```
**Solution:** Ensure MongoDB is running and the connection string is correct.

**JWT Secret Error:**
```bash
Error: secretOrPrivateKey has a value which is not a number or string
```
**Solution:** Make sure JWT_SECRET is set in your .env file.

**File Upload Issues:**
```bash
Error: MulterError: Unexpected field
```
**Solution:** Check that the form field name matches the multer configuration.

### Development Tips

- Use **MongoDB Compass** for database visualization
- Install **Postman** for API testing
- Use **nodemon** for automatic server restarts
- Check **console logs** in browser developer tools for client-side issues

## 🤝 Contributing

1. **Fork** the project
2. **Create** your feature branch (`git checkout -b feature/AmazingFeature`)
3. **Commit** your changes (`git commit -m 'Add some AmazingFeature'`)
4. **Push** to the branch (`git push origin feature/AmazingFeature`)
5. **Open** a Pull Request

### Contribution Guidelines

- Follow the existing code style and structure
- Write descriptive commit messages
- Add comments for complex logic
- Test your changes thoroughly
- Update documentation when necessary

## 📄 License

This project is licensed under the ISC License - see the [LICENSE](LICENSE) file for details.

## 👥 Authors

- **Ramya** - *Initial work* - [ramya9908](https://github.com/ramya9908)

## 🙏 Acknowledgments

- Thanks to the MERN stack community
- Inspiration from popular social media platforms
- MongoDB documentation and tutorials
- Express.js and React.js communities

## 📞 Support

If you have any questions or need help, please:

1. Check the [Issues](https://github.com/ramya9908/MERN_App/issues) page
2. Create a new issue if your problem isn't already reported
3. Provide detailed information about your environment and the issue

---

**Happy Coding! 🚀**
