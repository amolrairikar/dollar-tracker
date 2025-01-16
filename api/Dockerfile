FROM python:3.12-slim

# Set the working directory in the container
WORKDIR /api

# Install PostgreSQL development libraries and build essentials
RUN apt-get update && apt-get install -y \
    libpq-dev \
    build-essential \
    && rm -rf /var/lib/apt/lists/*

# Install pipenv
RUN pip install --no-cache-dir pipenv

# Copy only Pipfile and Pipfile.lock to leverage Docker caching
COPY Pipfile Pipfile.lock /api/

# Install dependencies from Pipfile.lock
RUN pipenv install --system --deploy --ignore-pipfile

# Copy the rest of the application code
COPY . /api/

# Command to run the application
CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
