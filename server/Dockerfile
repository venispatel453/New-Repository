FROM node AS Backend
WORKDIR /usr/src/app
COPY package*.json ./
RUN ls package.json && npm install --production || echo "package.json not found"

COPY . .

EXPOSE 8000
CMD ["node", "index.js"]
