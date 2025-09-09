# 🚀 Nepal Office Tracker - Deployment Guide

## 📋 Quick Deploy Options

### 🚂 Backend Deployment (Choose One)

#### Option 1: Railway (Recommended)
1. Visit [railway.app](https://railway.app)
2. Connect your GitHub account
3. Click "Deploy from GitHub repo"
4. Select: `a0neup03/nepal-office-tracker`
5. Railway will automatically detect `railway.json` config
6. Backend will be live at: `https://your-app.railway.app`

#### Option 2: Render
1. Visit [render.com](https://render.com)
2. Connect GitHub and select the repo
3. Choose "Web Service"
4. Render will detect `render.yaml` config
5. Backend will be live at: `https://your-app.onrender.com`

### 🌐 Frontend Deployment (Choose One)

#### Option 1: Vercel (Recommended)
1. Visit [vercel.com](https://vercel.com)
2. Import project from GitHub: `a0neup03/nepal-office-tracker`
3. Set Root Directory: `webapp_frontend`
4. Vercel will detect `vercel.json` config
5. Frontend will be live at: `https://your-app.vercel.app`

#### Option 2: Netlify
1. Visit [netlify.com](https://netlify.com)
2. Connect GitHub and select the repo
3. Netlify will detect `netlify.toml` config
4. Set build directory: `webapp_frontend`
5. Frontend will be live at: `https://your-app.netlify.app`

## 🔧 Environment Variables

### Backend Environment Variables
Set these in your deployment platform:

```
DATABASE_URL=sqlite:///./nepal_office_tracker.db
SECRET_KEY=your-super-secret-key-here
CORS_ORIGINS=https://your-frontend-url.vercel.app
```

### Frontend Environment Variables
Update in your frontend deployment:

```
REACT_APP_API_BASE_URL=https://your-backend-url.railway.app
```

## 📊 Project Structure

```
nepal-office-tracker/
├── webapp_backend/          # FastAPI Backend
│   ├── main.py             # Main FastAPI app
│   ├── models/             # Database models
│   ├── api/                # API routes
│   └── requirements.txt    # Python dependencies
├── webapp_frontend/         # React Frontend
│   ├── src/                # React components
│   ├── public/             # Static files
│   └── package.json        # Node dependencies
├── railway.json            # Railway config
├── render.yaml             # Render config
└── Procfile                # Heroku/Railway process
```

## ✅ Deployment Checklist

- [x] GitHub repository created: `https://github.com/a0neup03/nepal-office-tracker`
- [x] Backend configs ready (Railway, Render, Procfile)
- [x] Frontend configs ready (Vercel, Netlify)
- [ ] Deploy backend to Railway/Render
- [ ] Deploy frontend to Vercel/Netlify
- [ ] Update CORS origins in backend
- [ ] Update API URL in frontend
- [ ] Test complete system

## 🔗 Expected URLs

After deployment:
- **Backend API**: `https://your-backend.railway.app`
- **Frontend App**: `https://your-frontend.vercel.app`
- **API Docs**: `https://your-backend.railway.app/docs`

## 🧪 Testing Deployment

1. Visit frontend URL
2. Test district selection
3. Test office selection
4. Test timer functionality
5. Test rating system
6. Check analytics dashboard

## 📝 Next Steps

1. **Deploy Backend**: Choose Railway or Render
2. **Deploy Frontend**: Choose Vercel or Netlify
3. **Configure Environment**: Update CORS and API URLs
4. **Custom Domain**: Add custom domain (optional)
5. **Monitor**: Check logs and analytics

---

🇳🇵 **Ready to track Nepal government office experiences!**