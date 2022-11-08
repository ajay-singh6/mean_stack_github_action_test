
FROM node:latest as node

# Working directory be app
WORKDIR /app

COPY package*.json ./

###  Installing dependencies

RUN npm install --silent

# copy local files to app folder
COPY . .

RUN npm run build

FROM nginx:1.13.12-alpine

COPY --from=node /app/dist/client /usr/share/nginx/html
COPY ./nginx.conf /etc/nginx/conf.d/default.conf
