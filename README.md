# adazza-ci-docker [![build status](https://codebuild.us-east-1.amazonaws.com/badges?uuid=eyJlbmNyeXB0ZWREYXRhIjoid1hzeUMrQ0FQSlJVcjY5WG5HdWRlUzZNRWx1WWlMTXhleEJsMUlHbUpOUFdiWm4rVmN5alZOekVnKys2QTRqZ0pROXRCeGFJbGpqYmE0K1g3ZGxrOHlZPSIsIml2UGFyYW1ldGVyU3BlYyI6InMwTUR6VC94VWplQm5aRkwiLCJtYXRlcmlhbFNldFNlcmlhbCI6MX0%3D&branch=master)](https://console.aws.amazon.com/codesuite/codebuild/projects/adazza-ci-docker/history?region=us-east-1) [![lerna](https://img.shields.io/badge/maintained%20with-lerna-cc00ff.svg)](https://lernajs.io/)


Dockerfiles for CI/CD container images

## Registry

<https://console.aws.amazon.com/ecs/home>

This repo helps automate the baking of images for the ECR registry adazza-ci-ecr.  From the name you may intuit that these are Docker container images meant for continuous integration and deployment.

This repo includes a meta image `adazza-ci-docker` which is the Docker image that builds all Docker images (including itself).  If you mess this image up, you are solely responsible for fixing it :trollface:.

## Development

The common cases are 

- Updating an existing image
- Creating a new image

### Updating an existing image

This is straightforward - find the relevant directory under `./images/` and update the `Dockerfile` in question.  Once committed to `master` (via PR of course), it will be built and published to ECR.

### Creating a new image

Unfortunately this sort of requires having node/npm installed (or manually creating a `package.json` file, whichever you believe is easier):

1. Create a new directory for your container image
    - e.g. `mkdir -p images/adazza-awesome-ci-image`
1. Go to your directory
    - e.g., `pushd images/adazza-awesome-ci-image`
1. Create the `package.json` file
    - e.g., `npm init` and press `enter` several times (or create it manually!)
1. Create the `Dockerfile`
1. Return to the root of the project
    - e.g., `popd`
1. Test building locally
    - TODO: add an npm script for local docker build
1. Open a PR, commit to master, and your image will be built & published
