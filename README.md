# Flask Application

This is a Flask application template with the following structure and features:

## Project Structure

```
.
├── app/                 # Main application package
│   ├── __init__.py      # Application factory
│   ├── config.py        # Configuration classes
│   ├── extensions.py    # Extensions initialization
│   ├── models/          # Database models (empty by default)
│   ├── main/            # Main blueprint
│   │   ├── __init__.py
│   │   └── routes.py
│   └── api/             # API blueprint
│       ├── __init__.py
│       └── routes.py
├── app/templates/       # HTML templates
│   ├── base.html        # Base template
│   └── main/
│       └── index.html   # Home page
├── app/static/          # Static files
│   ├── css/
│   │   └── style.css    # Stylesheet
│   └── js/
│       └── main.js      # JavaScript
├── tests/               # Test files
│   ├── conftest.py      # Pytest fixtures
│   └── test_smoke.py    # Smoke tests
├── run.py               # Application runner
├── requirements.txt     # Python dependencies
└── .env.example         # Environment variables template

## Getting Started

To start the application:

1. Create a virtual environment:
```bash
python -m venv venv
```

2. Activate the virtual environment:
```bash
source venv/bin/activate  # On Linux/Mac
# or
venv\Scripts\activate     # On Windows
```

3. Install dependencies:
```bash
pip install -r requirements.txt
```

4. Copy and configure environment variables:
```bash
cp .env.example .env
# Edit .env to set your configuration
```

5. Run the development server:
```bash
flask --app run.py run --debug
```

## Database Initialization (optional, per-project)

This phase is run when a project actually needs the database, not as part of the base template. Documented here so future-you remembers the sequence.

Define a model in app/models/__init__.py (or a module it imports), e.g.:

```python
from app.extensions import db


class Example(db.Model):
    id = db.Column(db.Integer, primary_key=True)
    name = db.Column(db.String(120), nullable=False)
```

Then:

```bash
flask --app run.py db init      # once per project
flask --app run.py db migrate -m "initial tables"
flask --app run.py db upgrade
```

Note: the factory already imports app.models, so any model defined there is visible to Flask-Migrate automatically. If it's not picking up a model, the model's module isn't being imported — that's always the cause.

## Clone template repo

```bash
gh repo create my-new-project --template auxsophia/default_flask_app --private --clone
```