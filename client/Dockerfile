FROM node:alpine as builder

WORKDIR '/app'
COPY package.json .
RUN npm install
COPY . .

RUN npm run build

FROM nginx
EXPOSE 3000
#copiamos desde la imagen anterior al directorio que necesita nginx
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html
