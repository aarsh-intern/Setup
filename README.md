# Project Setup & Management Guide

This README contains common commands and steps to help with setting up, running, and managing the project environment, database, and Docker containers.

---

## Python Environment (Poetry)

Set up Python environment.
```bash
poetry install                            # Install dependencies
eval $(poetry env activate)              # Activate the poetry environment
poetry self add poetry-plugin-shell      # Add shell plugin for Poetry
```

## Database Migrations (Alembic)

Use Alembic for handling database schema changes.

alembic upgrade head                     # Apply all migrations
alembic revision --autogenerate -m "Added <table>"   # Create a new migration file

## Running the API Server

Use Uvicorn to run the FastAPI app:

uvicorn app.api.v1:app --port 8080 --reload

## Pre-commit Checks

Run pre-commit hooks on all files:

pre-commit run -a

## Google Cloud Authentication

Set the path to your Google Cloud service account credentials:

export GOOGLE_APPLICATION_CREDENTIALS="</path/to/credentials.json>"

## PostgreSQL Access

Switch to the postgres user and connect to a database:

sudo -i -u postgres
\c "host=localhost port=5432 dbname=<DB_NAME> user=<USER> password=<PASSWORD>"

## Docker Commands

Build and manage Docker containers:

docker-compose up --build       # Build and start containers
docker-compose down             # Stop and remove containers
docker ps -a                    # List all containers
sudo docker system prune        # Clean up unused Docker data

## SSH Key Generation

Generate and add SSH key to the agent:

ssh-keygen -t rsa -b 4096 -C "your_email@example.com"
eval "$(ssh-agent -s)"
ssh-add ~/.ssh/<id_rsa_name>
