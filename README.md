# 🧰 Azure DevOps Toolbox

A collection of Azure DevOps pipeline examples and tools for common DevOps scenarios. 🔭 Learn how to get started with Azure DevOps Toolbox and then dive deeper into other advanced topics.

<p>
  <img alt="AzureDevOps" src="https://img.shields.io/badge/Azure%20DevOps-blue?style=flat-square" />
  <img alt="Bash" src="https://img.shields.io/badge/-Bash-grey?style=flat-square&logo=gnubash&logoColor=white" />
  <img alt="Docker" src="https://img.shields.io/badge/-Docker-46a2f1?style=flat-square&logo=docker&logoColor=white" />
  <img alt="Kubernetes" src="https://img.shields.io/badge/Kubernetes-%23326CE5?style=flat-square&logo=kubernetes&logoColor=white" />
  <img alt="Amazon EKS" src="https://img.shields.io/badge/Amazon%20EKS-%23FF9900?style=flat-square&logo=amazoneks&logoColor=white" />
</p>

## 📑 Table of Contents

- [Overview](#overview)
- [Repository Structure](#repository-structure)
  - [deploy-container](#deploy-container)
  - [deploy-container-with-library](#deploy-container-with-library)
  - [deploy-eks](#deploy-eks)
  - [deploy-on-prem-kubernetes](#deploy-on-prem-kubernetes)
  - [deploy-with-library](#deploy-with-library)
  - [notify-pull-request-reviewers](#notify-pull-request-reviewers)
- [Key Concepts](#key-concepts)
- [Usage](#usage)
- [Contributing](#contributing)

## 🔍 Overview

The Azure DevOps Toolbox is a comprehensive collection of reusable pipeline templates, configurations, and tools designed to accelerate DevOps workflows in Azure DevOps. This repository serves as a reference implementation for common DevOps scenarios, providing ready-to-use solutions that can be adapted to specific project requirements.

The toolbox includes solutions for:
- Container deployment to virtual machines
- Container deployment with Azure DevOps Library for secure environment variables
- Kubernetes deployment to Amazon EKS
- Kubernetes deployment to on-premises clusters
- Kubernetes deployment with Azure DevOps Library for secure environment variables
- Pull request notification automation via Microsoft Teams

Each solution is documented with detailed explanations, usage instructions, and diagrams to facilitate implementation.

## 📂 Repository Structure

This repository contains the following folders, each with specific Azure DevOps pipeline examples and tools:

### 🐳 [deploy-container](./deploy-container)

Tools and pipelines for deploying containerized applications to virtual machines.

- **deploy-container-job.yml**: Reusable template for container deployment jobs
- **pipeline-deploy-container.yml**: Complete pipeline for building and deploying containers to development and production environments

### ☸️ [deploy-eks](./deploy-eks)

Tools and pipelines for deploying applications to Amazon EKS (Elastic Kubernetes Service).

- **pipeline-deploy-kubernetes.yml**: Pipeline for deploying applications to Kubernetes clusters

### ☸️ [deploy-on-prem-kubernetes](./deploy-on-prem-kubernetes)

Tools and pipelines for deploying containerized applications to on-premises Kubernetes clusters.

- **pipeline-deploy-kubernetes.yml**: Pipeline for building Docker images and deploying them to on-premises Kubernetes clusters with dynamic manifest generation

### 📚 [deploy-container-with-library](./deploy-container-with-library)

Tools and pipelines for deploying containerized applications with a library to virtual machines.

- **pipeline-deploy-container-with-library.yml**: Complete pipeline for building and deploying containers with a library to development and production environments

### 📚 [deploy-with-library](./deploy-with-library)

Tools and pipelines for deploying containerized applications to Kubernetes clusters using the Azure DevOps Library for secure management of environment variables.

- **pipeline-deploy-with-library.yml**: Pipeline for building Docker images and deploying them to Kubernetes clusters with environment variables from secure files

### 📢 [notify-pull-request-reviewers](./notify-pull-request-reviewers)

Tools for automating pull request notifications to reviewers via Microsoft Teams.

- **adaptive-card-teams.json**: Adaptive Card template for Teams notifications
- **azure-devops-pull-request-notification.json**: Azure Logic App workflow definition for sending notifications

## 🔑 Key Concepts

### 📋 Pipeline Templates

Pipeline templates are reusable components that define common job patterns. They help standardize deployment processes across multiple pipelines and reduce duplication. In this repository, templates like `deploy-container-job.yml` encapsulate complex deployment logic that can be referenced by multiple pipeline definitions.

### 🔄 Multi-Stage Pipelines

Azure DevOps multi-stage pipelines allow you to define separate stages for building, testing, and deploying applications. This repository demonstrates how to structure pipelines with distinct stages for different environments (development, production), enabling controlled progression through deployment environments.

### 🌐 Environment Resources

Azure DevOps environments represent deployment targets like virtual machines or Kubernetes clusters. The pipelines in this repository show how to target specific environments and resources, enabling controlled deployments with appropriate approvals and checks.

### 🔌 Service Connections

Service connections in Azure DevOps provide secure access to external services like container registries, Kubernetes clusters, and cloud platforms. The examples in this repository demonstrate how to reference service connections in pipeline definitions.

### ⚡ Logic Apps Integration

Azure Logic Apps can be used to extend Azure DevOps capabilities through webhooks and service hooks. The pull request notification system in this repository shows how to integrate Azure DevOps events with Logic Apps to automate communication workflows.

## 📝 Usage

To use the examples in this repository:

1. **Clone or Fork the Repository**:
   ```bash
   git clone https://github.com/alegarciadelrio/azuredevops.git
   ```

2. **Select the Appropriate Example**:
   - For container deployments: Use the files in the `deploy-container` folder
   - For container deployments with secure environment variables: Use the files in the `deploy-container-with-library` folder
   - For Kubernetes deployments on Amazon EKS: Use the files in the `deploy-eks` folder
   - For Kubernetes deployments on on-premises clusters: Use the files in the `deploy-on-prem-kubernetes` folder
   - For Kubernetes deployments with secure environment variables: Use the files in the `deploy-with-library` folder
   - For pull request notifications: Use the files in the `notify-pull-request-reviewers` folder

3. **Customize the Configuration**:
   - Update variables, parameters, and service connection IDs to match your environment
   - Modify deployment targets and resource names as needed
   - Adjust pipeline triggers to match your branching strategy

4. **Import into Azure DevOps**:
   - Create a new pipeline in your Azure DevOps project
   - Select "Existing Azure Pipelines YAML file"
   - Point to the appropriate YAML file in your repository

5. **Set Up Required Resources**:
   - Configure environments and resources in Azure DevOps
   - Create necessary service connections
   - Set up approval policies if needed

Refer to the README.md file in each folder for detailed, solution-specific usage instructions.

## 🌿 Branch Strategy and Conventions

### 🔀 Branch Strategy

This repository follows a GitFlow-inspired branching strategy:

- **`main`**: Production-ready code that has been thoroughly tested and is ready for release
- **`develop`**: Integration branch for features that are complete but awaiting release
- **`feature/*`**: Feature branches for new functionality (branched from and merged back to `develop`)
- **`hotfix/*`**: Hotfix branches for urgent production fixes (branched from `main` and merged to both `main` and `develop`)
- **`release/*`**: Release branches for preparing new releases (branched from `develop` and merged to both `main` and `develop`)

#### Branch Workflow

1. Development work happens on `feature/*` branches
2. Completed features are merged into `develop` via pull requests
3. When ready for release, a `release/*` branch is created from `develop`
4. After testing and finalization, the release branch is merged into both `main` and `develop`
5. Critical bugs in production are fixed in `hotfix/*` branches and merged to both `main` and `develop`

### 📝 Conventional Commits

This repository follows the [Conventional Commits](https://www.conventionalcommits.org/) specification for commit messages to ensure consistency and enable automated versioning and changelog generation.

#### Commit Message Format

```
<type>: <description>

[optional body]

[optional footer(s)]
```

#### Types

- **feat**: A new feature
- **fix**: A bug fix
- **docs**: Documentation changes
- **style**: Changes that do not affect the meaning of the code (formatting, etc.)
- **refactor**: Code changes that neither fix a bug nor add a feature
- **perf**: Performance improvements
- **test**: Adding or correcting tests
- **build**: Changes to the build system or dependencies
- **ci**: Changes to CI configuration files and scripts
- **chore**: Other changes that don't modify src or test files

#### Examples

```
feat: add health check to deployment job

fix: correct service port configuration

docs: update deployment instructions
```

### 🔄 Conventional Pull Requests

#### PR Title Format

Pull request titles should follow the same convention as commit messages:

```
<type>: <description>
```

#### PR Description Template

```markdown
## Description
[Provide a detailed description of the changes]

## Related Issues
[Reference any related issues: Fixes #123, Relates to #456]

## Type of Change
- [ ] Bug fix
- [ ] New feature
- [ ] Breaking change
- [ ] Documentation update
- [ ] Configuration change
- [ ] CI/CD improvement

## Testing Performed
[Describe the testing you have performed]

## Checklist
- [ ] My code follows the project's style guidelines
- [ ] I have performed a self-review of my code
- [ ] I have commented my code, particularly in hard-to-understand areas
- [ ] I have made corresponding changes to the documentation
- [ ] My changes generate no new warnings
- [ ] I have added tests that prove my fix is effective or that my feature works
- [ ] New and existing tests pass locally with my changes
```

## � Contributing

Contributions to the Azure DevOps Toolbox are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/your-feature-name`)
3. Commit your changes using conventional commits (`git commit -m 'feat: add some feature'`)
4. Push to the branch (`git push origin feature/your-feature-name`)
5. Open a Pull Request following the conventional PR format

Please ensure your contributions include appropriate documentation and follow the existing patterns in the repository.
