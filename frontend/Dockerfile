FROM node:20-alpine AS build

WORKDIR /app

COPY package.json package-lock.json ./

#Installiert exakt die Versionen aus package-lock.json
RUN npm ci

COPY . .

# Angular Production Build
RUN npm run build -- --configuration production


# Multi-Stage Build: Nginx als Webserver
FROM nginx:1.25-alpine

COPY nginx.conf /etc/nginx/conf.d/default.conf

COPY --from=build /app/dist/kukuk-frontend/browser /usr/share/nginx/html

EXPOSE 80

ENTRYPOINT ["nginx", "-g", "daemon off;"]
