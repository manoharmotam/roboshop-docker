FROM node:20
WORKDIR /app
COPY package.json /app
COPY *.js /app
RUN npm install
EXPOSE 8080
CMD ["node", "server.js"]