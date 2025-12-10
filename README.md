Multi-Container Voting Application using Docker & Docker Compose


<p align="center"> <!-- Overall Project Status --> <img src="https://img.shields.io/badge/Project-Active-success?style=for-the-badge" /> <!-- Tech Badges --> <img src="https://img.shields.io/badge/Docker-2496ED?style=for-the-badge&logo=docker&logoColor=white" /> <img src="https://img.shields.io/badge/Docker%20Compose-384d54?style=for-the-badge&logo=docker&logoColor=white" /> <img src="https://img.shields.io/badge/Python-3776AB?style=for-the-badge&logo=python&logoColor=white" /> <img src="https://img.shields.io/badge/Redis-DC382D?style=for-the-badge&logo=redis&logoColor=white" /> <img src="https://img.shields.io/badge/PostgreSQL-316192?style=for-the-badge&logo=postgresql&logoColor=white" /> <!-- Repo Info Badges --> <img src="https://img.shields.io/github/stars/Nanthakumar-N2/multi-container-voting-application-using-Docker-and-Docker-Compose?style=for-the-badge" /> <img src="https://img.shields.io/github/forks/Nanthakumar-N2/multi-container-voting-application-using-Docker-and-Docker-Compose?style=for-the-badge" /> <img src="https://img.shields.io/github/last-commit/Nanthakumar-N2/multi-container-voting-application-using-Docker-and-Docker-Compose?style=for-the-badge" /> </p>
A complete, containerized voting application built using Python (Flask), Redis, .NET Worker, and PostgreSQL—all orchestrated using Docker Compose.
This project demonstrates a real-world microservices workflow with separate frontend, backend, worker, and database services.

🚀 Project Overview

This application simulates a simple voting system:

Users vote between two options (e.g., Cats vs Dogs) from a Flask-based web frontend.

Votes are stored in Redis (in-memory).

A background Worker Service reads votes from Redis and stores them permanently in PostgreSQL.

The Result App displays live voting results from PostgreSQL.

The project is structured to demonstrate clean microservice separation and the power of container orchestration.

🧱 Architecture
+--------------------+        +--------------------+
|   Voting App       |        |   Result App       |
| (Python + Flask)   |        |  (Node.js/.NET)    |
+---------+----------+        +----------+---------+
          |                              |
          v                              v
+---------+----------+        +----------+---------+
|       Redis        | -----> |      Worker        |
|  Temporary Storage |        | (Python/.NET)      |
+---------+----------+        +----------+---------+
          |                              |
          +------------------------------+
                          |
                          v
                 +--------+----------+
                 |     PostgreSQL    |
                 |  Persistent DB    |
                 +-------------------+

🗂️ Repository Structure
.
├── vote/               # Frontend voting application (Python Flask)
├── result/             # Result application (.NET, Node.js or similar)
├── worker/             # Background worker that syncs Redis -> Postgres
├── docker-compose.yml  # Main orchestration file
├── README.md           # Documentation
└── images/             # Optional: screenshots / diagrams

🐳 Technologies Used
Component	Technology
Frontend	Python, Flask
Cache / Queue	Redis
Worker	Python / .NET
Database	PostgreSQL
Containerization	Docker, Docker Compose
Orchestration	Multi-container architecture
▶️ How to Run the Application
1. Clone the repository
git clone https://github.com/Nanthakumar-N2/multi-container-voting-application-using-Docker-and-Docker-Compose.git
cd multi-container-voting-application-using-Docker-and-Docker-Compose

2. Start all services
docker compose up --build

3. Access the apps
Service	URL
Voting App	http://localhost:5000

Result App	http://localhost:5001

Redis	localhost:6379
PostgreSQL	localhost:5432
🛑 Stopping the Services
docker compose down


If you want to remove volumes:

docker compose down -v

📦 Environment Variables (Optional)

Create a .env file if needed:

POSTGRES_USER=postgres
POSTGRES_PASSWORD=postgres
POSTGRES_DB=votes

📌 Key Features

Complete microservices example using Docker

Stateless frontend backed by Redis

Worker pattern using queue → database sync

Persistent storage using PostgreSQL volumes

Production-style folder structure

Fully isolated environment using Docker Compose

🧪 Testing Your Setup

Run:

docker ps


You should see all containers running:

vote

worker

result

redis

postgres

📸 Optional: Add Screenshots

Create a folder:

images/


Add images and reference them:

![Voting Page](images/vote.png)

🤝 Contributing

Pull requests are welcome!
Feel free to open issues for bugs, suggestions, or improvements.

📜 License

This project is open-source under the MIT License.
