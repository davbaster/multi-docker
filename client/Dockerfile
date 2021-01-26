FROM node:14.14.0-alpine as builder
WORKDIR '/app'
COPY ./package.json ./
RUN npm install
COPY . .
#it will create directory app/build
RUN npm run build

FROM nginx
EXPOSE 3000
#copy customer default.conf to nginx container
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
#copy build from builder to /usr/share/nginx/html on nginx container
COPY --from=builder /app/build /usr/share/nginx/html