# mulesoft-demos

This service is designed to provide a **hands-on demonstration of using MUnit within a Jenkins continuous integration environment**.  
Its purpose is to showcase how tu use MUnit tests can be integrated into an automated pipeline to validate MuleSoft flows, generate coverage reports, and ensure code quality before deployment.

## Scope

- Configuring a MuleSoft project with MUnit dependencies  
- Creating and executing unit tests with MUnit  
- Integrating test execution into a Jenkins pipeline  
- Generating and publishing execution and coverage reports  
- Demonstrating best practices for continuous validation with MUnit and Jenkins

## Requirements (Without Jenkins)

If you want to run the project without using Jenkins, make sure you have the following installed and configured locally:

- **Java JDK 8 or 11**  
  - Required for running MuleSoft projects and MUnit tests.  
  - [Download JDK](https://adoptium.net/)  

- **Maven 3.9.11**  
  - Must be installed locally and available in your `PATH`.  
  - Verify installation with:  
    ```bash
    mvn -version
    ```

- **MuleSoft Runtime (Standalone or Mule Maven Plugin)**  
  - Required to build and test MuleSoft applications.  

- **IDE or Text Editor** (optional but recommended)  
  - Example: Anypoint Studio, IntelliJ IDEA, or VS Code.

With these requirements, you can run the project locally using Maven commands such as:  

```bash
mvn clean test

## Requirements

Before running the project with **jenkins**, make sure you have the following installed:

- **Docker** (latest stable version)  
  - [Download and Install Docker](https://docs.docker.com/get-docker/)

- **Jenkins Docker Container**  
  - The official Jenkins **jdk17** image must be **downloaded and running inside a container**.  
  - The container must be **configured** with:  
    - Persistent storage (`jenkins_home` volume)  
    - Proper port mappings (`8080:8080`, `50000:50000`)  
    - Administrative setup completed (initial password, plugin installation, and first admin user created).
    - **Plugins**:  
      - *HTML Publisher* (required for publishing test reports).  
    - **Global Tools Configuration**:  
      - *Maven 3.9.11* installed and configured with the name: `maven-3.9.11`.
    - **Environment Variables**:  
      - A secret environment variable named **`mulesoft-key`** must be configured in Jenkins credentials or pipeline environment settings.

