# Custom Dockerfile for Frontend React App

# Step 1: Use a lightweight Node base image to build the frontend
FROM node:14-slim AS leena-frontend-builder

# Step 2: Set working directory inside the container
WORKDIR /leena-frontend-app

# Step 3: Copy dependency files and install packages
COPY package*.json ./
RUN npm install

# Step 4: Copy the rest of the frontend source code
COPY . .

# Step 5: Use a minimal base image for running the app
FROM alpine:3.16.7

# Step 6: Set the working directory for the runtime container
WORKDIR /leena-app-runtime

# Step 7: Install Node and NPM (no-cache to keep image size small)
RUN apk update && apk add --no-cache nodejs npm

# Step 8: Copy built app from the previous build stage
COPY --from=leena-frontend-builder /leena-frontend-app /leena-app-runtime

# Step 9: Expose the frontend port (usually 3000 for React apps)
EXPOSE 3000

# Step 10: Start the app
CMD ["npm", "start"]
