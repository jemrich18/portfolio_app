# Jeremiah Emrich - Portfolio

A modern Django portfolio website showcasing my skills, projects, and experience as a Django Developer.

## Features

- Modern, responsive design
- About Me section
- Skills showcase
- Resume download
- GitHub integration
- Mobile-friendly

## Tech Stack

- Django 6.0.1
- Python 3.12
- WhiteNoise for static files
- Gunicorn for production server

## Local Development

1. Clone the repository:
```bash
git clone <your-repo-url>
cd portfolio_app
```

2. Create and activate virtual environment:
```bash
python -m venv env
env\Scripts\activate  # Windows
source env/bin/activate  # Linux/Mac
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Run migrations:
```bash
python manage.py migrate
```

5. Create a superuser (optional):
```bash
python manage.py createsuperuser
```

6. Run development server:
```bash
python manage.py runserver
```

Visit `http://127.0.0.1:8000/` to view the portfolio.

## Deployment to Railway

1. **Push to GitHub**:
   - Initialize git repository: `git init`
   - Add files: `git add .`
   - Commit: `git commit -m "Initial commit"`
   - Push to GitHub

2. **Deploy on Railway**:
   - Go to [Railway.app](https://railway.app)
   - Click "New Project"
   - Select "Deploy from GitHub repo"
   - Choose your repository
   - Railway will automatically detect Django and deploy

3. **Set Environment Variables in Railway**:
   - `SECRET_KEY`: Generate a new secret key for production
   - `DEBUG`: Set to `False`
   - `ALLOWED_HOSTS`: Add your Railway domain (e.g., `yourapp.railway.app`)

4. **Generate a new SECRET_KEY**:
```python
python -c "from django.core.management.utils import get_random_secret_key; print(get_random_secret_key())"
```

5. Railway will automatically:
   - Run migrations
   - Collect static files
   - Start the Gunicorn server

## Environment Variables

Create a `.env` file for local development (already in .gitignore):

```
SECRET_KEY=your-secret-key-here
DEBUG=True
ALLOWED_HOSTS=localhost,127.0.0.1
```

## Project Structure

```
portfolio_app/
├── portfolio/              # Django project settings
│   ├── settings.py        # Project settings (production-ready)
│   ├── urls.py            # URL configuration
│   └── wsgi.py            # WSGI application
├── portfolio_app/         # Main application
│   ├── static/            # Static files (CSS, images, resume)
│   ├── templates/         # HTML templates
│   ├── views.py           # View functions
│   └── urls.py            # App URL patterns
├── requirements.txt       # Python dependencies
├── Procfile              # Railway/Heroku deployment
├── railway.json          # Railway configuration
└── runtime.txt           # Python version
```

## License

© 2026 Jeremiah Emrich. All rights reserved.
