# SEP Project - Sprint 1

## Overview
A fully functional **Authentication + Wallet + Profile + Promotion Codes** application. This is Sprint 1 - a **stable MVP** with simplified, safe features.

---

## Project Structure
```
SEP-project/
├── backend/          # Express.js API server
│   ├── routes/       # API endpoints
│   ├── db.js         # In-memory database
│   ├── middleware.js # Auth middleware
│   ├── server.js     # Main server
│   └── package.json
└── frontend/         # React web app
    ├── src/
    │   ├── pages/    # Page components
    │   ├── components/
    │   ├── context/  # Auth context
    │   ├── services/ # API client
    │   ├── App.js
    │   └── index.js
    └── package.json
```

---

## Quick Start

### Prerequisites
- Node.js (v14+) and npm

### Backend Setup

1. **Navigate to backend directory:**
   ```bash
   cd backend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the server:**
   ```bash
   npm run dev
   ```
   
   Server will run on `http://localhost:5000`

### Frontend Setup

1. **In a new terminal, navigate to frontend directory:**
   ```bash
   cd frontend
   ```

2. **Install dependencies:**
   ```bash
   npm install
   ```

3. **Start the React app:**
   ```bash
   npm start
   ```
   
   App will open on `http://localhost:3000`

---

## Features (Sprint 1)

### ✅ Authentication
- User registration and login
- JWT-based authentication
- Protected routes
- Session persistence

### ✅ Wallet
- View wallet balance
- Add fixed $100 amounts
- Simple, non-transactional design

### ✅ Promotion Codes
- Add promotion codes (PROMO2025, WELCOME100, SAVE50, FIRST10)
- View applied codes
- Remove promotion codes
- Validation against valid codes

### ✅ Profile Management
- View profile information
- Update name, address, DOB
- Upload ID proof for KYC (placeholder)
- Mark changes as "Pending KYC Approval"

---

## API Endpoints

### Authentication
- `POST /api/auth/register` - Register a new user
- `POST /api/auth/login` - Login and get JWT token

### Wallet (Protected)
- `GET /api/wallet` - Get wallet balance
- `POST /api/wallet/add-funds` - Add $100 to wallet

### Promotion Codes (Protected)
- `GET /api/promo` - Get user's promo codes
- `POST /api/promo/add` - Add a promo code
- `DELETE /api/promo/:id` - Remove a promo code

### Profile (Protected)
- `GET /api/profile` - Get user profile
- `PUT /api/profile` - Update profile

---

## Testing with Postman

### 1. Register
```
POST http://localhost:5000/api/auth/register
Body: {
  "email": "user@example.com",
  "username": "testuser",
  "password": "password123"
}
```

### 2. Login
```
POST http://localhost:5000/api/auth/login
Body: {
  "email": "user@example.com",
  "password": "password123"
}
```
Response will include a `token`.

### 3. Get Wallet (Protected)
```
GET http://localhost:5000/api/wallet
Headers: Authorization: Bearer <token>
```

### 4. Add Promo Code
```
POST http://localhost:5000/api/promo/add
Headers: Authorization: Bearer <token>
Body: {
  "code": "WELCOME100"
}
```

---

## User Flow Demo

1. **Visit Home Page** - `http://localhost:3000`
2. **Register** - Click "Register" and create account
3. **Auto-login** - Redirects to Wallet after registration
4. **Add Promo Code** - Click "Promo Codes", add WELCOME100
5. **Update Profile** - Click "Profile", update name/address
6. **Add Funds** - Click "Wallet", add $100
7. **Logout** - Use header logout button

---

## Valid Promo Codes (for testing)
- `PROMO2025`
- `WELCOME100`
- `SAVE50`
- `FIRST10`

---

## Database (In-Memory)
- **No external database needed** - data is stored in memory
- Data resets on server restart
- Perfect for Sprint 1 demo

---

## What's NOT Included (Intentionally)
❌ Fund transfers  
❌ Account linking  
❌ Real payment gateways  
❌ OTP/2FA  
❌ Admin approval workflows  
❌ Transaction history  
❌ Actual KYC verification  

---

## Next Steps (Future Sprints)
- Persistent database (MongoDB/PostgreSQL)
- Real payment gateway integration
- Advanced security features
- Transaction history
- Admin panel for KYC approvals

---

## Troubleshooting

### Backend won't start
- Check if port 5000 is already in use
- Try: `netstat -ano | findstr :5000` (Windows)
- Kill the process or use a different port in `.env`

### Frontend won't connect to backend
- Ensure backend is running on port 5000
- Check CORS settings in backend (should be enabled)
- Clear browser cache and restart frontend

### Login fails
- Use the exact email or username you registered with
- Password is case-sensitive

---

## Support
For issues, check the console logs in both browser (frontend) and terminal (backend).

---

**Happy coding! 🚀**
