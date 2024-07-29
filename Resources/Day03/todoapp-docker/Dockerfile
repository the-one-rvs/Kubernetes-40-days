# Build stage
FROM node:20 AS build-env

WORKDIR /app

COPY package*.json ./
RUN npm install --omit=dev

COPY . .
RUN npm run build

# Production stage
FROM gcr.io/distroless/nodejs20-debian11

WORKDIR /app

COPY --from=build-env /app .

EXPOSE 3000

ENTRYPOINT ["node", "src/index.js"]
