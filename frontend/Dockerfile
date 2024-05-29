# frontend/Dockerfile
FROM node:latest

# Set work directory
WORKDIR /app

# Install dependencies
COPY package.json /app/
RUN npm install

# Copy project
COPY . /app/

# Build the angular project
RUN npm run build --prod

# Install Nginx
FROM nginx:alpine
COPY --from=0 /app/dist/frontend /usr/share/nginx/html

# Expose port
EXPOSE 80

# Start Nginx server
CMD ["nginx", "-g", "daemon off;"]
