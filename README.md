# Car Service REST API sample

## Overview

The Car Data Service API is a Spring Boot application designed to expose comprehensive data about cars and related entities through a single endpoint. It uses a custom JSON builder to structure the data.

## Features

- **Expose Car Data**: Retrieve detailed information about cars, including related entities like clients, maintainers, and tools.
- **Custom JSON Structure**: Generate JSON responses with a custom JSON builder, maintaining the order of attributes.

## Technology Stack

- **Framework**: [Spring Boot](https://docs.spring.io/spring-boot/index.html) v3.2 (Spring v6)
- **Languages**: Java v17
- **Build Tool**: [Maven](https://maven.apache.org/) v3.9
- **Code Formatting**: [Checkstyle](https://checkstyle.sourceforge.io/) and [Spotless](https://github.com/diffplug/spotless)
- **Version Control**: Git

## Getting Started

### Installation

1. **Clone the repository**

```bash
git clone <GITHUB_REPOSITORY_URL>
cd car-service-rest-api
```

2. **Build**
```bash 
./mvnw clean install
```

3. **Run**
```bash
mvn spring-boot:run -Dspring-boot.run.profiles=demo
```
_Note: The app doesn't have endpoints to do CRUD operations yet. The `demo` profile refers to `../configs/LoadDatabase`, which helps to fill database with fictive data at runtime._

### Usage
**Endpoint**: `/api/cars`

**Method**: `GET`

**Response :**
```json
[
    {
        "car": {
            "id": 1,
            "model": "Model S",
            "make": "Tesla",
            "clientName": "Client One",
            "maintainerName": "Technician One",
            "tools": [
                {
                    "id": 1,
                    "name": "Wrench"
                },
                {
                    "id": 2,
                    "name": "Screwdriver"
                }
            ]
        }
    }
]
```


## Code Quality and Maintenance

To maintain a consistent code style and ensure high code quality, we have integrated several tools and practices into our project:

### Code Formatting

1. **Spotless**: Ensures that the code adheres to defined formatting rules. Spotless helps keep the codebase clean and uniformly formatted.

2. **Checkstyle**: Assists in writing code that conforms to Java standard coding practices. It enforces a set of coding standards and helps maintain good quality.

_Note: If you're new to these tools, there’s no need to worry. They are already configured and will work seamlessly in the background._

### Git Hooks

To ensure code quality and proper branching, we use Git hooks managed by the [**Git Build Hook Maven Plugin**](https://github.com/rudikershaw/git-build-hook). This plugin facilitates the management of hook scripts (check `./configs/git-hooks/pre-commit` file). 

This technique helps prevent poorly formatted or non-compliant code from being committed or pushed.

Currently, there are 2 sorts of hooks :
1. **Pre-commit**: Automatically format code and run checks before allowing a commit. If issues are found, the commit will be aborted until the issues are resolved.

2. **Pre-push**: (check the [next section](#branch-naming-convention))

### Branch Naming Convention
To maintain clarity and consistency, we follow a structured branch naming convention. A pre-push Git hook is in place to enforce this convention (check `./configs/git-hooks/pre-push` file).
