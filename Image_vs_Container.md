# Docker Image vs Docker Container

---

### 1. Docker Image

* A **static template** used to create containers
* **Immutable** (cannot be modified once created)
* **Read-only**
* Contains:

  * Application code
  * Runtime (Python, Java, etc.)
  * Libraries and dependencies
  * Configuration files
* Does **not consume CPU/RAM**
* Stored in registries (Docker Hub, private registry)

**Example:**
👉 Image = *Setup of a Python application*

---

### 2. Docker Container

* A **running instance of a Docker image**
* **Mutable** (can be modified while running)
* **Read + write**
* Consumes **CPU, RAM, and storage**
* Has its own:

  * Filesystem
  * Network
  * Process space
* Temporary in nature (can be started, stopped, deleted)

**Example:**
👉 Container = *Python application actually running*

---

### 3. Immutability vs Mutability

* **Docker Image → Immutable**

  * Any change requires creating a new image
* **Docker Container → Mutable**

  * Changes exist only during container lifetime

---

### 4. Relationship Between Image and Container

* Image is used to **create** a container
* One image can create **multiple containers**
* Deleting a container does **not** delete the image

---

### 5. Simple Analogy

* **Image** → Recipe book (immutable)
* **Container** → Cooked food (mutable)

---

### 6. Key Differences (Exam-Ready Table)

| Feature    | Docker Image | Docker Container |
| ---------- | ------------ | ---------------- |
| Nature     | Static       | Dynamic          |
| State      | Not running  | Running          |
| Mutability | Immutable    | Mutable          |
| Access     | Read-only    | Read & Write     |
| Purpose    | Blueprint    | Execution        |
| Resources  | No CPU/RAM   | Uses CPU/RAM     |

---

### 7. One-Line Conclusion

> **Docker Image is an immutable blueprint, while Docker Container is a mutable running application.**



![Image](https://uncookednews.com/wp-content/uploads/2021/10/Docker-Images-and-Containers-Explained-2022-uncookednews.png?utm_source=chatgpt.com)
    