# Build Phase
FROM node:16.13.2-alpine AS builder
WORKDIR /usr/app
COPY ./package.json .
RUN npm install
COPY . .
CMD ["npm", "run", "build"]

# Run Phase
FROM node:16.13.2-alpine
WORKDIR /usr/app
COPY package.json ./
RUN npm install
COPY --from=builder /usr/app/dist .
CMD ["node", "server.js"]