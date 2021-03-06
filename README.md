# Sso

## Dependencies:

#### Common.in:

1. psycopg2

    - Install `postgresql` on your system

## Development

- `git clone REPOSITORY_LINK` # Clone the repository
- `cd sso`
- `virtualenv venv -p /path/to/python` # Create virtualenv
- `. venv/Scripts/activate` # Activate virtualenv
- `pip install pip-tools`
- `pip-compile -r requirements/develop.in -o requirements-DATE.develop` # Generates a requirements file with the latest version of the dependencies up to the current date
- `pip-sync requirements-DATE.develop` # Synchronize the dependencies and versions of your virtual environment with those of the generated file
- Open `.env` and populate variables
- Set `ENVIRONMENT_MODULE` in `.env` file, alternatives are: `develop`, `testing`, `staging` and `production`.
- `python manage.py runserver`

## Create application or client details(public key, private key) in the server side in the django shell

- `from simple_sso.sso_server.models import Token, Consumer`
- `Consumer.objects.create(public_key='your_application_public_key', private_key='your_application_private_key', name='your_application_name')`

## Run tests and generate html coverage code report

- `coverage run --source='.' manage.py test && coverage html`
- Open `htmlcov/index.html` in your browser
