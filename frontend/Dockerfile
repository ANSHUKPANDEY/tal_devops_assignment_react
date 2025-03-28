FROM node:18-alpine

WORKDIR /app

COPY package.json .

COPY src/App.js src/index.js
COPY public/index.html /app/public/index.html

RUN npm install

COPY . .

EXPOSE 3001

CMD ["npm", "start"]
