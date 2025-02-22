FROM node:18-alpine

WORKDIR /app/backend

COPY package.json .

RUN npm install

COPY . .

EXPOSE 80

ENV MONGODB_USERNAME=root

ENV MONGODB_PASSWORD=secret

CMD ["npm", "start"]