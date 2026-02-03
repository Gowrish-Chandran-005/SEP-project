# Quick Start Guide - Sprint 1

## 🚀 Get Started in 5 Minutes

### Prerequisites
- Node.js v14+ installed
- npm installed
- Two terminal windows open

---

## Step 1: Start Backend (Terminal 1)

```bash
cd backend
npm install    # (skip if already done)
npm start
```

**Expected output:**
```
✓ Backend running on port 5000
✓ Test login: email=user@example.com, password=password123
```

---

## Step 2: Start Frontend (Terminal 2)

```bash
cd frontend
npm install    # (skip if already done)
npm start
```

**Expected output:**
```
You can now view sep-project-frontend in the browser.
Local: http://localhost:3000
```

---

## Step 3: Open Browser

Navigate to: **http://localhost:3000**

You should see the SEP Project home page! 🎉

---

## Step 4: Test the App

### Option A: Use Test Account
1. Click **"Login"**
2. Enter:
   - Email: `user@example.com`
   - Password: `password123`
3. Click **"Login"**
4. You should see the Wallet page with $1000 balance

### Option B: Create New Account
1. Click **"Register"**
2. Fill in all fields
3. Click **"Register"**
4. Auto-login to Wallet page

---

## Test All Features

### 👛 Wallet
- Click "Wallet" in header
- View your $1000 balance
- Click "Add $100" to increase balance
- Check if balance updates ✅

### 🎁 Promo Codes
- Click "Promo Codes" in header
- Try adding: `WELCOME10` (valid)
- Try adding: `INVALID` (will fail)
- Remove a code using the delete button ✅

### 👤 Profile
- Click "Profile" in header
- Update your name
- Upload any file for ID proof
- Click "Save Profile"
- Should show "Pending KYC Approval" ✅

### 🔐 Logout
- Click "Logout" in header
- Should redirect to Home page
- Try accessing /wallet without logging in
- Should redirect back to login ✅

---

## Valid Promo Codes for Testing

```
WELCOME10
SAVE20
SUMMER50
```

Try any of these when adding promotion codes.

---

## Troubleshooting

### Backend won't start
```bash
# Check if port 5000 is in use
# Windows: netstat -ano | findstr :5000
# Mac/Linux: lsof -i :5000

# Kill the process or use different port
# Edit backend/.env and change PORT
```

### Frontend won't load
```bash
# Ensure backend is running first
# Check http://localhost:5000/api/health
# If it works, frontend should work too
```

### Login fails
```bash
# Use exact credentials:
# Email: user@example.com
# Password: password123

# Check backend console for errors
```

### Promo code "Invalid"
```bash
# Use ONLY these codes:
# - WELCOME10 (case insensitive)
# - SAVE20
# - SUMMER50

# Any other code will be rejected
```

---

## Project Structure

```
SEP-project/
├── backend/
│   ├── server.js
│   ├── db.js
│   ├── middleware.js
│   ├── routes/
│   │   ├── auth.js
│   │   ├── wallet.js
│   │   ├── promo.js
│   │   └── profile.js
│   ├── .env
│   └── package.json
│
└── frontend/
    ├── src/
    │   ├── pages/
    │   ├── components/
    │   ├── context/
    │   ├── services/
    │   ├── App.js
    │   └── index.js
    └── package.json
```

---

## API Endpoints (for testing with Postman)

### Register
```
POST http://localhost:5000/api/auth/register
{
  "name": "John Doe",
  "email": "john@example.com",
  "username": "johndoe",
  "password": "password123"
}
```

### Login
```
POST http://localhost:5000/api/auth/login
{
  "email": "user@example.com",
  "password": "password123"
}
```

Response includes `token` - copy this for authenticated requests.

### Get Wallet (Protected)
```
GET http://localhost:5000/api/wallet
Headers: Authorization: Bearer <your-token-here>
```

### Add Promo Code (Protected)
```
POST http://localhost:5000/api/promos/add
Headers: Authorization: Bearer <your-token-here>
{
  "code": "WELCOME10"
}
```

---

## Key Features

✅ JWT Authentication
✅ Protected Routes
✅ Wallet with Balance
✅ Promo Code Management
✅ Profile Management
✅ KYC Placeholder
✅ Session Persistence
✅ Error Handling
✅ Loading States
✅ Responsive UI

---

## What's Working

✅ Login/Register
✅ View Wallet
✅ Add Funds
✅ Add Promo Codes
✅ Remove Promo Codes
✅ Update Profile
✅ File Upload (placeholder)
✅ Logout
✅ Session Persistence
✅ Protected Routes

---

## What's NOT in Sprint 1 (By Design)

❌ Real payments
❌ Fund transfers
❌ Account linking
❌ Transaction history
❌ Real KYC verification
❌ Admin workflows

These will be added in future sprints!

---

## Need Help?

1. **Check Console Logs**
   - Browser: Press F12 → Console
   - Backend: Check terminal output

2. **Common Issues**
   - Port 5000 in use? Kill process or change port
   - CORS error? Backend should handle it
   - Login failed? Check credentials

3. **Full Documentation**
   - See README.md for detailed information
   - See SPRINT_1_COMPLETE.md for completion report

---

## Demo Flow

**Perfect for showing stakeholders:**

1. Open app → Home page
2. Click Register → Create account
3. Auto-login → See Wallet
4. Add $100 → Balance increases
5. Click Promo → Add WELCOME10
6. Click Profile → Update field
7. Logout → Back to Home

**Time: ~3 minutes** ⏱️

---

**You're all set! Have fun testing!** 🎉

For more details, see README.md
