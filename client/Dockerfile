FROM node AS Frontend
WORKDIR /usr/src/app
RUN ls -l
COPY package*.json .
RUN npm install 
COPY . .
RUN npm run build
EXPOSE 3000 
CMD ["npm", "start"]
