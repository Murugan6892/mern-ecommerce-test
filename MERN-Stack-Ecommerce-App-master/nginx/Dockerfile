# Dockerfile for frontend
FROM node:18-alpine AS build

WORKDIR /app

# Only copy package files first
COPY package*.json ./

# Install dependencies inside the container
RUN npm install

# Copy all source files
COPY . .

# Build the React app
RUN CI=false npm run build

# Use nginx to serve built app
FROM nginx:latest
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
