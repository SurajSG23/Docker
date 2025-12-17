# `compose.yaml` 


## 1. What is `compose.yaml`?

* `compose.yaml` is a **configuration file** for **Docker Compose**
* It is used to **run multiple Docker settings using one command**
* Instead of long `docker run` commands, everything is written in **one file**

Think of it as a **recipe** to run containers

---

## 2. Why Use Docker Compose?

* Easy to manage **ports, volumes, environment variables**
* Best for:

  * Node.js + database
  * Development setups
* Start everything with **one command**

```bash
docker compose up
```

---

## 3. Simple `compose.yaml` for Node + Express App

```yaml
version: "3.9"

services:
  app:
    image: node:18
    container_name: express-app
    working_dir: /app
    volumes:
      - .:/app
    ports:
      - "3000:3000"
    command: npm start
```

---

## 4. Explanation (Line by Line)

```yaml
version: "3.9"
```

* Compose file version

```yaml
services:
```

* Defines the containers to run

```yaml
app:
```

* Name of the service (container)

```yaml
image: node:18
```

* Uses Node.js base image from Docker Hub

```yaml
container_name: express-app
```

* Custom name for the container

```yaml
working_dir: /app
```

* Sets working directory inside container

```yaml
volumes:
  - .:/app
```

* Mounts current folder to `/app`
* Code changes reflect instantly

```yaml
ports:
  - "3000:3000"
```

* Maps container port to local port

```yaml
command: npm start
```

* Command to start Express app

---

## 5. Run the App

From the project folder:

```bash
docker compose up
```

Stop containers:

```bash
docker compose down
```

---

## 6. When to Use Compose?

* Multiple containers
* Development with live reload
* Cleaner than long Docker commands

---

## 7. Simple Analogy

* `Dockerfile` → How to build
* `compose.yaml` → How to run
* `docker compose up` → Start everything

---

## 8. One-Line Exam Answer

> **`compose.yaml` is used to define and run multi-container Docker applications using a single configuration file.**

