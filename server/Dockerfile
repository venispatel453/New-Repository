FROM node:21 AS Backend
WORKDIR /usr/src/app
COPY package*.json ./
COPY . .
RUN npm install --production

EXPOSE 8000
CMD ["node", "index.js"]
