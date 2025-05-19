FROM node:14-slim AS build

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

# Copy the rest of the application code to the container
COPY . .

FROM alpine:3.16.7

WORKDIR /app

RUN apk update && apk add npm

COPY --from=build /usr/src/app /app

# Expose the port the app runs on
EXPOSE 3000

RUN npm install -g serve

EXPOSE 3000

# Command to run the application
CMD ["serve", "-s", "build", "-l", "3000"]
