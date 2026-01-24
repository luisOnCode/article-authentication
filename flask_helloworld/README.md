# Flask Docker "Hello World" (Phase 1)

## Project Overview
This is a foundational project designed to establish a solid **Docker + Python/Flask** workflow. The goal is to look at containerization basics before moving on to an **Authentication Service** featuring JWTs, Refresh Token Rotation, and Database integration.

## Tech Stack
* **Python 3.11-slim**: A lightweight base image to keep things fast.
* **Flask**: Our micro-web framework.
* **Docker Compose**: To orchestrate our environment.

---

## How to Run the Project

Ensure you have Docker and Docker Compose installed, then follow these steps:

1.  **Clone the project** to your local machine.
2.  **Open your terminal** in the ```flask_helloworld/``` folder.
3.  **Run the following command**:
    ```bash
    docker compose up --build
    ```

### Why use Docker Compose instead of raw Docker CLI?
While `docker build` and `docker run` work, **Docker Compose** is superior for these reasons:
* **Infrastructure as Code**: All your settings (port 5010, volume mounts, build context) are saved in `docker-compose.yml` instead of lost in your terminal history.
* **Volumes (Hot Reloading)**: Your `volumes: - .:/app` setting allows you to change `app.py` on your computer and see the results instantly inside the container without restarting.
* **Scalability**: Later, when we add a Database (PostgreSQL) and a Cache (Redis) for our Auth service, we can start everything with the same single command.

---

## Testing the Endpoint

Once the container is running, the app is listening on your machine at port **5010**.

### Using a Browser or HTTP Client (Postman/Insomnia):
* **Method**: `GET`
* **URL**: `http://localhost:5010/hello`

### Expected Response:
* **Status**: `200 OK`
* **Body**:
    ```json
    {
      "message": "Hello World!"
    }
    ```

---

## Roadmap: What's Next?
Now that the "plumbing" is working, the next steps for the **Authentication Project** are:
1.  **Implementing Login Logic**: Adding `POST /login` with password hashing (Bcrypt).
2.  **JWT Generation**: Issuing Access and Refresh tokens.
3.  **Database Integration**: Adding a service to the `docker-compose.yml` to store user credentials.
4.  **Middleware**: Creating a decorator