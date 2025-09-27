# Personal Finance Tracker

A full-stack personal finance management application with web and mobile interfaces. Track your income, expenses, budgets, and financial goals with beautiful charts and analytics.

## 🌟 Features

### 💰 Financial Management
- **Income & Expense Tracking** - Categorize and track all your financial transactions
- **Budget Management** - Set monthly budgets and monitor spending by category
- **Financial Goals** - Create and track progress toward financial objectives
- **Real-time Analytics** - Interactive charts and spending insights

### 📱 Multi-Platform
- **Web Application** - Responsive web interface
- **Mobile App** - Native Android APK with offline capabilities
- **Cross-device Sync** - Data synchronized across all platforms

### 🔒 Security & Privacy
- **Secure Authentication** - JWT-based user authentication
- **Password Encryption** - Bcrypt password hashing
- **User Data Isolation** - Each user's data is completely private

## 🚀 Live Demo

- **Web App**: [https://personal-finance-tracker-moyc.onrender.com](https://personal-finance-tracker-moyc.onrender.com)
- **Mobile App**: Download APK from releases

## 🛠️ Technology Stack

### Frontend
- **Web**: HTML5, CSS3, JavaScript (ES6+)
- **Mobile**: Apache Cordova
- **Charts**: Chart.js for data visualization
- **UI**: Responsive CSS Grid & Flexbox

### Backend
- **Runtime**: Node.js
- **Framework**: Express.js
- **Database**: MongoDB Atlas
- **Authentication**: JWT (JSON Web Tokens)
- **Security**: bcryptjs, CORS

### Deployment
- **Backend**: Render.com
- **Database**: MongoDB Atlas (Cloud)
- **Mobile**: Android APK

## 📦 Installation & Setup

### Prerequisites
- Node.js (v16+)
- npm or yarn
- MongoDB Atlas account
- Android Studio (for mobile development)

### Backend Setup

1. **Clone the repository**
```bash
git clone https://github.com/YOUR_USERNAME/personal-finance-tracker.git
cd personal-finance-tracker/backend
```

2. **Install dependencies**
```bash
npm install
```

3. **Environment Configuration**
Create `.env` file:
```env
NODE_ENV=development
PORT=5000
MONGODB_URI=your_mongodb_connection_string
JWT_SECRET=your_super_secret_jwt_key
FRONTEND_URL=http://localhost:3000
```

4. **Start the server**
```bash
npm start
```

The backend will run on `http://localhost:5000`

### Frontend Setup

1. **Navigate to frontend directory**
```bash
cd ../frontend
```

2. **Serve the frontend**
```bash
# Using Python (if installed)
python -m http.server 3000

# Or using Node.js http-server
npx http-server -p 3000
```

The frontend will be available at `http://localhost:3000`

### Mobile App Setup

1. **Install Cordova CLI**
```bash
npm install -g cordova
```

2. **Navigate to mobile directory**
```bash
cd ../mobile/FinanceTracker
```

3. **Add Android platform**
```bash
cordova platform add android
```

4. **Build the APK**
```bash
cordova build android
```

5. **Install on device**
```bash
# Connect Android device and enable USB debugging
cordova run android
```

## 🗂️ Project Structure

```
personal-finance-tracker/
├── backend/
│   ├── package.json
│   ├── server.js
│   ├── .env
│   └── frontend/
│       └── index.html
├── frontend/
│   ├── index.html
│   ├── assets/
│   ├── css/
│   └── js/
├── mobile/
│   └── FinanceTracker/
│       ├── config.xml
│       ├── package.json
│       ├── www/
│       ├── platforms/
│       └── plugins/
└── README.md
```

## 📱 Mobile App Features

### Android APK
- **Offline Capability** - View existing data without internet
- **Native Performance** - Smooth, responsive interface
- **Secure Storage** - Local data encryption
- **Auto-sync** - Automatic data synchronization when online

### Mobile-Specific Optimizations
- Touch-friendly interface
- Optimized for various screen sizes
- Network error handling
- Offline mode support

## 🔧 API Documentation

### Authentication Endpoints
- `POST /api/auth/register` - User registration
- `POST /api/auth/login` - User login

### Transaction Endpoints
- `GET /api/transactions` - Get user transactions
- `POST /api/transactions` - Create new transaction
- `PUT /api/transactions/:id` - Update transaction
- `DELETE /api/transactions/:id` - Delete transaction

### Budget Endpoints
- `GET /api/budgets` - Get user budgets
- `POST /api/budgets` - Create/update budget

### Goal Endpoints
- `GET /api/goals` - Get user goals
- `POST /api/goals` - Create new goal
- `PUT /api/goals/:id` - Update goal
- `DELETE /api/goals/:id` - Delete goal

### Analytics Endpoints
- `GET /api/dashboard/stats` - Get dashboard statistics
- `GET /api/analytics/summary` - Get analytics summary

## 🚀 Deployment

### Deploy Backend to Render

1. **Create Render account** at render.com
2. **Connect GitHub repository**
3. **Set environment variables**:
   - `NODE_ENV=production`
   - `MONGODB_URI=your_mongodb_atlas_uri`
   - `JWT_SECRET=your_production_jwt_secret`
4. **Deploy** - Render will automatically build and deploy

### Deploy Frontend

The frontend is served as static files by the Express backend at the root URL.

### Mobile App Distribution

1. **Build release APK**:
```bash
cordova build android --release
```

2. **Sign the APK** (for distribution):
```bash
# Generate keystore
keytool -genkey -v -keystore release-key.keystore -alias mykey -keyalg RSA -keysize 2048 -validity 10000

# Build signed APK
cordova build android --release -- --keystore=release-key.keystore --storePassword=password --alias=mykey --password=password
```

## 📊 Database Schema

### Users
```javascript
{
  _id: ObjectId,
  username: String (unique),
  email: String (unique),
  password: String (hashed),
  createdAt: Date
}
```

### Transactions
```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  type: String (income/expense),
  amount: Number,
  category: String,
  description: String,
  date: Date,
  createdAt: Date
}
```

### Budgets
```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  category: String,
  limit: Number,
  month: Number (1-12),
  year: Number,
  createdAt: Date
}
```

### Goals
```javascript
{
  _id: ObjectId,
  userId: ObjectId,
  title: String,
  targetAmount: Number,
  currentAmount: Number,
  targetDate: Date,
  description: String,
  createdAt: Date
}
```

## 🧪 Testing

### Manual Testing
- Register new user account
- Add income and expense transactions
- Set monthly budgets for different categories
- Create financial goals with target amounts
- View analytics and charts
- Test mobile app functionality

### API Testing
Use tools like Postman or curl to test API endpoints:

```bash
# Health check
curl https://personal-finance-tracker-moyc.onrender.com/health

# Register user
curl -X POST https://personal-finance-tracker-moyc.onrender.com/api/auth/register \
  -H "Content-Type: application/json" \
  -d '{"username":"testuser","email":"test@example.com","password":"password123"}'
```

## 🤝 Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
4. Push to the branch (`git push origin feature/AmazingFeature`)
5. Open a Pull Request

## 📝 License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

## 👨‍💻 Author

**Your Name**

- Email: malugu.dileepkumar@example.com

## 🙏 Acknowledgments

- Chart.js for beautiful data visualizations
- MongoDB Atlas for reliable cloud database
- Render.com for seamless deployment
- Apache Cordova for mobile app framework

## 📞 Support

If you have any questions or need help, please:
1. Check the [Issues](https://github.com/yourusername/personal-finance-tracker/issues) page
2. Create a new issue if needed
3. Contact me directly at malugu.dileepkumar@gmail.com

## 🚨 Security

If you discover a security vulnerability, please send an e-mail to malugu.dileepkumar@gmail.com. All security vulnerabilities will be promptly addressed.

---

**⭐ Star this repository if you found it helpful!**
