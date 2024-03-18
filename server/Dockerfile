FROM node AS Backend
WORKDIR /usr/src/app/server
COPY server/package*.json ./
RUN npm install
COPY server/ .
EXPOSE 8000
CMD ["node", "index.js"]
