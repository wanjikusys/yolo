# Custom Dockerfile for Backend API

# Step 1: Use Node 14 as the base image for building the app
FROM node:14 AS leena-builder

# Step 2: Set the working directory inside the container
WORKDIR /leena-app

# Step 3: Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Step 4: Copy the entire backend source code into the container
COPY . .

# Step 5: Use a lightweight image for the final container (multi-stage)
FROM alpine:3.16.7

# Set working directory in the final stage
WORKDIR /leena-backend

# Install Node.js runtime on Alpine
RUN apk update && apk add --no-cache nodejs npm

# Copy the built app from the builder stage
COPY --from=leena-builder /leena-app /leena-backend

# Expose the backend port (adjust if your server runs on a different one)
EXPOSE 5000

# Start the backend server
CMD ["node", "server.js"]
