# syntax=docker/dockerfile:1
# Build stage
FROM node:17.8-alpine AS builder
ENV NODE_ENV production
WORKDIR /app
COPY ["package.json", "package-lock.json*", "./"]
RUN npm install --production
COPY . .
RUN npm run build

# Using nginx for production image
FROM nginx:1.21-alpine AS production
ENV NODE_ENV production
COPY --from=builder /app/build /usr/share/nginx/html
COPY nginx.conf /etc/nginx/conf.d/default.conf