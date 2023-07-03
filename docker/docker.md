# [Home](../README.md) > Docker


1. Show all Docker images
   ```bash
   docker image ls
   ```

2. Run a Docker image
   ```bash
   docker run -p <some port>:<some port> --name <some name> <container id>
   # Replace <some port> with the desired port number, <some name> with the desired container name, and <container id> with the ID of the container image.
   ```

3. Run Docker with AWS profile
   ```bash
   docker run -v <aws root credentials files> -e AWS_PROFILE=<profile-name> <container id>
   # Replace <aws root credentials files> with the path to your AWS root credentials files, <profile-name> with the desired AWS profile name, and <container id> with the ID of the container image.
   ```

4. Build a Docker image
   ```bash
   docker build -t <container id> .
   # Replace <container id> with the desired name or tag for the Docker image.
   ```

5. Remove a Docker image
   ```bash
   docker rmi <container id>
   # Replace <container id> with the ID or name of the Docker image you want to remove.
   ```

6. Show all running and stopped containers
   ```bash
   docker ps -a
   ```

7. Tag an ECR image with local image :latest tag
   ```bash
   docker tag <container id>:latest <ecr URI>:latest
   # Replace <container id> with the ID or name of the local Docker image and <ecr URI> with the URI of the ECR repository.
   ```

8. Login to AWS ECR from CLI
   ```bash
   aws ecr get-login-password --region $AWS_REGION | docker login --username AWS --password-stdin <ecr repo id>.dkr.ecr.<region>.amazonaws.com
   # Replace <ecr repo id> with the ID of the ECR repository and <region> with the AWS region.
   ```
   example
   ```bash
    aws ecr get-login-password --region $AWS_REGION | docker login --username AWS --password-stdin 043337637715.dkr.ecr.us-west-2.amazonaws.com
    ```

9. Push a local directory image to ECR
   ```bash
   docker push <ecr URI>:latest
   # Replace <ecr URI> with the URI of the ECR repository.
   ```
   example
   ```
   docker push 043337637715.dkr.ecr.us-west-2.amazonaws.com/fx-get-backtest-prices:latest
   ```

10. Tag an ECR image with local image :latest: tag
    ```bash
    docker tag <container id>:latest <ecr URI>:latest
    # Replace <container id> with the ID or name of the local Docker image and <ecr URI> with the URI of the ECR repository.
    ```
    example
    ```bash
    docker tag fx-get-backtest-prices:latest 043337637715.dkr.ecr.us-west-2.amazonaws.com/fx-get-backtest-prices:latest
    ```
