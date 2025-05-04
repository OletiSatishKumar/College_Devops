# College DevOps

## Project Overview

This project implements a college management system using a microservices architecture. The system includes a backend built with Spring Boot, a frontend built with React, and MySQL as the database. The project leverages Docker for containerization and Kubernetes for orchestration. Jenkins is used for CI/CD, enabling seamless integration and delivery.

## Project Structure

* **backend/**: Java Spring Boot application

  * Contains business logic and API endpoints
  * Dockerized with a `Dockerfile`
* **frontend/**: React application

  * Provides the UI for the system
  * Dockerized with a `Dockerfile`
* **database/**: SQL initialization scripts
* **k8s/**: Kubernetes manifests for deployment

  * Manifests for both `dev` and `prod` environments
  * Ingress configurations
* **jenkins/**: Optional Jenkins pipeline configurations
* `.gitignore`: Git ignore rules
* `README.md`: Project documentation

## Technologies Used

* **Backend**: Java, Spring Boot, MySQL
* **Frontend**: React
* **Docker**: Containerization for both backend and frontend
* **Kubernetes**: Orchestration for deployment
* **Jenkins**: CI/CD pipeline (optional)

## Getting Started

### Prerequisites

* Docker
* Kubernetes (Optional for local testing)
* Jenkins (Optional)

### Backend Setup

1. **Clone the repository**:

   ```bash
   git clone https://github.com/OletiSatishKumar/College_Devops.git
   cd College_Devops
   ```

2. **Build the Docker image for backend**:

   ```bash
   cd backend
   docker build -t server-springboot .
   ```

3. **Run the backend Docker container**:

   ```bash
   docker run -d --name backend --network app-network -e SPRING_DATASOURCE_URL=jdbc:mysql://host.docker.internal:3306/mydb -e SPRING_DATASOURCE_USERNAME=root -e SPRING_DATASOURCE_PASSWORD=Satish@@1303 -p 8000:9192 server-springboot
   ```

### Frontend Setup

1. **Build the Docker image for frontend**:

   ```bash
   cd frontend
   docker build -t client-react .
   ```

2. **Run the frontend Docker container**:

   ```bash
   docker run -d --name frontend -p 3000:3000 client-react
   ```

### MySQL Setup

1. **Run MySQL container** (using Docker):

   ```bash
   docker run -d --name mysql-container -e MYSQL_ROOT_PASSWORD=Satish@@1303 -e MYSQL_DATABASE=mydb -p 3306:3306 mysql:8
   ```

2. **Run the SQL initialization script** (located in the `database/` folder):

   ```bash
   docker exec -i mysql-container mysql -uroot -pSatish@@1303 mydb < database/init.sql
   ```

## Kubernetes Setup

1. **Deploy the services in Kubernetes**:

   * Modify the YAML files under `k8s/dev/` or `k8s/prod/` as needed.
   * Apply the deployments:

     ```bash
     kubectl apply -f k8s/dev/
     ```

## Jenkins Setup (Optional)

1. **Set up Jenkins pipeline** using the `Jenkinsfile` located in the `jenkins/` folder.

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.

---

You can adjust this based on additional specifics or changes in your project. Let me know if you'd like to add anything else!
