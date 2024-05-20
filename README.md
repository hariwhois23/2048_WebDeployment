**2048 Game Containerization and Deployment using Docker and AWS Elastic Beanstalk**





<img width="1470" alt="Screenshot 2024-05-20 at 11 57 05 AM" src="https://github.com/hariwhois23/2048_WebDeployment/assets/117026847/0d77731d-cd1d-436c-9116-3bcdf8baf2ee">


This documentation provides a step-by-step guide to containerize the 2048 game using Docker and deploy it on the web using AWS Elastic Beanstalk.

# Step 1: Clone the 2048 Game Repository

Clone the 2048 game repository to your local machine:

$ git clone https://github.com/gabrielecirulli/2048.git


# Step 2: Create a Dockerfile

Create a Dockerfile in the root directory of the cloned repository: Dockerfile

The Dockerfile is available in this following github repository.

# Step 3: Build the Docker Image

Build the Docker image for the 2048 game:

$ docker build -t 2048.0-game .

# Step 4: Run the Docker Container Locally

Run the Docker container to ensure the game works locally:

$ docker run -p 8080:80 2048-game

Visit http://localhost:8080 in your browser to verify.

# Step 5: Set Up AWS Elastic Beanstalk

Initialize Elastic Beanstalk in your project directory:

$ eb init
Follow the prompts to configure Elast ic Beanstalk. Ensure you select the correct region and platform (Docker).


# Step 6: Create a Docker Configuration File

Create a Dockerrun.aws.json file in the root directory:

The following json file is available on this github repository

# Step 7: Deploy to AWS Elastic Beanstalk

Deploy the Docker container to AWS Elastic Beanstalk:

$ eb create 2048-game-env

Monitor the deployment process. Once complete, Elastic Beanstalk will provide a URL where your 2048 game is hosted.

# Step 8: Open the Application

Open the provided URL in your web browser to see the deployed 2048 game.
