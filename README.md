# 🚀 DevOps Challenge – AI Deployment on OVH Bare Metal with CI/CD

This project showcases a real-world **DevOps deployment pipeline** integrating **Docker**, **Python**, **OVH bare metal servers**, and **Artifactory/JFrog**, aiming to optimize the deployment and execution of an AI-based API.

---

## 🧠 Project Overview

Originally, the AI system executed requests **every second** to fetch data from a database, process it, and store results in another database. This version introduces a **more robust, scalable, and automated approach** using:

- **Dockerized AI service**
- **CI/CD pipeline**
- **OVH bare metal infrastructure**
- **JFrog Artifactory** for image hosting
- **Gunicorn** to serve the Python API
- Direct **API-based invocation** of the AI logic

---

## ⚙️ Architecture Diagram

```mermaid
flowchart TD
    A[Developer pushes code] --> B[CI/CD Pipeline triggered]
    B --> C[Docker Image Build]
    C --> D[Push to JFrog Artifactory]
    D --> E[Pull Docker Image on OVH Server]
    E --> F[Run with Gunicorn]
    F --> G[Exposed AI API]
    G --> H[API Called Externally]
    H --> I[AI processes data]
    I --> J[Writes result to database]
````

---

## 🔄 CI/CD Pipeline Overview

```mermaid
graph TD
    A[Code Commit] --> B[CI Trigger]
    B --> C[Run Unit Tests]
    C --> D[Build Docker Image]
    D --> E[Push Image to Artifactory]
    E --> F[Deploy Container on OVH]
    F --> G[Run AI API (Gunicorn)]
```

---

## 🧪 Technologies Used

* **Python** – Core logic and API
* **Docker** – Containerization of the AI app
* **Gunicorn** – Python WSGI HTTP server for production use
* **GitLab CI / Jenkins** – CI/CD automation
* **JFrog Artifactory** – Docker image hosting
* **OVH Bare Metal** – Scalable infrastructure for deployment
* **PostgreSQL / MySQL** – Database (example used)

---

## 📂 Folder Structure

```bash
.
├── Dockerfile
├── ai_service/
│   ├── main.py        # AI logic and API handler
│   ├── model/         # AI models if any
│   └── utils.py       # Helper functions
├── gunicorn_config.py
├── .gitlab-ci.yml     # Or Jenkinsfile
└── README.md
```

---

## 🔧 Setup & Deployment

1. Clone the repo:

   ```bash
   git clone https://github.com/yourusername/devops-challenge.git
   ```

2. Build and test locally:

   ```bash
   docker build -t ai-service .
   docker run -p 8000:8000 ai-service
   ```

3. The CI/CD pipeline will handle:

   * Image build
   * Push to JFrog Artifactory
   * Deploy to OVH bare metal server

---

## 🧠 Example Python Function

```python
@app.route("/predict", methods=["POST"])
def predict():
    data = request.get_json()
    result = run_ai_prediction(data)
    save_to_database(result)
    return jsonify({"status": "success", "result": result})
```

---

## 📫 Contact

For more information or collaboration:

* 💼 https://github.com/dassimanuel000
