# Use an appropriate Node.js base image
FROM node:16

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json to install dependencies
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy the rest of the application files
COPY . .

# Expose port 5000 for the backend service
EXPOSE 5000

# Specify the command to run the backend application
CMD ["npm", "start"]
