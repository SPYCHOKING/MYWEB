# ProWebSec - Django Web Application

## Overview
ProWebSec is a Django-based web application for a web security and development business. The application provides information about web development and security services, with pages for home, about, services, contact, pricing, and bug reports.

**Current State**: Fully configured with professional styling, animations, and enhanced security features.

## Recent Changes (December 8, 2025)
- **Enhanced Styling**: Added professional CSS animations including fade-in, slide-in, bounce effects
- **Pricing Page**: Completely redesigned with modern pricing cards and maintenance plans
- **Security Headers**: Added comprehensive security settings (XSS filter, content-type nosniff, referrer policy)
- **JavaScript Enhancements**: Added scroll progress bar, back-to-top button, parallax effects, ripple animations
- **Fixed Links**: Corrected all navigation links across templates to use Django URL patterns
- **Active Nav Highlighting**: Navigation now highlights the current page

## Project Architecture

### Technology Stack
- **Framework**: Django 4.2
- **Python**: 3.10
- **Database**: SQLite (development)
- **Static Files**: WhiteNoise middleware
- **Web Server**: 
  - Development: Django's built-in server (port 5000)
  - Production: Gunicorn

### Directory Structure
```
MYWEB/                 # Main Django project
├── settings.py        # Django settings (configured for Replit + security)
├── urls.py           # URL routing
├── wsgi.py           # WSGI application
main/                 # Main app
├── models.py         # ContactMessage model
├── views.py          # View functions
├── migrations/       # Database migrations
templates/            # HTML templates
├── index.html        # Homepage with hero section
├── about.html        # About page with team section
├── service.html      # Services page with service cards
├── contact.html      # Contact form page
├── pricing.html      # Pricing packages page
├── bug_reports.html  # Bug reports page
├── thank-you.html    # Thank you page
static/               # Static files
├── css/             # Stylesheets
│   └── style.css    # Main styles (1600+ lines)
└── script.js        # JavaScript (350+ lines)
```

### Key Features
1. **Contact Form**: Saves contact submissions to database via ContactMessage model
2. **Responsive Design**: Mobile-first with hamburger menu
3. **Professional Animations**: Scroll animations, hover effects, parallax
4. **Security Features**: 
   - CSRF protection on all forms
   - Security headers configured
   - XSS filter enabled
   - Content-Type nosniff
5. **Admin Interface**: Django admin available at /admin/

### Database Schema
- **ContactMessage Model**:
  - name (CharField)
  - email (EmailField)
  - phone (CharField, optional)
  - service (CharField, optional)
  - message (TextField)
  - date_submitted (DateTimeField, auto)

## Development

### Running Locally
The Django development server is configured to run automatically on `0.0.0.0:5000`. The workflow "Django Web Server" handles this.

### Admin Access
- URL: `/admin/`
- Username: `admin`
- Password: `admin123`

### Database
The project uses SQLite for development. All migrations are already applied.

### Static Files
Static files are managed by WhiteNoise:
- Development: Files served from `static/` directory
- Production: Files collected to `staticfiles/` directory

To recollect static files:
```bash
python manage.py collectstatic --noinput
```

## Deployment
The project is configured for autoscale deployment using Gunicorn:
- **Build command**: Collects static files
- **Run command**: Gunicorn on port 5000 with reuse-port option
- **Target**: Autoscale (suitable for stateless web applications)

## Configuration Notes

### Security Settings (MYWEB/settings.py)
- `SECURE_CONTENT_TYPE_NOSNIFF = True`
- `SECURE_BROWSER_XSS_FILTER = True`
- `SECURE_REFERRER_POLICY = 'strict-origin-when-cross-origin'`
- `SESSION_COOKIE_HTTPONLY = True`
- `CSRF_COOKIE_HTTPONLY = True`

### Replit-Specific Settings
- `ALLOWED_HOSTS = ['*']` - Accepts all hosts
- `CSRF_TRUSTED_ORIGINS` - Configured for Replit domains
- `SECURE_PROXY_SSL_HEADER` - Configured for HTTPS proxy
- `X_FRAME_OPTIONS = 'ALLOWALL'` - Allows iframe embedding for Replit preview

### For Production Deployment
Before deploying to production, configure:
- `SECRET_KEY` - Use environment variable
- `DEBUG = False`
- `ALLOWED_HOSTS` - Restrict to specific domains
- `SESSION_COOKIE_SECURE = True`
- Consider PostgreSQL instead of SQLite

## URLs
- `/` - Homepage
- `/about/` - About page
- `/service/` - Services page
- `/contact/` - Contact form
- `/pricing/` - Pricing page
- `/bug_reports/` - Bug reports page
- `/thank-you/` - Thank you page
- `/admin/` - Django admin interface

## User Preferences
- Professional web development and security business theme
- Purple/blue gradient color scheme
- Modern, clean design with animations
- Indian Rupee (₹) pricing
