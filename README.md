### README for FastAPI Dockerized App Template

---

## **FastAPI Dockerized App**

This project provides a simple FastAPI app template, Dockerized and ready for development or deployment.

---

### **Project Structure**
```plaintext
fastapi-docker/
├── app/
│   ├── main.py             # FastAPI app entry point
│   ├── __init__.py         # Makes the `app` directory a module
├── Dockerfile              # Dockerfile to build the application image
├── docker-compose.yml      # Docker Compose file for managing services
├── requirements.txt        # Python dependencies
├── .dockerignore           # Files to ignore in the Docker build context
```

---

### **Prerequisites**
- **Docker**: [Download and install Docker](https://www.docker.com/)
- **Docker Compose**: Comes bundled with Docker Desktop or can be installed separately.

---

### **Setup and Usage**

#### **1. Clone the Repository**
```bash
git clone https://github.com/Mo-Khalaf/fastapi-docker-template.git
cd fastapi-docker-template
```

#### **2. Build and Start the Application**

Using Docker Compose:
```bash
docker-compose up --build
```

The application will be available at:  
**http://localhost:8000**

#### **3. Access FastAPI Interactive Docs**
- Swagger UI: **http://localhost:8000/docs**
- ReDoc: **http://localhost:8000/redoc**

#### **4. Stop the Application**
```bash
docker-compose down
```

---

### **Important Commands**

#### **Docker Compose Commands**
- **Build and start containers**:
  ```bash
  docker-compose up --build
  ```
- **Start existing containers**:
  ```bash
  docker-compose up
  ```
- **Stop and remove containers**:
  ```bash
  docker-compose down
  ```
- **View logs**:
  ```bash
  docker-compose logs -f
  ```

#### **Standalone Docker Commands**
- **Build the Docker image**:
  ```bash
  docker build -t fastapi-docker-app .
  ```
- **Run the container**:
  ```bash
  docker run -d -p 8000:8000 fastapi-docker-app
  ```

#### **FastAPI Development Commands**
- Run the app locally without Docker:
  ```bash
  uvicorn app.main:app --reload --host 0.0.0.0 --port 8000
  ```
  (Requires Python and dependencies installed.)

---

### **Project Configuration**

#### **Dockerfile**
- Defines the build instructions for the application.
- Default command:
  ```dockerfile
  CMD ["uvicorn", "app.main:app", "--host", "0.0.0.0", "--port", "8000"]
  ```

#### **docker-compose.yml**
- Manages services and their configurations. Key settings:
  - **Ports**: Exposes `8000` (default for Uvicorn).
  - **Volumes**: Mounts `./app:/app` for live reloading during development.

---

### **Development vs. Production**
| **Environment**       | **Command**                                                                                   | **Notes**                                                                                 |
|-----------------------|-----------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------|
| **Development**       | `docker-compose up` (with `--build` for changes)                                             | Auto-reload enabled via Uvicorn when editing code.                                       |
| **Production**        | Build with `docker-compose` or standalone `docker build`, then deploy without `--reload`.    | Remove `--reload` in production for better performance and stability.                    |

---

### **Contributing**
Feel free to fork the repository and contribute to improve this template. Pull requests are welcome.

---

### **License**
This project is licensed under the MIT License.