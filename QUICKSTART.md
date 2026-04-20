# 🚀 Quick Start Guide - ShopKart E-Commerce Platform

## Step-by-Step Setup (5 minutes)

### 1️⃣ Prerequisites Check
Ensure you have installed:
- **Node.js** (v14+) → Check: `node --version`
- **MongoDB** → Check: `mongod --version` OR use MongoDB Atlas (cloud)

### 2️⃣ Install All Dependencies

Open PowerShell in project folder:

```powershell
# Install all dependencies (backend + frontend)
npm run install-all
```

OR install separately:

```powershell
# Backend
cd backend
npm install

# Frontend
cd ../frontend
npm install
```

### 3️⃣ Setup Environment Variables

#### Backend `.env` file:

```powershell
cd backend
Copy-Item .env.example .env
notepad .env
```

**Minimum required settings:**

```env
PORT=5000
MONGODB_URI=mongodb://localhost:27017/ecommerce
JWT_SECRET=my_super_secret_key_12345
FRONTEND_URL=http://localhost:3000
```

#### Frontend `.env` file:

```powershell
cd ../frontend
Copy-Item .env.example .env
notepad .env
```

```env
REACT_APP_API_URL=http://localhost:5000/api
```

### 4️⃣ Start MongoDB

**Option A - Local MongoDB:**
```powershell
net start MongoDB
```

**Option B - MongoDB Atlas:**
- Create free account at [MongoDB Atlas](https://www.mongodb.com/cloud/atlas)
- Get connection string
- Update `MONGODB_URI` in backend `.env`

### 5️⃣ Add Sample Products (Optional but Recommended)

```powershell
cd backend
node seedDatabase.js
```

This adds 12 sample products to your database!

### 6️⃣ Start the Application

**Option A - Start Both (Recommended):**

From project root:
```powershell
npm run dev
```

**Option B - Start Separately:**

Backend (Terminal 1):
```powershell
cd backend
npm run dev
```

Frontend (Terminal 2):
```powershell
cd frontend
npm start
```

### 7️⃣ Open Application

- **Frontend**: http://localhost:3000
- **Backend API**: http://localhost:5000/api/health

## ✅ Quick Test

1. **Register** a new account at `/register`
2. **Login** with your credentials
3. **Browse** products on home page
4. **Add to cart** and checkout
5. **View orders** in profile

## 🔧 Troubleshooting

### MongoDB Connection Error
```powershell
# Check if MongoDB is running
net start MongoDB

# OR use MongoDB Atlas cloud database
```

### Port Already in Use
```powershell
# Kill process on port 5000
Get-Process -Id (Get-NetTCPConnection -LocalPort 5000).OwningProcess | Stop-Process -Force

# Kill process on port 3000
Get-Process -Id (Get-NetTCPConnection -LocalPort 3000).OwningProcess | Stop-Process -Force
```

### Cannot Find Module Error
```powershell
# Reinstall dependencies
rm -r node_modules
npm install
```

## 📦 What You Get

### ✨ Features Included:

**User Features:**
- ✅ User registration & login
- ✅ Product browsing with search & filters
- ✅ Shopping cart management
- ✅ Order placement & tracking
- ✅ Wishlist
- ✅ Multiple addresses
- ✅ Order cancellation & returns
- ✅ Product reviews & ratings

**Admin Features:**
- ✅ Product management (CRUD)
- ✅ Order status updates
- ✅ User management

**Technical Features:**
- ✅ JWT authentication
- ✅ RESTful API
- ✅ MongoDB database
- ✅ Responsive design
- ✅ Real-time notifications
- ✅ Secure password hashing

## 🎯 Next Steps

1. **Customize** - Change colors, logo, branding
2. **Add Products** - Create your own product catalog
3. **Payment Gateway** - Integrate Stripe/Razorpay
4. **Deploy** - Host on Vercel (frontend) + Render (backend)
5. **Email** - Add order confirmation emails
6. **Images** - Setup Cloudinary for product images

## 📚 Important Files

| File | Purpose |
|------|---------|
| `backend/server.js` | Backend entry point |
| `backend/models/` | Database schemas |
| `backend/routes/` | API endpoints |
| `frontend/src/App.js` | Frontend entry point |
| `frontend/src/pages/` | Page components |
| `frontend/src/context/` | State management |

## 🆘 Get Help

Check these if something goes wrong:
1. MongoDB is running
2. Environment variables are set
3. Dependencies are installed
4. Ports 3000 and 5000 are free
5. Node.js version is 14+

## 🎉 You're All Set!

Your e-commerce platform is ready to use! Start by registering an account and exploring the features.

**Happy Coding! 🚀**
