# Step 1: Use official Node.js image as base
FROM node:20

# Step 2: Set working directory inside container
WORKDIR /app

# Step 3: Copy package files and install dependencies
COPY package*.json ./
RUN npm install

# Step 4: Copy the rest of the application
COPY . .

# Step 5: Expose port
EXPOSE 3000

# Step 6: Start the app
CMD ["node", "app.js"]