FROM node:21 AS Frontend
WORKDIR /usr/src/app
COPY package*.json .
RUN npm install 
COPY . .
RUN npm run build
EXPOSE 3000 
CMD ["npm", "run" "start"]
