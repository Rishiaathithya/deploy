FROM node:18-alpine AS  builder

WORKDIR /app

COPY package*.json ./

RUN npm install

COPY . .

RUN npm run build


# we are importing node from the previous environment

FROM nginx:stable-alpine

COPY --from=builder /app/build  /usr/share/nginx/html

EXPOSE 80

CMD [ "nginx" , "-g" , "daemon off;" ]

