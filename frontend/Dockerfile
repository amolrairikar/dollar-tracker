# Use official Node.js image
FROM node:18-slim

# Set the working directory in the container
WORKDIR /usr/src/frontend/dollartracker

# Copy package.json and package-lock.json to install dependencies
COPY dollartracker/package*.json ./

# Install dependencies (use --legacy-peer-deps if you're facing dependency issues)
RUN npm install

# Copy the rest of the application code
COPY dollartracker/ ./

# Expose the port the app runs on
EXPOSE 5173

# Command to run the app
CMD ["npm", "run", "dev"]
