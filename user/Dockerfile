# Use a base Node.js image
FROM node:14

# Set environment variables for New Relic
ENV NEW_RELIC_NO_CONFIG_FILE=true \
    NEW_RELIC_ENABLED=true \
    NEW_RELIC_LOG_LEVEL=info \
    NEW_RELIC_LICENSE_KEY=your_license_key \
    NEW_RELIC_APP_NAME="Your Application Name" \
    NEW_RELIC_DISTRIBUTED_TRACING_ENABLED=true

# Install New Relic agent
RUN npm install newrelic

# Expose the port your app runs on
EXPOSE 8080

# Set the working directory
WORKDIR /opt/server

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies
RUN npm install

# Copy New Relic configuration file
COPY newrelic.js .

# Copy server.js
COPY server.js .

# Start the application with New Relic agent
CMD ["node", "-r", "newrelic", "server.js"]


