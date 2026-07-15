# ...existing code...
FROM node:20-alpine3.18 AS build
WORKDIR /app

# install dependencies
COPY package*.json ./
RUN npm install

# copy source and build
COPY . .
RUN npm run build

# production image: nginx serving the CRA build output
FROM nginx:stable-alpine
COPY --from=build /app/build /usr/share/nginx/html
EXPOSE 80
CMD ["nginx", "-g", "daemon off;"]
# ...existing code...