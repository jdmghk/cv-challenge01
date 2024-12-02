# Frontend Dockerfile
FROM node:latest

# Set working sirectory
WORKDIR /app

# Copy the application files
COPY . .

# Install dependencies
RUN npm install

# Expose the port 
EXPOSE 5173

# Serve the built application
CMD ["npm", "run", "dev", "--", "--host", "0.0.0.0"]