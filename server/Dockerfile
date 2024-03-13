FROM node AS Backend
WORKDIR /usr/src/app
COPY package*.json ./
RUN npm install --production
COPY . .

EXPOSE 4004
CMD ["node", "index.js"]
