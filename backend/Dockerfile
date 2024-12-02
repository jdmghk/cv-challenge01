# Use Python 3.9 slim as the base image
FROM python:3.10-slim

# Set working directory in the container
WORKDIR /app

# Install system dependencies
RUN apt-get update -y && \
    apt-get install -y --no-install-recommends \
    curl \
    && rm -rf /var/lib/apt/lists/*

# Install Poetry
RUN curl -sSL https://install.python-poetry.org | python3 -

# Add Poetry to the PATH
ENV PATH="/root/.local/bin:$PATH"

# Copy the rest of the application code into the container
COPY . /app

# Install the dependencies using Poetry
RUN poetry install

# Make the prestart script executable
RUN chmod +x ./prestart.sh

# Expose port 8000
EXPOSE 8000

# Command to run the application
CMD ["sh", "-c", "poetry run bash ./prestart.sh && poetry run uvicorn app.main:app --host 0.0.0.0 --port 8000 --reload"]