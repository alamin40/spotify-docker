#Node.js base image
FROM node:13-alpine

#Set work directory -- into container
WORKDIR /app

#Copy package.json 
COPY package*.json ./

#Install npm
RUN npm install

# Copy the code for rest of the application
COPY . .

EXPOSE 8080

#Run the application
CMD ["npm", "start"]

