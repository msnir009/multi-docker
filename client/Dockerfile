FROM node:alpine as builder

WORKDIR '/app'
COPY package*.json ./



RUN npm install
RUN npm install -D jest-dom
COPY . .
RUN npm run build

#creates a new phase
FROM nginx
#for aws beanstalk to look for the port mapping
EXPOSE 80 
COPY ./nginx/default.conf /etc/nginx/conf.d/default.conf
COPY --from=builder /app/build /usr/share/nginx/html