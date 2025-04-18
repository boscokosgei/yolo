# Stage 1: Build the React App
FROM node:16-alpine AS build

WORKDIR /app

COPY package*.json ./
RUN npm install

COPY . .
RUN npm run build

# Stage 2: Serve with a small Node + Serve image
FROM node:16-alpine

WORKDIR /app

# Install `serve` (only this, nothing else)
RUN npm install -g serve

# Copy only built static files
COPY --from=build /app/build .

EXPOSE 3000

CMD ["serve", "-s", ".", "-l", "3000"]