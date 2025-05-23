## Technologies Used

GitHub Actions

Docker

DockerHub

✅ Prerequisites
DockerHub account

GitHub repository

GitHub Secrets configured:

DOCKER_USERNAME

DOCKER_PASSWORD

First, In our repo, you clicked on action

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/020eac9ddc011b8e4a1abf9512a40c866759dae8/Week_6_CI-CD(Github-Actions)/DCKER1.png)
click on set up workfow yourself

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/020eac9ddc011b8e4a1abf9512a40c866759dae8/Week_6_CI-CD(Github-Actions)/DCKER2.png)

Create a .yml file(docker.yml) and write our script

# Use a lightweight base image
FROM python:3.11-slim

# Set a working directory
WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the app files
COPY . .

# Expose the port Flask runs on
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]

This GitHub Actions workflow automates the process of building and pushing a Docker image to Docker Hub whenever there is a push or pull request to the main branch.

## GitHub Secrets Required
Go to your repo → Settings → Secrets and variables → Actions → Add the following:

DOCKER_USERNAME: your Docker Hub username

DOCKER_PASSWORD: your Docker Hub password or access token

We also create app.py

from flask import Flask
app = Flask(__name__)

@app.route('/')
def home():
    return "Hello from Flask in Docker!"

This app.py file is a very basic Flask application written in Python.

We also create a Dockefile


# Use a lightweight base image
FROM python:3.11-slim

# Set a working directory
WORKDIR /app

# Install dependencies
COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

# Copy the app files
COPY . .

# Expose the port Flask runs on
EXPOSE 5000

# Run the app
CMD ["python", "app.py"]

Make sure to have a requirements.txt file:

Flask==0.10.1

After commit, we check the workflow runs and checked if it passed
![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/020eac9ddc011b8e4a1abf9512a40c866759dae8/Week_6_CI-CD(Github-Actions)/Screenshot%202025-04-14%20131417.png)

Lastly, we check dockerhub to know if our image was pushed

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/020eac9ddc011b8e4a1abf9512a40c866759dae8/Week_6_CI-CD(Github-Actions)/Screenshot%20(67).png)

