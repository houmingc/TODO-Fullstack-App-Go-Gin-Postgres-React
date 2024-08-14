# Use a more recent Node.js version
FROM node:16

# Set the working directory
WORKDIR /app

# Copy the application code to the container
COPY . ./

# Install dependencies
RUN npm install --silent

# Expose the port the app runs on
EXPOSE 3000

# Start the React application
CMD ["npm", "start"]
