# Deployment Checklist for Railway

## Before Deployment

- [x] Created requirements.txt with all dependencies
- [x] Updated settings.py for production (environment variables, WhiteNoise)
- [x] Created .gitignore to exclude sensitive files
- [x] Created .env for local development
- [x] Created Procfile for Railway
- [x] Created railway.json configuration
- [x] Added runtime.txt with Python version

## Deployment Steps

### 1. Initialize Git Repository

```bash
git init
git add .
git commit -m "Initial commit - Portfolio app ready for deployment"
```

### 2. Create GitHub Repository

1. Go to GitHub.com
2. Create a new repository (e.g., "portfolio-django")
3. Push your code:

```bash
git remote add origin https://github.com/yourusername/portfolio-django.git
git branch -M main
git push -u origin main
```

### 3. Deploy to Railway

1. Go to https://railway.app and sign in with GitHub
2. Click "New Project"
3. Select "Deploy from GitHub repo"
4. Choose your portfolio repository
5. Railway will automatically detect it's a Django app

### 4. Set Environment Variables in Railway

Click on your project > Variables tab, and add:

**Required Variables:**
```
SECRET_KEY=<generate-new-secret-key>
DEBUG=False
ALLOWED_HOSTS=.railway.app
```

**To generate a new SECRET_KEY:**
```bash
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

### 5. Deploy & Monitor

- Railway will automatically build and deploy your app
- Check the deployment logs for any errors
- Once deployed, you'll get a URL like: `https://your-app.railway.app`

### 6. Post-Deployment

1. Visit your Railway URL
2. Test all pages (Home, About, Skills)
3. Test Resume download
4. Test GitHub link
5. Check on mobile devices

## Optional: Custom Domain

1. Purchase a domain (e.g., from Namecheap, Google Domains)
2. In Railway: Settings > Domains
3. Add your custom domain
4. Update your domain's DNS settings with Railway's provided records
5. Update ALLOWED_HOSTS in Railway environment variables to include your domain

## Troubleshooting

### Static files not loading?
- Check that WhiteNoise is in MIDDLEWARE
- Run: `python manage.py collectstatic` locally to test
- Check Railway deployment logs

### 500 Internal Server Error?
- Check Railway logs
- Verify all environment variables are set
- Ensure DEBUG=False in production

### Database issues?
- Railway automatically provides PostgreSQL if needed
- For SQLite (current setup), database will reset on each deployment
- Consider adding PostgreSQL for persistent data

## Need Help?

- Railway Docs: https://docs.railway.app/
- Django Deployment: https://docs.djangoproject.com/en/6.0/howto/deployment/
- Check Railway logs for errors

---

**Note**: Remember to never commit your `.env` file or expose your SECRET_KEY!
