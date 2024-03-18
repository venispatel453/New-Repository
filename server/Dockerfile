FROM node AS Backend
WORKDIR /usr/src/app/server
COPY server/package*.json ./
RUN ls package.json && npm install --production || echo "package.json not found"

COPY server/ .

EXPOSE 8000
CMD ["node", "index.js"]
