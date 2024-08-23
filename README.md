
# Sample Gradle Project with Checkmarx ONE SCA Integration

This project demonstrates how to integrate Checkmarx ONE Software Composition Analysis (SCA) using the SCA Resolver in a Gradle build. The configuration allows automated security scanning of your project's dependencies, generating an SBOM (Software Bill of Materials) in CycloneDX format.

## Prerequisites

- **Java Development Kit (JDK):** Ensure you have JDK 8 or higher installed.
- **Gradle:** Ensure you have Gradle installed on your system.
- **Checkmarx ONE CLI and SCA Resolver:** The setup task will automatically download these tools if they are not present.

## Project Structure

- **`build.gradle`**: Configures the project, repositories, dependencies, and integrates Checkmarx SCA.
- **`gradle.properties`**: Contains placeholder properties for the Checkmarx API Key and Artifactory credentials.

## Setup Instructions

### 1. Clone the Repository

Clone this repository to your local machine. If testing it on a different gradle build, you will have to add these steps to your build.gradle and gradle.properties

### 2. Configure `gradle.properties`

Before running the build, update the `gradle.properties` file with your Checkmarx and Artifactory credentials:

[properties]
# Checkmarx API Key
CX_API_KEY=your-checkmarx-api-key

# Artifactory Credentials
artifactory_contextUrl=https://your-artifactory-url
artifactory_user=your-artifactory-username
artifactory_password=your-artifactory-password

### 3. Build and Run Checkmarx Scan

To build the project and run a Checkmarx SCA scan, use the following commands:

[bash]
gradle setupCheckmarxTools
gradle runCheckmarxScan

The `setupCheckmarxTools` task will automatically download and set up the necessary tools for your operating system. Note: Windows is the only validated OS tested during intial implementation.

### 4. View the SBOM

After the scan is completed, 
-The scan should be represented in the portal at https://us.ast.checkmarx.net
=The generated SBOM will be located in the project directory. 

## Tasks Overview

- **`setupCheckmarxTools`**: Downloads and sets up Checkmarx ONE CLI and SCA Resolver.
- **`runCheckmarxScan`**: Runs a Checkmarx SCA scan on the project and generates an SBOM.

## License

This project is licensed under the MIT License.