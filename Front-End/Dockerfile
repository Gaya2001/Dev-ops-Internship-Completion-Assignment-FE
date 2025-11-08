# Production build with serve package
FROM node:18-alpine

WORKDIR /app

# Build arguments for environment variables
ARG VITE_API_URL=https://restcountries.com/v3.1
ARG VITE_SERVER_URL=https://api.kavinducloudops.tech/api

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy source code
COPY . .

# Build the application with environment variables
RUN VITE_API_URL=${VITE_API_URL} VITE_SERVER_URL=${VITE_SERVER_URL} npm run build

# Install serve globally to serve static files
RUN npm install -g serve

# Expose port
EXPOSE 3000

# Serve the built files (production)
CMD ["serve", "-s", "dist", "-l", "3000"]
