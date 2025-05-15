# 🐳 Container Deployment With Library Pipeline

This folder contains Azure DevOps pipeline templates and configurations for deploying containerized applications with a library to virtual machines.

## 📄 Files

### 📋 pipeline-deploy-container-with-library.yml

A complete pipeline definition for building and deploying containerized applications with a library. This pipeline:

1. Builds and pushes a Docker image to Azure Container Registry
2. Deploys the container to a development environment
3. Deploys the container to a production environment (after successful deployment to development)

#### ⚙️ Pipeline Configuration

- **🔄 Trigger**: Automatically runs on changes to the `develop` branch and files in the `containerFolder` directory
- **🔧 Variables**: Configurable settings for container name, registry, ports, and environment details
- **📦 Stages**:
  - **🏗️ Build**: Builds and pushes the Docker image
  - **🚀 DeployToDev**: Deploys to the development environment
  - **🌐 DeployToProd**: Deploys to the production environment

## 📝 Usage

1. Copy this file to your Azure DevOps repository
2. Customize the variables in `pipeline-deploy-container-with-library.yml` to match your project requirements
3. Set up the necessary service connections in your Azure DevOps project
4. Configure your deployment environments and virtual machines
5. Reference this pipeline in your Azure DevOps project
6. Create a variable group with the following variables:
   | Variable | Example Value |
   |----------|---------------|
   | containerName | 'containerName' |
   | containerRegistry | 'example.azurecr.io' |
   | containerTag | '$(Build.BuildId)' |
   | containerPort | '8000' |
   | servicePort | '8000' |
   | registryServiceConnection | '************************ID************' |
   | devEnvironment | 'development' |
   | devEnvironmentVM | 'server-dev' |
   | prodEnvironment | 'production' |
   | prodEnvironmentVM | 'server-prod' |
   | dockerfilePath | '$(Build.SourcesDirectory)/containerFolder/Dockerfile' |
   | dockerRegistryServiceConnection | '************************ID************' |
   | vmImageName | 'ubuntu-latest' |