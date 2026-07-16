# ==========================
# Build Stage
# ==========================
FROM node:20-alpine3.18 AS build

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy application source
COPY . .

# Build React application
RUN npm run build

# ==========================
# Production Stage
# ==========================
FROM nginx:stable-alpine

# Copy React build output
COPY --from=build /app/build /usr/share/nginx/html

# Expose Nginx port
EXPOSE 80

# Start Nginx
CMD ["nginx", "-g", "daemon off;"]