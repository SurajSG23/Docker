# Docker Volumes

## 1. What is a Docker Volume?

* A **Docker volume** is a way to **store data outside the container**
* Data in volumes **persists even if the container is deleted**
* Managed completely by **Docker**
* Used mainly for:

  * Databases
  * Logs
  * Application data

---

## 2. Why Volumes are Needed

* Containers are **temporary** by default
* When a container is removed:

  * All internal data is lost
* Volumes solve this problem by **separating data from containers**

---

## 3. Types of Volumes / Mounts

### a) Named Volumes (Recommended)

* Created and managed by Docker
* Stored in Docker’s internal location
* Safe and portable

```bash
docker volume create mydata
docker run -v mydata:/app/data node:18
```

---

### b) Bind Mounts

* Maps a **local folder** to container folder
* Mostly used in **development**

```bash
docker run -v ${PWD}:/app node:18
```

---

### c) Anonymous Volumes

* Created automatically
* No custom name
* Hard to manage

---

## 4. Volumes vs Container Storage

* Container storage is **ephemeral (temporary)**
* Volume storage is **persistent**

**Key idea:**

> Delete container ❌ data lost \
> Delete container ✅ volume data safe

---

## 5. Volumes in Node.js / Express (Example)

### Using Bind Mount (Development)

```bash
docker run -p 3000:3000 -v ${PWD}:/app node:18
```

* Code changes reflect **instantly**
* Used with nodemon

---

### Using Named Volume (Production-like)

```bash
docker run -p 3000:3000 -v appdata:/app/data node:18
```

---

## 6. Volumes in Dockerfile? ❌

* Volumes are **not for Dockerfile**
* Volumes are defined at:

  * `docker run`
  * `docker-compose.yml`

---

## 7. Important Docker Volume Commands

```bash
docker volume ls        # list volumes
docker volume inspect mydata
docker volume rm mydata
```

---

## 8. Volume vs Bind Mount (Exam Table)

| Feature           | Volume          | Bind Mount   |
| ----------------- | --------------- | ------------ |
| Managed by Docker | Yes             | No           |
| Data location     | Docker internal | Local system |
| Best for          | Production      | Development  |
| Portable          | Yes             | No           |

---

## 9. Simple Analogy

* **Container** → Rented room
* **Volume** → Locker outside the room
* Room removed → locker still exists

---

## 10. One-Line Exam Answer

> **Docker volumes are used to persist and share data between containers and the host system, independent of the container lifecycle.**

