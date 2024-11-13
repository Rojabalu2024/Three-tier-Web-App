# Use a base image with Python
FROM python:3.12-slim

# Set the working directory
WORKDIR /app
# Install PostgreSQL client libraries for psycopg2
RUN apt-get update && apt-get install -y libpq-dev gcc && rm -rf /var/lib/apt/lists/*


# Copy requirements and install dependencies
COPY requirements.txt .
RUN pip install -r requirements.txt

# Copy the rest of the application code
COPY . .

# Expose the port your app runs on
#EXPOSE 8000

# Run the app with Gunicorn
CMD ["gunicorn", "-w", "4", "app:app", "--bind", "0.0.0.0:8000"]
