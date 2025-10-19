# Unyva - University Student Marketplace

A comprehensive platform for university students to buy, sell, and exchange items within their campus community. The application consists of a React Native mobile frontend and a Node.js backend API.

## 📋 Table of Contents

- [Features](#-features)
- [Tech Stack](#-tech-stack)
- [Project Structure](#-project-structure)
- [Prerequisites](#-prerequisites)
- [Installation & Setup](#-installation--setup)
- [Environment Configuration](#-environment-configuration)
- [Running the Application](#-running-the-application)
- [API Documentation](#-api-documentation)
- [Database Schema](#-database-schema)
- [Testing](#-testing)
- [Deployment](#-deployment)
- [Contributing](#-contributing)
- [Troubleshooting](#-troubleshooting)
- [License](#-license)

## 🚀 Features

### Frontend (Mobile App)
- **Student Registration**: Two-step registration with document upload
- **Marketplace**: Browse and purchase items within the university community
- **Product Management**: List products with images and descriptions
- **User Authentication**: Secure login and session management
- **Favorites System**: Save favorite products
- **Search & Filters**: Advanced search with category and price filters
- **Delivery System**: Integrated delivery management for orders
- **Profile Management**: Update user information and view order history
- **Responsive Design**: Optimized for iOS and Android devices

### Backend (API Server)
- **RESTful API**: Complete API for all frontend operations
- **User Management**: Student registration, authentication, and profile management
- **Product Management**: CRUD operations for products and services
- **Order Processing**: Complete order lifecycle management
- **Delivery System**: Delivery user registration and assignment
- **File Upload**: Image handling for products and user documents
- **Email Notifications**: Automated email sending for various events
- **Database Integration**: PostgreSQL with proper schema design
- **Security**: JWT authentication and input validation

## 🛠️ Tech Stack

### Frontend
- **Framework**: React Native with Expo
- **Language**: TypeScript
- **Navigation**: Expo Router
- **State Management**: React Context API
- **UI Components**: Custom components with React Native primitives
- **Image Handling**: Expo Image Picker
- **Storage**: AsyncStorage for local data persistence
- **HTTP Client**: Fetch API with custom service layer

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Language**: TypeScript
- **Database**: PostgreSQL
- **ORM**: Custom database layer with pg library
- **Authentication**: JWT (JSON Web Tokens)
- **File Upload**: Multer for multipart form data
- **Email**: Nodemailer with Gmail SMTP
- **Validation**: Custom validation middleware
- **Security**: CORS, Helmet, input sanitization

## 📁 Project Structure

```
software/
├── unyva-frontend/          # React Native Mobile App
│   ├── app/                 # App screens and routing
│   │   ├── (auth)/         # Authentication screens
│   │   ├── (tabs)/         # Main tab navigation
│   │   ├── orders/         # Order management screens
│   │   ├── product/        # Product detail screens
│   │   ├── sell/           # Product selling screens
│   │   └── services/       # Service-related screens
│   ├── components/         # Reusable UI components
│   ├── context/            # React Context providers
│   ├── hooks/              # Custom React hooks
│   ├── services/           # API service functions
│   ├── types/              # TypeScript type definitions
│   ├── constants/          # App constants and configuration
│   ├── assets/             # Images, fonts, and static files
│   ├── config/             # API and app configuration
│   └── theme/              # Styling and theming
├── unyva-backend/           # Node.js API Server
│   ├── src/
│   │   ├── controllers/    # Route handlers
│   │   ├── middleware/     # Express middleware
│   │   ├── models/         # Database models (if any)
│   │   ├── routes/         # API route definitions
│   │   ├── services/       # Business logic services
│   │   ├── types/          # TypeScript types
│   │   ├── utils/          # Utility functions
│   │   ├── validators/     # Input validation
│   │   ├── database-init.ts # Database initialization
│   │   ├── db.ts           # Database connection
│   │   └── index.ts        # Server entry point
│   ├── uploads/            # File upload directory
│   ├── scripts/            # Database scripts and utilities
│   └── package.json        # Backend dependencies
└── README.md               # This file
```

## 📋 Prerequisites

- **Node.js** (v16 or higher)
- **npm** or **yarn**
- **Expo CLI** (for mobile development)
- **PostgreSQL** (v12 or higher)
- **Git**
- **iOS Simulator** (macOS only) or **Android Studio** (for Android development)

## 🏃‍♂️ Installation & Setup

### 1. Clone the Repository

```bash
git clone <repository-url>
cd software
```

### 2. Backend Setup

```bash
cd unyva-backend
npm install
```

### 3. Frontend Setup

```bash
cd ../unyva-frontend
npm install
```

### 4. Database Setup

Create a PostgreSQL database:

```bash
createdb unyva_db
```

Run the database schema:

```bash
psql -d unyva_db -f src/database-init.sql
```

## 🔧 Environment Configuration

### Backend Environment Variables

Create `unyva-backend/.env`:

```env
# Server Configuration
PORT=5000
HOST=0.0.0.0
NODE_ENV=development

# Database Configuration
DATABASE_URL=postgresql://username:password@localhost:5432/unyva_db
DB_HOST=localhost
DB_PORT=5432
DB_NAME=unyva_db
DB_USER=your_db_username
DB_PASSWORD=your_db_password

# JWT Configuration
JWT_SECRET=your-super-secret-jwt-key-change-this-in-production
JWT_EXPIRES_IN=7d

# Email Configuration (Gmail)
EMAIL_USER=your-email@gmail.com
EMAIL_PASS=your-app-password

# Base URL
BASE_URL=http://localhost:5000
```

### Frontend Environment Variables

Create `unyva-frontend/.env`:

```env
# API Configuration
EXPO_PUBLIC_API_URL=http://localhost:5000

# App Configuration
EXPO_PUBLIC_IS_DEV=true
EXPO_PUBLIC_APP_NAME=Unyva
EXPO_PUBLIC_APP_VERSION=1.0.0
EXPO_PUBLIC_API_TIMEOUT=10000
EXPO_PUBLIC_DEBUG=true
```

## 🚀 Running the Application

### Start Backend Server

```bash
cd unyva-backend
npm run dev
```

The API server will start on `http://localhost:5000`

### Start Frontend App

```bash
cd unyva-frontend
npm start
```

This will start the Metro bundler. You can then:

- Press `w` to open in web browser
- Press `i` to open iOS simulator
- Press `a` to open Android emulator
- Scan QR code with Expo Go app on your phone

## 📚 API Documentation

### Authentication Endpoints

- `POST /api/auth/register-step1` - Student registration step 1
- `POST /api/auth/register-step2` - Student registration step 2
- `POST /api/auth/login` - User login
- `GET /api/auth/profile` - Get user profile
- `PUT /api/auth/profile` - Update user profile

### Product Endpoints

- `GET /api/products` - Get all products
- `POST /api/products` - Create new product
- `GET /api/products/:id` - Get product by ID
- `PUT /api/products/:id` - Update product
- `DELETE /api/products/:id` - Delete product

### Order Endpoints

- `GET /api/orders` - Get user orders
- `POST /api/orders` - Create new order
- `GET /api/orders/:id` - Get order by ID
- `PUT /api/orders/:id/status` - Update order status

### Delivery Endpoints

- `POST /api/delivery/register` - Register as delivery user
- `GET /api/delivery/orders` - Get available delivery orders
- `PUT /api/delivery/orders/:id/accept` - Accept delivery order

## 🗄️ Database Schema

### Core Tables

- **students**: User account information
- **products**: Marketplace items
- **orders**: Purchase transactions
- **order_items**: Individual items in orders
- **delivery_users**: Delivery personnel
- **reviews**: Product reviews and ratings
- **categories**: Product categories
- **university_halls**: Campus locations

### Key Relationships

- Students can list multiple products
- Products belong to categories
- Orders contain multiple order_items
- Orders can be assigned to delivery_users
- Products can have multiple reviews

## 🧪 Testing

### Backend Testing

```bash
cd unyva-backend
npm test
```

### Frontend Testing

```bash
cd unyva-frontend
npm test
```

### Manual Testing Checklist

- [ ] User registration flow
- [ ] Login/logout functionality
- [ ] Product listing and search
- [ ] Product creation and editing
- [ ] Order placement and management
- [ ] Delivery system integration
- [ ] Image upload functionality
- [ ] Profile management

## 🚀 Deployment

### Backend Deployment

1. Set production environment variables
2. Build the application:
   ```bash
   npm run build
   ```
3. Start production server:
   ```bash
   npm start
   ```

### Frontend Deployment

1. Configure production API URL in `.env`
2. Build for production:
   ```bash
   npx expo build:android
   npx expo build:ios
   ```
3. Submit to app stores using Expo Application Services

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Development Guidelines

- Follow TypeScript best practices
- Write meaningful commit messages
- Test your changes thoroughly
- Update documentation as needed
- Follow the existing code style

## 🔧 Troubleshooting

### Common Issues

#### Metro Bundler Issues
```bash
# Clear Metro cache
npx expo start -c

# Clear npm cache
npm cache clean --force

# Reinstall dependencies
rm -rf node_modules package-lock.json
npm install
```

#### API Connection Issues
1. Verify backend server is running on port 5000
2. Check API URL configuration in frontend
3. Ensure CORS is properly configured
4. Test API endpoints with tools like Postman

#### Database Connection Issues
1. Verify PostgreSQL is running
2. Check database credentials in `.env`
3. Ensure database exists and schema is applied
4. Check connection string format

#### Build Issues
1. Clear all caches (Metro, npm, Expo)
2. Reinstall all dependencies
3. Check for conflicting package versions
4. Verify Expo CLI version compatibility

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

## 📞 Support

For questions or support:

1. Check the troubleshooting section above
2. Review existing issues on GitHub
3. Create a new issue with detailed information
4. Contact the development team

---

**Note**: This application is designed specifically for university students and requires valid student credentials for registration. All transactions are conducted within the university community for safety and trust.
