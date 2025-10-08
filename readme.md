# Virtual Assistant Project

A full-stack virtual assistant application built with React frontend and Node.js backend.

## 🚀 Deployment Instructions

### Prerequisites
- Node.js installed
- npm or yarn package manager
- Render account for hosting

### Backend Deployment (Render)

1. **Connect your GitHub repository to Render**
   - Go to [Render Dashboard](https://dashboard.render.com/)
   - Click "New +" → "Web Service"
   - Connect your GitHub repository

2. **Configure the service:**
   - **Name**: `virtual-assistant-backend`
   - **Environment**: `Node`
   - **Build Command**: `npm install && npm run build`
   - **Start Command**: `npm start`
   - **Plan**: Free

3. **Environment Variables:**
   - `NODE_ENV`: `production`
   - Add your MongoDB connection string
   - Add any other required environment variables

### Frontend Deployment

The frontend is now served by the backend, so you don't need a separate frontend deployment.

### Local Development

1. **Clone the repository:**
   ```bash
   git clone <your-repo-url>
   cd virtualAssistant(3)
   ```

2. **Install dependencies:**
   ```bash
   # Backend
   cd backend
   npm install
   
   # Frontend
   cd ../frontend
   npm install
   ```

3. **Run the application:**
   ```bash
   # Backend (in backend directory)
   npm run dev
   
   # Frontend (in frontend directory, new terminal)
   npm run dev
   ```

### Build Process

The application uses a unified build process where the backend serves the frontend static files:

1. **Frontend build**: `npm run build` (creates `dist/` folder)
2. **Backend serves**: Static files from `../frontend/dist/`

### Troubleshooting

#### Common Issues:

1. **MIME type mismatch**: Ensure the backend is properly serving static files
2. **CORS errors**: Check that the frontend URL is in the CORS origins list
3. **Build failures**: Verify all dependencies are installed

#### Debug Steps:

1. Check Render logs for backend errors
2. Verify environment variables are set correctly
3. Ensure the build command completes successfully
4. Check that the `dist/` folder is created after build

### File Structure

```
├── backend/           # Node.js backend
│   ├── config/       # Configuration files
│   ├── controllers/  # Route controllers
│   ├── models/       # Database models
│   ├── routes/       # API routes
│   └── index.js      # Main server file
├── frontend/         # React frontend
│   ├── src/         # Source code
│   ├── public/      # Static assets
│   └── dist/        # Build output (generated)
└── deploy.sh        # Deployment script
```

### API Endpoints

- `POST /api/auth/signup` - User registration
- `POST /api/auth/signin` - User authentication
- `GET /api/user/current` - Get current user
- `POST /api/user/asktoassistant` - AI assistant interaction

### Technologies Used

- **Frontend**: React, Vite, Tailwind CSS
- **Backend**: Node.js, Express, MongoDB
- **Authentication**: JWT with cookies
- **AI**: Google Gemini API
- **Deployment**: Render

## 📝 Notes

- The backend now serves the frontend static files
- CORS is configured for both development and production
- Health check endpoint available at `/api/auth/health`
- Error handling middleware included