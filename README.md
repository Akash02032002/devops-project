# DevOps Project: MERN Task Manager

This project is a simple and beautiful Task Manager application built with the MERN stack (MongoDB, Express, React, Node.js). It serves as a demonstration of modern DevOps practices, including containerization with Docker, and CI/CD pipelines using both GitHub Actions and Jenkins.

## Features

*   **Create, Read, and Delete Tasks**: A simple and intuitive interface to manage your tasks.
*   **Modern UI**: A beautiful and responsive user interface built with React and styled with Tailwind CSS.
*   **Containerized**: The entire application is containerized using Docker and can be easily run with Docker Compose.
*   **CI/CD Pipelines**: The project includes two CI/CD pipelines:
    *   **GitHub Actions**: For building, linting, and deploying the application to an AWS EC2 instance.
    *   **Jenkins**: For building and running the application in a Jenkins environment.

## Technologies and Tools

### Frontend

*   **React**: A JavaScript library for building user interfaces.
*   **Vite**: A fast build tool for modern web development.
*   **Tailwind CSS**: A utility-first CSS framework for rapid UI development.
*   **ESLint**: For code linting.
*   **Prettier**: For code formatting.

### Backend

*   **Node.js**: A JavaScript runtime for building server-side applications.
*   **Express**: A fast, unopinionated, minimalist web framework for Node.js.
*   **MongoDB**: A NoSQL database for storing task data.
*   **Mongoose**: An elegant MongoDB object modeling tool for Node.js.
*   **CORS**: For enabling Cross-Origin Resource Sharing.
*   **dotenv**: For managing environment variables.

### DevOps

*   **Docker**: For containerizing the application.
*   **Docker Compose**: For defining and running multi-container Docker applications.
*   **GitHub Actions**: For CI/CD automation.
*   **Jenkins**: For CI/CD automation.
*   **AWS EC2**: As the deployment target for the application.

## Project Structure

```
.
├── .github/workflows/ci.yml  # GitHub Actions workflow
├── client/                   # React frontend
│   ├── Dockerfile
│   ├── package.json
│   └── src/
├── server/                   # Node.js backend
│   ├── Dockerfile
│   ├── package.json
│   └── ...
├── docker-compose.yml        # Docker Compose configuration
├── Jenkinsfile               # Jenkins pipeline configuration
└── README.md
```

## Getting Started

To run this project locally, you need to have Docker and Docker Compose installed.

1.  **Clone the repository:**

    ```bash
    git clone https://github.com/your-username/devops-project.git
    cd devops-project
    ```

2.  **Create a `.env` file in the `server` directory:**

    ```
    PORT=5000
    MONGO_URI=<your_mongodb_connection_string>
    ```

3.  **Run the application using Docker Compose:**

    ```bash
    docker-compose up -d --build
    ```

The application will be available at `http://localhost:5173`.

## CI/CD Pipeline

This project includes two CI/CD pipelines:

### GitHub Actions

The GitHub Actions workflow is defined in `.github/workflows/ci.yml`. It is triggered on push or pull request to the `main` and `dev` branches. The workflow has two jobs:

*   **`build-and-lint`**: This job installs dependencies, lints the code, and builds the Docker images for both the client and server.
*   **`deploy`**: This job is triggered on push to the `main` branch. It deploys the application to an AWS EC2 instance using SSH and `docker-compose`.

### Jenkins

The Jenkins pipeline is defined in the `Jenkinsfile`. It can be used to build and run the application in a Jenkins environment. The pipeline performs the following stages:

*   **Checkout Code**: Checks out the code from the GitHub repository.
*   **Prepare .env**: Creates a `.env` file for the server.
*   **Build Docker Images**: Builds the Docker images for the frontend and backend.
*   **Run with Docker Compose**: Starts the application using `docker-compose`.