# Production build with serve package
FROM node:18-alpine

WORKDIR /app

# Copy package files
COPY package*.json ./

# Install dependencies
RUN npm ci

# Copy source code
COPY . .

# Build the application (bakes .env into bundle)
RUN npm run build

# Install serve globally to serve static files
RUN npm install -g serve

# Expose port
EXPOSE 3000

# Serve the built files (production)
CMD ["serve", "-s", "dist", "-l", "3000"]