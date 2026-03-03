#build stage 
FROM node:18 AS build
WORKDIR  /app
COPY package.json package-lock.json ./
RUN npm install 
COPY . .
RUN npm run build 
# runtime file 
FROM ubuntu:22.04 
RUN apt update && apt install apache2 -y
#copy output to apache root directory 
COPY --from=build /app/dist  /var/www/html/
EXPOSE 80
CMD ["apachectl","-D","FOREGROUND"]
