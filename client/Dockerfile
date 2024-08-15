# Use official Node.js 14 as base image
FROM node:16.20.2-buster-slim AS build

# Set working directory
WORKDIR /usr/src/app

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm ci 

# Copy the rest of the client code
COPY . .

RUN mv .env.example .env

# Build the client for production
RUN npm run build


FROM nginx:1.27.0-alpine-perl AS production 

COPY --from=build  /usr/src/app/dist /usr/share/nginx/html

EXPOSE 80 

CMD ["nginx", "-g", "daemon off;"]
