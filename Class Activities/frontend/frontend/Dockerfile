## BUILD PHASE
# Base image
FROM node:node:16.13.2-alpine AS builder

# Switch workdir to '/app'
WORKDIR '/app'

# Copy package.json into
# the container
COPY package.json .

# Install all the deps
RUN npm install

# Copy the rest of the
# files into the container
COPY . .

# Build the production files
RUN npm run build

## RUN PHASE
# Base image
FROM nginx

# Copy over the production files
# to the nginx webroot
COPY --from=builder /app/build /usr/share/nginx/html