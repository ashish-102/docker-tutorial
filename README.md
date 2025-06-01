# 🚀 FastAPI Dockerized App

This project demonstrates how to containerize a simple [FastAPI](https://fastapi.tiangolo.com/) application using **Docker** and manage it with **Docker Compose**.

---

## 📁 Project Structure

```
.
├── main.py               # FastAPI application
├── requirements.txt      # Python dependencies
├── Dockerfile            # Docker image definition
├── docker-compose.yml    # Multi-container configuration (optional DB, etc.)
└── README.md             # Documentation
```

---

## 🐳 Docker Instructions

### 1. Build the Docker Image

```bash
docker build -t fastapi-app .
```

### 2. Run the Container

```bash
docker run -d -p 8000:8000 fastapi-app
```

Visit your app at: [http://localhost:8000](http://localhost:8000)

---

## ⚙️ Docker Compose (Optional)

If you’re using `docker-compose.yml`:

```bash
docker compose up --build
```

This makes it easy to scale and add services like a database.

---

## 📦 `requirements.txt`

```txt
fastapi
uvicorn[standard]
```

---

## 🐍 `main.py`

```python
from fastapi import FastAPI

app = FastAPI()

@app.get("/")
def read_root():
    return {"message": "Hello from Dockerized FastAPI!"}
```

---

## 🐋 `Dockerfile`

```dockerfile
FROM python:3.11-slim

WORKDIR /app

COPY requirements.txt .
RUN pip install --no-cache-dir -r requirements.txt

COPY . .

CMD ["uvicorn", "main:app", "--host", "0.0.0.0", "--port", "8000"]
```

---

## 🧾 `docker-compose.yml` (Optional)

```yaml
version: "3.9"

services:
  web:
    build: .
    ports:
      - "8000:8000"
    volumes:
      - .:/app
```

---

## 🧪 Test the API

After running the container, you can test the API at:

- [http://localhost:8000](http://localhost:8000) – root endpoint
- [http://localhost:8000/docs](http://localhost:8000/docs) – interactive Swagger UI
- [http://localhost:8000/redoc](http://localhost:8000/redoc) – alternative documentation UI

---

## 💡 Notes

- Make sure **Docker** and **Docker Compose** are installed and running.
- You can use a `.dockerignore` file to exclude unnecessary files from the image.

---

## 📜 License

This project is licensed under the **MIT License**.

---

## 🙌 Acknowledgements

- [FastAPI](https://fastapi.tiangolo.com/)
- [Docker](https://www.docker.com/)
- [Uvicorn](https://www.uvicorn.org/)

---

## ✅ Next Steps

1. Save this as `README.md` in your project directory.
2. Initialize Git and push to GitHub:

```bash
git init
git add .
git commit -m "Initial commit: FastAPI Docker setup"
git branch -M main
git remote add origin https://github.com/YOUR_USERNAME/YOUR_REPO_NAME.git
git push -u origin main
```

---

Let me know if you want:
- This turned into a **GitHub template**
- A **GitHub Pages** site
- A **CI/CD pipeline** to build and deploy automatically
