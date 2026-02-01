# # 1. Use official Node.js LTS image
# FROM node:20-alpine

# # 2. Set working directory inside container
# WORKDIR /app

# # 3. Copy package.json and package-lock.json / yarn.lock
# COPY package*.json ./

# # 4. Install dependencies
# RUN npm install

# # 5. Copy the rest of the project
# COPY . .

# # 6. Expose Vite dev server port
# EXPOSE 5173

# # 7. Run Vite dev server
# CMD ["npm", "run", "dev", "--", "--host"]
#######################################
# Stage 1: Build
# ==========================
# Stage 1: Build / Dev
# ==========================
# ==========================
# Stage 1: Builder / Dev
# ==========================
# Stage 1: Builder
# ==========================
# Stage 1: Builder
# ==========================
FROM node:20-alpine AS builder
WORKDIR /app

COPY package*.json ./
RUN npm install
COPY . .

# Build Vite production files into /app/dist
RUN npm run build

# ==========================
# Stage 2: Production (Nginx)
# ==========================
FROM nginx:alpine AS production
WORKDIR /usr/share/nginx/html
RUN rm -rf ./*

# Copy built files from builder
COPY --from=builder /app/dist ./

# Expose HTTP port
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]

# Build & run
# Build production image:
# bash
# Copy code
# docker build -t vite-app-prod-target production
# Run production container:
# bash
# Copy code
# docker run -p 80:80 vite-app-prod
# Open in browser:
# arduino
# Copy code
# http://localhost