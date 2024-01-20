FROM node:14.16.0-alpine3.13

# Create app user and group
RUN addgroup app && adduser -S -G app app

# Set the working directory
WORKDIR /app

# Copy package.json and package-lock.json separately to leverage Docker cache
COPY package*.json ./
RUN npm install

# Copy the rest of the application files
COPY . .

# Grant write permissions to the app user for /app directory and the entrypoint script
RUN chown -R app:app /app && chmod +x /app/docker-entrypoint.sh

# Expose the application port
EXPOSE 3001

# Switch to the app user
USER app

# Start the application
CMD ["npm", "start"]
