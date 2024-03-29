# Use a base Node.js image
FROM node:14

# Set environment variables for Instana
ENV INSTANA_AUTO_PROFILE true

# Set environment variables for New Relic
ENV NEW_RELIC_NO_CONFIG_FILE=true \
    NEW_RELIC_ENABLED=true \
    NEW_RELIC_LOG_LEVEL=info \
    NEW_RELIC_LICENSE_KEY=78906c4da216ba24690fce6a95b1cbe0FFFFNRAL \
    NEW_RELIC_APP_NAME="Catalogue" \
    NEW_RELIC_DISTRIBUTED_TRACING_ENABLED=true

# Set working directory
WORKDIR /opt/server

# Copy package.json and package-lock.json
COPY package*.json ./

# Install dependencies including the New Relic agent
RUN npm install newrelic && npm install

# Copy server.js
COPY server.js .

# Expose port 8080
EXPOSE 8080

# Start the application with the New Relic agent
CMD ["node", "-r", "newrelic", "server.js"]


