# FROM node:14-alpine

# LABEL maintainer="muturi254"
# WORKDIR /app

# COPY package*.json ./

# RUN npm install

# COPY . .

# EXPOSE 5001

# ENTRYPOINT [ "npm", "start" ]
FROM node:16-alpine AS build

WORKDIR /app

# Install dependencies
COPY package*.json ./
RUN npm install

# Copy app source code
COPY . .

# Stage 2: Run from minimal image
FROM node:16-alpine

WORKDIR /app

# Copy only the build artifacts (your full backend code + node_modules)
COPY --from=build /app .

# Expose your backend port
EXPOSE 5000


# Start the backend
CMD ["node", "server.js"]