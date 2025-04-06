## Checking the Docker version
After Installing Docker and checking the docker version with docker --version


Run Hello-world and explain the output



## Output Explanation:
Docker searches for the hello-world image locally.
If not found, it pulls the image from Docker Hub.
It creates and runs a container from the image.
The container executes the built-in script, prints a message, and exits.


3. Write a Dockerfile for a Flask or Node.js App



4. Push Image to Docker Hub
    First, we login into my dockerhub account


Next, Build the image, with this command

docker build -t chinonso-dock/flask-app .





We check the image with docker images



Next, we push the newly built image to dockerhub, docker push chinonso-dock/flask-app



After the push command, we check my dockerhub accounts for the images.

5. Create a container that persists data using volumes.
To persist data, we use Docker volumes.
Create a volume
docker volume create flask-data
Run the Flask Container with the Volume
docker run -d -p 5000:5000 -v flask-data:/app chinonso-dock/flask-app



-v flask-data:/app → Mounts the volume inside the container at /app, ensuring data persists.


6. Connect Two Containers Using a Custom Docker Network
docker network create mynetwork
Run a PostgreSQL Container in the Network
Run Flask App in the Same Network



Running a PostgreSQL container is not required unless your Flask app needs a database. I included it as an example of connecting two containers in a custom Docker network.
If the Flask app interacts with a database (e.g., storing user data, blog posts, etc.), then you need a database container like PostgreSQL or MySQL.



Verify Network Connections





