# Django GitHub Automatic Deployment on Azure VM

This project is a production-ready Django setup using SQLite, optimized for performance and designed for automatic deployment via GitHub Actions to an Azure VM. Suitable for up to 20 learners.

## Features
- Django with SQLite (easy setup, suitable for small groups)
   - Waitress for WSGI production server (Windows compatible)
- WhiteNoise for static file serving
- Environment variable management with python-dotenv
- GitHub Actions workflow for CI/CD to Azure VM
- Security and performance best practices

## Quick Start
1. Clone the repository and install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
2. Run migrations and create a superuser:
   ```sh
   python manage.py migrate
   python manage.py createsuperuser
   ```
3. Collect static files:
   ```sh
   python manage.py collectstatic
   ```
4. Run locally:
   ```sh
   python manage.py runserver
   ```

## Deployment

Configure your Azure Windows VM with Python and Waitress.
   - Install NSSM (Non-Sucking Service Manager) to run Django as a Windows service.
   - Set up WinRM and add your VM credentials as GitHub repository secrets (`AZURE_VM_HOST`, `AZURE_VM_USER`, `AZURE_VM_PASSWORD`).
   - Push to main branch to trigger deployment.

## Scaling & Performance
   - Use Waitress with multiple threads (recommended: 4-8 for 20 users)
- Enable WhiteNoise for static files
- Use environment variables for secrets
- Monitor resource usage on Azure VM

## Security
- Set `DEBUG = False` in production
- Use strong, unique `SECRET_KEY`
- Restrict `ALLOWED_HOSTS` to your domain/IP

## For 20 Learners
- Each learner can have their own branch or app
- Use SQLite for simplicity, but consider PostgreSQL for larger groups

---


## Running as a Windows Service (Production)

1. Install NSSM on your Azure VM: https://nssm.cc/download
2. Register Django with Waitress as a service:
   - Service name: `django`
   - Path: `python.exe`
   - Arguments: `-m waitress --port=8000 githubdeploy.wsgi:application`
   - Startup directory: your project folder
3. Use `nssm restart django` to restart after deployment.

See `.github/workflows/deploy.yml` for CI/CD setup.
