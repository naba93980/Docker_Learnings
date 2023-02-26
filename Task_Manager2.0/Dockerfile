FROM node:lts-alpine
ENV NODE_ENV=production
ENV MONGO_URI=mongodb://admin:password@mongodb:27017/TaskManagerDockerTutorial?authSource=admin
WORKDIR /usr/src/app
COPY ["package.json", "package-lock.json*", "npm-shrinkwrap.json*", "./"]
RUN npm install --production --silent && mv node_modules ../
COPY . .
RUN chown -R node /usr/src/app
USER node
CMD ["npm", "start"]
