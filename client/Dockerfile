FROM node AS Frontend
WORKDIR /usr/src/app/client
COPY client/package*.json ./
RUN npm install 
COPY client/ .

EXPOSE 3000 
CMD ["npm", "run" ,"start"]
