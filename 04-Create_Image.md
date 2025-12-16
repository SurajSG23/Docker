# Create Docker Image for **Express + Node.js App**

## 1. Create Express App (`app.js`)

```js
import express from "express";

const app = express();

app.get("/", (req, res) => {
  res.send("Hello from Express + Node.js Docker App");
});

app.listen(3000, () => {
  console.log("Server running on port 3000");
});
```

---

## 2. Create `package.json` (Important for `import`)

```json
{
  "name": "express-docker-app",
  "version": "1.0.0",
  "type": "module",
  "main": "app.js",
  "scripts": {
    "start": "node app.js"
  },
  "dependencies": {
    "express": "^4.18.2"
  }
}
```

`"type": "module"` is **mandatory** to use
`import express from "express"`

---

## 3. Create Dockerfile

Create a file named **`Dockerfile`**:

```dockerfile
# Step 1: Use Node.js version 18 as the base image
# This provides Node.js and npm inside the container
FROM node:18

# Step 2: Set /app as the working directory inside the container
# All next commands will run from this directory
WORKDIR /app

# Step 3: Copy only package.json and package-lock.json
# This helps Docker cache npm install if dependencies don't change
COPY package*.json ./

# Step 4: Install all project dependencies listed in package.json
# node_modules will be created inside the container
RUN npm install

# Step 5: Copy the remaining application source code
# This includes app.js and other files
COPY . .

# Step 6: Inform Docker that the app runs on port 3000
# This does not publish the port automatically
EXPOSE 3000

# Step 7: Command to run when the container starts
# Runs the "start" script defined in package.json
CMD ["npm", "start"]

```

---

## 4. Build Docker Image

Run in the project folder:

```bash
docker build -t express-docker-app .
```

---

## 5. Run the Container

```bash
docker run -p 3000:3000 express-docker-app
```

---

## 6. Test the App

Open browser and visit:
**[http://localhost:3000](http://localhost:3000)**

You should see:

```
Hello from Express + Node.js Docker App
```

---

## 7. Flow (Very Important)

1. `node:18` base image pulled from Docker Hub
2. Express installed inside image
3. Image built using Dockerfile
4. Container runs Express app
5. Port 3000 exposed to host machine

---

## 8. Common Mistakes to Avoid

* ❌ Forgetting `"type": "module"`
* ❌ Not exposing correct port
* ❌ Port mismatch in `docker run -p`

---

## 9. One-Line Exam Answer

> **An Express.js application can be containerized by using a Node.js base image, installing Express, copying source files, and running the app using Dockerfile instructions.**

