FROM node:18-alpine as builder
WORKDIR /app

#copy packeage files and install dependencies
COPY package.json package-lock.json ./
RUN npm install

#copy all source files and build
COPY . .
RUN npm run build

#Serve the app using Nginx
FROM nginx:alpine

#copy built files from builder stage to Nginx
COPY --from=builder /app/build /usr/share/nginx/html

EXPOSE 80
CMD ["nginx","-g","daemon off;"] 
