# Use official Node.js 14 as base image
FROM node:16.20.2-buster-slim

# Set working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci 

# Copy the rest of the server code
COPY . .

ENV NODE_ENV=production
# Expose port 3000 for the server
EXPOSE 3000

# Start the server
CMD [ "npm", "run", "start" ]
