## 1. Project Structure (Typical)

```
my-vite-app/
├─ src/
├─ public/
├─ index.html
├─ vite.config.js
├─ package.json
├─ Dockerfile
├─ .dockerignore
```

---

## 2. `package.json` (important scripts)

```json
{
  "name": "vite-react-app",
  "private": true,
  "type": "module",
  "scripts": {
    "dev": "vite",
    "build": "vite build",
    "preview": "vite preview"
  },
  "dependencies": {
    "react": "^18.2.0",
    "react-dom": "^18.2.0"
  }
}
```

---

## 3. `.dockerignore`

```dockerignore
node_modules
dist
.git
.env
```

---

## 4. **Dockerfile (Recommended – Multi-Stage Build)**

```dockerfile
# ---------- Build stage ----------
FROM node:18 AS builder

# Set working directory
WORKDIR /app

# Copy dependency files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy source code
COPY . .

# Build Vite project (creates dist/)
RUN npm run build

# ---------- Production stage ----------
FROM nginx:alpine

# Copy built files to nginx
COPY --from=builder /app/dist /usr/share/nginx/html

# Expose port 80
EXPOSE 80

# Start nginx
CMD ["nginx", "-g", "daemon off;"]
```

---

## 5. Build Docker Image

Run inside project folder:

```bash
docker build -t vite-react-app .
```

---

## 6. Run the Container

```bash
docker run -p 3000:80 vite-react-app
```

Open browser:
**[http://localhost:3000](http://localhost:3000)**

---

## 7. How This Works (Simple Flow)

1. Node image builds React + Vite app
2. `npm run build` creates `dist/`
3. Nginx serves static files
4. Lightweight and fast image

---

## 8. Why Multi-Stage Build is Best

* Smaller image size
* No Node.js in production
* Faster startup
* More secure

---

## 9. One-Line Exam Answer

> **A React Vite Docker image is created by building the app using Node.js and serving the generated static files using Nginx with a multi-stage Dockerfile.**
