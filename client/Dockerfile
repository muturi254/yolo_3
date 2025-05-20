FROM node:14-slim AS build

# Set the working directory in the container
WORKDIR /app

# Copy the package.json and package-lock.json files to the container
COPY package*.json ./

# Install application dependencies
RUN npm install

COPY . .

RUN npm run build

FROM node:16-alpine3.16

WORKDIR /app

COPY --from=build /app/build ./build

RUN npm install -g serve

EXPOSE 3000

# Command to run the application
CMD ["serve", "-s", "build", "-l", "3000"]


