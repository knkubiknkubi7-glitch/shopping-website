# E-Commerce Platform - ShopKart

A complete full-stack e-commerce web application similar to Amazon/Meesho with all modern features.

## 🚀 Features

### Frontend Features
- **Modern UI**: Clean and professional e-commerce interface
- **Product Search**: Advanced search with filters (category, price, rating, brand)
- **Product Listings**: Grid view with pagination
- **Shopping Cart**: Add/remove items, quantity management
- **Wishlist**: Save favorite products
- **User Authentication**: Login and registration
- **Order Management**: Place orders, track status, view history
- **Returns & Cancellations**: Request returns for delivered orders
- **Responsive Design**: Works on desktop, tablet, and mobile
- **Real-time Updates**: Toast notifications for user actions

### Backend Features
- **RESTful API**: Express.js backend with MongoDB
- **User Management**: Secure authentication with JWT tokens
- **Product Management**: CRUD operations for products
- **Cart Management**: Persistent cart for logged-in users
- **Order Processing**: Complete order lifecycle management
- **Review System**: Product reviews and ratings
- **Address Management**: Multiple delivery addresses
- **Order Tracking**: Status updates and timeline
- **Return Processing**: Handle return requests

## 📋 Prerequisites

Before you begin, ensure you have installed:
- **Node.js** (v14 or higher) - [Download here](https://nodejs.org/)
- **MongoDB** (v4.4 or higher) - [Download here](https://www.mongodb.com/try/download/community)
  - OR use **MongoDB Atlas** (free cloud database) - [Sign up here](https://www.mongodb.com/cloud/atlas)
- **Git** (optional) - [Download here](https://git-scm.com/)

## 🛠️ Installation & Setup

### 1. Install Dependencies

Open PowerShell in the project root directory and run:

```powershell
# Install root dependencies
npm install

# Install backend dependencies
cd backend
npm install
cd ..

# Install frontend dependencies
cd frontend
npm install
cd ..
```

### 2. Configure Environment Variables

#### Backend Configuration

Create a `.env` file in the `backend` folder:

```powershell
# Navigate to backend folder
cd backend

# Copy template file
Copy-Item .env.example .env

# Edit the .env file
notepad .env
```

Update the following variables in `.env`:

```env
PORT=5000
NODE_ENV=development

# MongoDB Configuration
# Option 1: Local MongoDB
MONGODB_URI=mongodb://localhost:27017/ecommerce

# Option 2: MongoDB Atlas (recommended)
# MONGODB_URI=mongodb+srv://YOUR_USERNAME:YOUR_PASSWORD@cluster0.xxxxx.mongodb.net/ecommerce

# JWT Secret (change this to a random string)
JWT_SECRET=your_super_secret_jwt_key_here_change_this

# Frontend URL
FRONTEND_URL=http://localhost:3000
```

#### Frontend Configuration

Create a `.env` file in the `frontend` folder:

```powershell
# Navigate to frontend folder
cd ..\frontend

# Copy template file
Copy-Item .env.example .env

# Edit the .env file
notepad .env
```

Update the `.env` file:

```env
REACT_APP_API_URL=http://localhost:5000/api
```

### 3. Setup MongoDB

#### Option A: Local MongoDB

1. Install MongoDB Community Edition
2. Start MongoDB service:
   ```powershell
   # Start MongoDB service
   net start MongoDB
   ```

#### Option B: MongoDB Atlas (Cloud - Recommended)

1. Go to [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
2. Create a free account and cluster
3. Click "Connect" → "Connect your application"
4. Copy the connection string
5. Replace `<password>` with your database password
6. Update `MONGODB_URI` in backend `.env` file

### 4. Start the Application

#### Start Backend Server

```powershell
# In project root
cd backend
npm run dev
```

The backend will start on `http://localhost:5000`

#### Start Frontend (New Terminal)

```powershell
# In project root (new terminal)
cd frontend
npm start
```

The frontend will start on `http://localhost:3000` and open in your browser.

## 📁 Project Structure

```
ecommerce-platform/
├── backend/
│   ├── models/           # MongoDB schemas
│   │   ├── User.js
│   │   ├── Product.js
│   │   ├── Cart.js
│   │   ├── Order.js
│   │   └── Review.js
│   ├── routes/           # API routes
│   │   ├── authRoutes.js
│   │   ├── productRoutes.js
│   │   ├── cartRoutes.js
│   │   ├── orderRoutes.js
│   │   ├── userRoutes.js
│   │   └── reviewRoutes.js
│   ├── middleware/       # Custom middleware
│   │   └── auth.js
│   ├── .env             # Environment variables
│   ├── server.js        # Entry point
│   └── package.json
│
├── frontend/
│   ├── public/
│   │   └── index.html
│   ├── src/
│   │   ├── components/   # Reusable components
│   │   │   ├── Navbar/
│   │   │   ├── Footer/
│   │   │   ├── ProductCard/
│   │   │   └── ProtectedRoute/
│   │   ├── pages/        # Page components
│   │   │   ├── Home/
│   │   │   ├── Products/
│   │   │   ├── ProductDetails/
│   │   │   ├── Cart/
│   │   │   ├── Checkout/
│   │   │   ├── Orders/
│   │   │   ├── Auth/
│   │   │   └── Profile/
│   │   ├── context/      # React Context
│   │   │   ├── AuthContext.js
│   │   │   └── CartContext.js
│   │   ├── services/     # API services
│   │   │   └── api.js
│   │   ├── App.js
│   │   ├── index.js
│   │   └── index.css
│   ├── .env             # Environment variables
│   └── package.json
│
└── package.json          # Root package.json
```

## 🔑 API Endpoints

### Authentication
- `POST /api/auth/register` - Register new user
- `POST /api/auth/login` - Login user

### Products
- `GET /api/products` - Get all products (with filters)
- `GET /api/products/:id` - Get single product
- `GET /api/products/featured` - Get featured products
- `POST /api/products` - Create product (Admin)
- `PUT /api/products/:id` - Update product (Admin)
- `DELETE /api/products/:id` - Delete product (Admin)

### Cart
- `GET /api/cart` - Get user cart
- `POST /api/cart/add` - Add item to cart
- `PUT /api/cart/update/:itemId` - Update cart item
- `DELETE /api/cart/remove/:itemId` - Remove item
- `DELETE /api/cart/clear` - Clear cart

### Orders
- `POST /api/orders` - Create order
- `GET /api/orders` - Get user orders
- `GET /api/orders/:id` - Get order details
- `PUT /api/orders/:id/cancel` - Cancel order
- `PUT /api/orders/:id/return` - Request return

### User
- `GET /api/users/profile` - Get user profile
- `PUT /api/users/profile` - Update profile
- `POST /api/users/address` - Add address
- `GET /api/users/wishlist` - Get wishlist
- `POST /api/users/wishlist/:productId` - Toggle wishlist

### Reviews
- `POST /api/reviews` - Create review
- `GET /api/reviews/product/:productId` - Get product reviews

## 🧪 Testing the Application

1. **Register a new account** at `http://localhost:3000/register`
2. **Login** with your credentials
3.  **Browse products** on the home page or products page
4. **Search and filter** products by category, price, rating
5. **Add products** to cart
6. **View cart** and proceed to checkout
7. **Place an order** with test address
8. **Track order** in "My Orders" section
9. **Request returns** for delivered orders

## 📱 MongoDB Schema Models

### User Model
- Personal information (name, email, password)
- Multiple delivery addresses
- Wishlist
- Role-based access (user, admin, seller)

### Product Model
- Product details (name, description, price)
- Images and category
- Stock management
- Ratings and reviews
- Shipping information
- Discount and pricing

### Cart Model
- User-specific cart
- Cart items with product references
- Quantity management
- Auto-calculated totals

### Order Model
- Unique order ID
- Order items with product snapshots
- Shipping address
- Payment information
- Order status tracking
- Timeline/history
- Return/cancellation support

### Review Model
- Product reviews and ratings
- User verification
- Helpful votes
- Images support

## 🚀 Deployment

### Backend Deployment (Heroku/Railway/Render)

1. Create account on deployment platform
2. Connect your repository
3. Set environment variables
4. Deploy backend

### Frontend Deployment (Vercel/Netlify)

1. Create account on Vercel or Netlify
2. Connect your repository
3. Set build command: `cd frontend && npm run build`
4. Set publish directory: `frontend/build`
5. Add environment variable: `REACT_APP_API_URL`
6. Deploy

### MongoDB Atlas (Production Database)

1. Create production cluster
2. Configure IP whitelist
3. Create database user
4. Update connection string in backend `.env`

## 🛡️ Security Features

- Password hashing with bcrypt
- JWT token authentication
- Protected API routes
- Input validation
- CORS configuration
- Environment variables for secrets

## 🎨 Technologies Used

### Frontend
- React.js - UI framework
- React Router - Navigation
- Axios - HTTP client
- React Context - State management
- React Icons - Icon library
- React Toastify - Notifications

### Backend
- Node.js - Runtime
- Express.js - Web framework
- MongoDB - Database
- Mongoose - ODM
- JWT - Authentication
- Bcrypt - Password hashing

## 📞 Support

For issues or questions:
1. Check MongoDB connection
2. Verify environment variables
3. Check console for errors
4. Ensure all dependencies are installed

## ⚡ Quick Start Command

Run both frontend and backend simultaneously:

```powershell
# From project root
npm run dev
```

This will start:
- Backend on `http://localhost:5000`
- Frontend on `http://localhost:3000`

## 🎯 Next Steps

After setup:
1. Add sample products via API or admin panel
2. Test all features thoroughly
3. Customize styling and branding
4. Add payment gateway integration (Stripe/Razorpay)
5. Implement image upload (Cloudinary)
6. Add email notifications
7. Deploy to production

## 📝 Notes

- Default port is 5000 for backend and 3000 for frontend
- MongoDB must be running before starting backend
- All API routes require `/api` prefix
- Protected routes require JWT token in Authorization header
- Cart data persists in database for logged-in users
- Free shipping on orders above ₹500
- 18% GST applied on all orders
- 7-day return policy on delivered orders

---

**Happy Shopping! 🛒**
