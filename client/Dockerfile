FROM node:23-alpine as builder

WORKDIR /app

COPY ./package.json ./

RUN npm install

COPY . .

CMD npm run build

#run phase
FROM nginx
EXPOSE 80

COPY ./nginx/nginx.conf /etc/nginx/nginx.conf
COPY --from=builder /app/build /usr/share/nginx/html
