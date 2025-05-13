# 🎯 Full-Stack React + Python Web App

A full-stack web application using a React frontend and Python backend (FastAPI).

## 📝 Overview

This project provides a modern web application structure with a React frontend and Python backend. The frontend handles the user interface and interactions, while the backend manages data processing, business logic, and API endpoints.

## ⚙️ Tech Stack

- 🧠 **Backend**: FastAPI (or Flask/Django)
- 💻 **Frontend**: React.js
- ☁️ **Deployment**: Render (backend) & Vercel (frontend)

## 🏗️ Project Structure

```
web-app/
├── frontend/          # React frontend application
└── backend/           # Python backend application
    ├── main.py        # FastAPI/Flask application entry point
    └── requirements.txt
```

## ✅ Prerequisites

Before deployment, ensure you have:

- Complete React app in the `frontend/` folder
- Complete Python backend app in the `backend/` folder with:
  - `main.py` (FastAPI/Flask/Django application)
  - `requirements.txt` (Python dependencies)
- A GitHub account

## 🚀 Deployment Guide

### 1. Deploy Backend on Render

1. Push your `backend/` folder to a GitHub repository
2. Go to [Render](https://render.com) and sign in
3. Click on "New Web Service"
4. Connect your GitHub backend repository
5. Configure the service:
   - **Name**: Choose a name for your service (e.g., `myapp-api`)
   - **Environment**: Python 3.11 (or your preferred version)
   - **Build Command**: `pip install -r requirements.txt`
   - **Start Command**: 
     - For FastAPI: `uvicorn main:app --host 0.0.0.0 --port 10000`
     - For Flask: `gunicorn main:app`
     - For Django: `gunicorn myproject.wsgi:application`
   - **Plan**: Free (or choose paid plan for better performance)
6. Click "Create Web Service"
7. Wait for deployment to complete
8. Copy your live backend URL: `https://your-backend.onrender.com`

### 2. Update Frontend API URL

Update your React app (`frontend/src/App.js` or appropriate file) to use the new backend URL:

**Option 1**: Directly update the API calls:
```js
axios.get("https://your-backend.onrender.com/api/data/", {
  // your request data
});
```

**Option 2**: Use an environment variable (recommended):

Create a `.env` file in your frontend directory:
```
REACT_APP_API_URL=https://your-backend.onrender.com
```

Then update your API calls:
```js
axios.get(`${process.env.REACT_APP_API_URL}/api/data/`, { 
  // your request data
});
```

### 3. Deploy Frontend on Vercel

1. Push your `frontend/` folder to a GitHub repository
2. Go to [Vercel](https://vercel.com) and sign in
3. Click "New Project"
4. Import your GitHub frontend repository
5. Configure the project:
   - Set root directory to `frontend` if needed
   - Add environment variables (if using `.env`):
     - Key: `REACT_APP_API_URL`
     - Value: `https://your-backend.onrender.com`
6. Click "Deploy"
7. Once deployment is complete, you'll get a live frontend URL: `https://your-app.vercel.app`

## ✅ Recommended Deployment Order

1. **Deploy Backend First** - Get the live backend URL
2. **Update Frontend** with backend URL
3. **Deploy Frontend**

## 🔧 Troubleshooting

- **CORS Issues**: Ensure your backend allows requests from your frontend domain
  ```python
  # In your FastAPI app
  from fastapi.middleware.cors import CORSMiddleware
  
  app.add_middleware(
      CORSMiddleware,
      allow_origins=["https://your-frontend-url.vercel.app"],
      allow_credentials=True,
      allow_methods=["*"],
      allow_headers=["*"],
  )
  ```
- **Environment Variables**: Double-check your environment variable configuration
- **API Endpoints**: Verify that API endpoint paths match between frontend and backend
- **Build Errors**: Check deployment logs for build-time errors
- **Runtime Errors**: Monitor application logs for runtime exceptions

## 🚩 Next Steps

- Add user authentication
- Implement result saving functionality
- Add more advanced NLP features
- Improve UI/UX with visualization of sentiment scores

## 📄 License

MIT
