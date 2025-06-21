# Solution for SRE Challenge

## How to run the code locally

1. Install dependencies:
   ```sh
   pip install -r requirements.txt
   ```
2. Run the FastAPI app locally:
   ```sh
   uvicorn main:app --reload
   ```

## How to build and push the Docker image

1. Build the Docker image:
   ```sh
    git tag v1.0.0 
    git push --tags
   ```

## How to deploy the application

- Go to the CD workflow: [GitHub Actions CD Workflow Example](https://github.com/afarid/sre-challenge/actions/workflows/cd.yaml) 
- Click on run workflow and specify the version and environment that you want to deploy on.   

## How to verify the application is running

1. Get the service URL:
   ```sh
   kubectl get svc sre-challenge
   ```
2. Curl the endpoint:
   ```sh
   curl http://<service-ip>:<port>/
   ```

## Security and Best Practices
- Environment variables are managed via Kubernetes secrets and Helm values.
- Sensitive values are not hardcoded.
- Centeralized secret management using External secrets operator or Vault.  


## Branch Protection (to be set in GitHub repository settings):
- Require PR reviews before merging to main
- Require status checks to pass (lint, test, coverage)
- Restrict who can push to main