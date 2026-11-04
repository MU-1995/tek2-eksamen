FROM nginx:1.25
COPY index.html /usr/share/nginx/html/
EXPOSE 80



// optimized //

FROM node:18-alpine
WORKDIR /app
COPY package*.json ./
RUN npm install

COPY . .
CMD ["node", "server.js"]