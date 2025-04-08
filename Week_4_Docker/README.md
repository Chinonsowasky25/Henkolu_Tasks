## Checking the Docker version
After Installing Docker and checking the docker version with docker --version

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20112202.png?raw=true)

Run Hello-world and explain the output

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20114946.png?raw=true)

## Output Explanation:
- Docker searches for the hello-world image locally.
- If not found, it pulls the image from Docker Hub.
- It creates and runs a container from the image.
- The container executes the built-in script, prints a message, and exits.

## Write a Dockerfile for a Flask or Node.js App

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20115310.png?raw=true)

## Push Image to Docker Hub
    First, we login into my dockerhub account
    
![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20115519.png?raw=true)

Next, Build the image, with this command

docker build -t chinonso-dock/flask-app  

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20120358.png?raw=true)

We check the image with docker images

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20120732.png?raw=true)


Next, we push the newly built image to dockerhub, docker push chinonso-dock/flask-app

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%20(64).png?raw=true)


After the push command, we check my dockerhub accounts for the images.

## Create a container that persists data using volumes.
To persist data, we use Docker volumes.
Create a volume
docker volume create flask-data
Run the Flask Container with the Volume
docker run -d -p 5000:5000 -v flask-data:/app chinonso-dock/flask-app

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20122104.png?raw=true)

-v flask-data:/app → Mounts the volume inside the container at /app, ensuring data persists.


## Connect Two Containers Using a Custom Docker Network
- docker network create mynetwork
- Run a PostgreSQL Container in the Network
- Run Flask App in the Same Network

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20122849.png?raw=true)

Running a PostgreSQL container is not required unless your Flask app needs a database. I included it as an example of connecting two containers in a custom Docker network.
If the Flask app interacts with a database (e.g., storing user data, blog posts, etc.), then you need a database container like PostgreSQL or MySQL.

![image](https://github.com/user-attachments/assets/26091fdc-9f7f-45f7-b939-fac52dcf5e76)


## Verify Network Connections

![image alt](https://github.com/Chinonsowasky25/Henkolu_Tasks/blob/master/Week_4_Docker/Screenshot%202025-03-29%20123520.png?raw=true)





