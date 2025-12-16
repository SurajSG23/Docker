# How to Pull & Run Node.js Image in Docker

## 1. Prerequisite

* **Docker Desktop must be installed and running**
* Internet connection (to pull image from Docker Hub)

---

## 2. Pull Node.js Image from Docker Hub

* This downloads the Node.js **base image** to your system.

```bash
docker pull node:18
```

* `node` → image name
* `18` → Node.js version tag
* Image is pulled from **Docker Hub** and stored locally.

After this, the Node.js image is available on your machine.

---

## 3. Verify the Image

```bash
docker images
```

* Lists all Docker images available locally
* You should see `node` in the list.

---

## 4. Run Node.js Container (Interactive Mode)

```bash
docker run -it node:18
```

* `docker run` → creates and starts a container
* `-it` → interactive terminal
* `node:18` → image used
* Opens **Node.js REPL** inside the container.

Check Node version:

```bash
node -v
```

---

## 5. Run a Simple Node.js Command

```bash
docker run node:18 node -e "console.log('Hello from Node in Docker')"
```

* Runs Node.js directly inside a container
* Container stops after execution.

---

## 6. Run Node.js App Using Docker (Basic)

Assume you have `app.js`:

```js
console.log("Hello from Node App");
```

Run using volume mapping:

```bash
docker run -it -v %cd%:/app -w /app node:18 node app.js
```

* `-v %cd%:/app` → maps current folder to container
* `-w /app` → sets working directory
* `node app.js` → runs the app

---

## 7. Run Node App with Port Mapping (Web App)

For Express app running on port `3000`:

```bash
docker run -it -p 3000:3000 node:18
```

* `-p 3000:3000` → maps container port to local port
* App accessible at:
   `http://localhost:3000`

---

## 8. Important Notes

* **Node image is immutable**
* Container is **temporary** unless saved
* One Node image can run **multiple containers**
* Stopped container does not delete the image

---

## 9. One-Line Summary

> **Pull the Node image from Docker Hub, then run it using Docker Desktop to execute Node.js applications inside a container.**

