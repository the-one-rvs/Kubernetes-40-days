# Build stage
FROM node:18 AS builder

WORKDIR /app

COPY package*.json ./
RUN npm install --omit=dev

COPY . .
RUN npm run build

# Production stage
FROM gcr.io/distroless/nodejs20-debian11

WORKDIR /app
COPY --from=builder /app/build .
ENTRYPOINT ["node","index.js"]
