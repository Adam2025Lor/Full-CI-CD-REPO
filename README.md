Project 3: Full CI/CD Pipeline with GitHub Actions, Docker & Helm
 
Process & Steps
Repository Setup:
Created a new GitHub repository to manage all project code and workflows.

Application & Dockerization:
Developed a simple Flask application (flaskapp.py).
Created a Dockerfile to containerize the Flask app.

Helm Chart:
Created a Helm chart named foo to deploy the application on Kubernetes.
Configured values.yaml to pull the Docker image and set app configurations.

Docker Image Management:
Built the Docker image locally.
Pushed the image to Docker Hub for deployment.

Git Integration:
Pushed all project files and Helm chart to the GitHub repository.
Established a clear Git workflow with branches and versioning.

CI with GitHub Actions:
Configured GitHub Actions to:
Use matrix builds to test the app with different Python versions (via pylint).
Run the linting step on code changes to main.

CD with GitHub Actions:
After successful tests, the CD process:
Builds a Docker image with a tag based on git sha.
Deploys the Helm chart to a local Kubernetes cluster via a GitHub self-hosted runner.

Full Pipeline Flow
A developer pushes code to the main branch.
GitHub Actions triggers a CI workflow:
Tests Python code style using pylint with matrix builds (3.9, 3.10).

If CI succeeds:
Docker image is built and tagged with the commit SHA.
GitHub Action logs in to Docker Hub.
CD pipeline deploys the Helm chart using helm upgrade --install.



Git Branching Strategy and Workflow
To manage version control effectively, I used a simple branching model:
main branch contains production-ready code.
Feature branches (Test, Dev) are used for development.
All feature branches are merged into main via pull requests after successful CI checks. GitHub Actions automatically runs the CI pipeline (tests and linting) on every push to the Main branch or pull requests. 
Merge conflicts were resolved manually when they occurred.
