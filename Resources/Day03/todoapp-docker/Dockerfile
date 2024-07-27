# Stage 1: Build the application
FROM node:18 AS builder
WORKDIR /app
COPY package*.json ./
RUN npm install
COPY . .
RUN npm run build

# Stage 2: Create the Distroless image
FROM gcr.io/distroless/nodejs18
WORKDIR /app
COPY --from=builder /app/build .
# CMD ["index.js"]
