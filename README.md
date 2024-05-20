**2048 Game Containerization and Deployment using Docker and AWS Elastic Beanstalk**

This documentation provides a step-by-step guide to containerize the 2048 game using Docker and deploy it on the web using AWS Elastic Beanstalk.
Step 1: Clone the 2048 Game Repository

Clone the 2048 game repository to your local machine:

git clone https://github.com/gabrielecirulli/2048.git
cd 2048

Step 2: Create a Dockerfile

Create a Dockerfile in the root directory of the cloned repository:

Dockerfile

The Dockerfile is available on the following github repository.

# Expose port 8080
EXPOSE 8080

# Command to run the application
CMD ["npm", "start"]

Step 3: Build the Docker Image

Build the Docker image for the 2048 game:

docker build -t 2048-game .

Step 4: Run the Docker Container Locally

Run the Docker container to ensure the game works locally:

docker run -p 8080:8080 2048-game
Visit http://localhost:8080 in your browser to verify.

Step 5: Set Up AWS Elastic Beanstalk

Initialize Elastic Beanstalk in your project directory:

eb init
Follow the prompts to configure Elastic Beanstalk. Ensure you select the correct region and platform (Docker).


Step 6: Create a Docker Configuration File

# Create a Dockerrun.aws.json file in the root directory:

**json
**
{
  "AWSEBDockerrunVersion": 2,
  "containerDefinitions": [
    {
      "name": "2048-game",
      "image": "2048-game",
      "essential": true,
      "memory": 128,
      "portMappings": [
        {
          "containerPort": 8080,
          "hostPort": 8080
        }
      ]
    }
  ]
}

Step 7: Deploy to AWS Elastic Beanstalk

**Deploy the Docker container to AWS Elastic Beanstalk:**


**Copy code
eb create 2048-game-env
Monitor the deployment process. Once complete, Elastic Beanstalk will provide a URL where your 2048 game is hosted.
**

Step 8: Open the Application

Open the provided URL in your web browser to see the deployed 2048 game.
