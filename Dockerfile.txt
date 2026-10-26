# 1. Base Image
FROM python:3.12-slim

# 2. Set Working Directory inside container
WORKDIR /app

# 3. Copy dependencies and install
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# 4. Copy the rest of the application code
COPY . .

# 5. Expose application port
EXPOSE 5000

# 6. Command to start the application
CMD ["python", "app.py"]